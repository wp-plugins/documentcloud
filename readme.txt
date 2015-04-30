=== DocumentCloud ===
Contributors: chrisamico, reefdog
Tags: documentcloud, documents, journalism, reporting, research
Requires at least: 3.2
Tested up to: 4.2.1
Stable tag: trunk
License: GPLv2
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Embed DocumentCloud resources in WordPress content.

== Description ==

[DocumentCloud](https://www.documentcloud.org/) is a service that allows journalists to analyze, annotate and publish documents, hosted by Investigative Reporters & Editors. Initial development of this plugin supported by [NPR](http://www.npr.org) as part of [StateImpact](http://stateimpact.npr.org) project.

This plugin allows you embed DocumentCloud resources using a custom shortcode:

    [documentcloud url="https://www.documentcloud.org/documents/282753-lefler-thesis.html"]

When you save, WordPress fetches and stores the actual embed code HTML from the DocumentCloud servers using oEmbed. You can freely toggle between visual and HTML mode without mangling embed code, and your embed will always be up to date with the latest embed code.

By default, documents will have a responsive width (it will narrow and widen as necessary to fill available content area) and use the theme's default height. If you want to override this, you can either set `responsive="false"` or explicitly set a `width`:

    [documentcloud url="https://www.documentcloud.org/documents/282753-lefler-thesis.html" width="600"]

You can set your own defaults in Settings > DocumentCloud, but default widths will be ignored unless `responsive` is disabled:

    [documentcloud url="https://www.documentcloud.org/documents/282753-lefler-thesis.html" responsive="false"]

To embed a note, just use any note-specific URL. Notes ignore `width/height` and always act responsively:

    [documentcloud url="https://www.documentcloud.org/documents/282753-lefler-thesis.html#document/p1/a53674"]

Here's the full list of embed options you can pass via shortcode attributes; some are specific to the type of resource you're embedding.

**All resources (documents and notes):**

- `url` (**required**, string): Full URL of the DocumentCloud resource.
- `container` (string): ID of element to insert the embed into; if excluded, embedder will create its own container.

**Documents only:**

- `height` (integer): Height (in pixels) of the embed.
- `width` (integer): Width (in pixels) of the embed. If used, will implicitly set `responsive="false"`.
- `responsive` (boolean): Use responsive layout, which dynamically adjusts width to fill content area. Defaults `true`.
- `responsive_offset` (integer): Distance (in pixels) to vertically offset the viewer for some responsive embeds.
- `default_page` (integer): Page number to have the document scroll to by default.
- `default_note` (integer): ID of the note that the document should highlight by default.
- `notes` (boolean): Show/hide notes:
- `search` (boolean): Hide or show search form.
- `sidebar` (boolean): Hide or show sidebar. Defaults `false`.
- `pdf` (boolean): Hide or show link to download original PDF. Defaults `true`.
- `text` (boolean): Hide or show text tab. Defaults `true`.
- `zoom` (boolean): Hide or show zoom slider.
- `format` (string): Indicate to the theme that this is a wide asset by setting this to `wide`. Defaults `normal`.

You can read more about publishing and embedding DocumentCloud resources on https://www.documentcloud.org/help/publishing.

== Installation ==

1. Upload the contents of the plugin to `wp-content/plugins/documentcloud`
2. Activate the plugin through the "Plugins" menu
3. In your posts, embed documents or notes using the DocumentCloud button or the `[documentcloud]` shortcode
4. Optional: Set a default width/height for all DocumentCloud embeds (which can be overridden on a per-embed basis with the `height/width` attributes) at Settings > DocumentCloud. (This default width will only be used if you set `responsive="false"` on an embed.)

== Changelog ==

= 0.3 =
* Add support for embedding notes.
* Default to responsive.
* Enable caching.

= 0.2 =
* Fetch embed code via oEmbed instead of generating statically.
* Add new options: `container`, `responsive`, `responsive_offset`, `default_page`, `default_note`, `notes`, `search`, and `zoom`.
* Deprecate `id` attribute. It's still usable, but support may drop in the future. Use `url` instead.

= 0.1 =
* Initial release.

== Upgrade Notice ==

= 0.3 =
Adds support for embedding notes and enables caching.

= 0.2 =
Adds oEmbed support for future-proofing embed codes. Provides additional embed options like `default_page`.
