# AGENTS.md — macos-on-ios

Run native arm64 macOS apps/games unmodified on iPad/iPhone via retagging + UIKit-backed shims. Read README.md first; per-game notes in games/<game>/README.md.

## Rules

* No game files, saves, profiles, certificates or build outputs in git (.gitignore covers them).
* Game installs are read-only; the converter copies.
* Verify on the device (console, crash stack, screenshot, HUD) before calling anything fixed.
* New macOS-only API: implement in shim/overrides/*.m (generated stubs log what's missing).
* Game-specific behaviour starts behind a convert_app.py option; generalize it once a second game needs it.

## Loop

`games/<game>/run.sh [secs]` → read `$T/<bundle-id>.console.log` (SHIM/STATS lines); crash stack is printed automatically; game logs live in the app container (copy out with devicectl).
