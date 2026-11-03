# NEON TABLE FORGE v7 — Structure Libraries

## Delivered files

- `NEON_TABLE_FORGE_v7.html` — standalone editor. It contains starter examples so the library manager works offline on first launch.
- `esp32-web-gui.ntflib.json` — portable ESP32 web GUI component library.
- `retro-bbs-ansi.ntflib.json` — portable retro BBS/ANSI textmode component library.

Each `.ntflib.json` file contains exactly one library. The editor imports and exports that format and keeps a local editable copy in browser storage. The starter libraries are also included in the application so they are available when the HTML is opened directly from disk; export them from the Library panel after edits to keep a portable copy.

## Using the library manager

1. Open **Structures library** in the top bar or inspector.
2. Select a library and select a component from the list. Search supports component names, categories, descriptions and tags.
3. Edit the name, category, description, tags and HTML. Use **Edit visually** to edit visible text/content in the preview; use HTML source for precise structural edits.
4. Click **Save component**. The library is stored in local browser storage.
5. Click **Insert into table** to insert the selected component into the currently active cell, including when editing a nested table.
6. Use **Export active library** to save one portable `.ntflib.json` file. Import that file on another device/browser with **Import .ntflib.json**.

## File format

The format is UTF-8 JSON with `format: "ntf-structure-library"` and `version: 1`. Each file describes one library and contains `structures[]`, where each structure has `id`, `name`, `category`, `description`, `tags[]`, and `html`. The `html` field is a self-contained HTML snippet. Inline styling is preserved. Scripts, event attributes, embedded stylesheets, SVG, iframe/object content and unsafe URLs are removed by the editor's sanitizer.

ESP32 relay, network configuration, console and system-action examples use HTML POST forms with relative endpoints, so the examples do not rely on side-effecting GET links. Templates use illustrative device names, endpoints, pin assignments, values and dates. Replace these with the target firmware's actual routes, GPIO map, telemetry values and security model before deployment. The ESP32 firmware must implement the matching routes, validate inputs, authenticate privileged actions and apply CSRF protections where applicable. The included buttons and links are markup building blocks; they do not automatically communicate with an ESP32 or create firmware endpoints.

## Storage notes

Browser storage is local to the browser profile. It is not a substitute for file backup or cross-device sync. Use the per-library export to preserve/share changes. The app limits each imported library file to 4 MB, each structure HTML snippet to 180 KB, 300 structures per library and 60 libraries per browser profile.
