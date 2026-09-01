# VibeVJ Community Guide

Welcome! This is a **community repository**. That means YOU can push your own
new features — custom generators, GLSL shaders, fixtures, and other assets.

Please respect our Workflow, so we can see and verify your work. 
Link your Pull Request to an Issue by Pushing into its Branch. 
We only gonna verify Pull Requests Linked to an Ticket in the Verify Status.
If the Assests are working we gonna Merge the Request.

This page is your quick map to the whole project tree, so you always know
exactly where to drop in your new work.

## Directory Tree

```
.
├── assets/              # 👑 THE place for NEW community features
│   ├── Generators/      # New generator .asset folders
│   │   ├── Audio/
│   │   ├── Math/
│   │   ├── Network/
│   │   ├── Output/
│   │   └── Utility/
│   ├── Shaders/         # New GLSL shaders
│   │   ├── Effects/
│   │   ├── Sources/
│   │   └── Utilities/
│   ├── Fixtures/        # New fixture definition JSON files
│   │   ├── Bars/
│   │   ├── MovingHeads/
│   │   └── Pars/
│   ├── Views/           # UI view assets
│   └── Textures/        # Image / texture assets
│
├── engine/              # ⚠️ INTERNAL ENGINE CODE — DO NOT CHANGE
│   ├── assets/          # Engine-internal glue assets (DO NOT CHANGE)
│   ├── generators/      # Universal generator wrapper + per-extension loaders
│   │   ├── generatoritem.shio   # Wraps any generator into a window
│   │   └── extensions/         # Loaders: asset, glsl, png, txt
│   └── processes/       # Subprocess code (DO NOT CHANGE)
│
├── configs/             # Configuration files
├── projects/            # Saved VJ projects
└── src/                 # Main app / menu & layout UI
```

## Where to put your new feature

Everything new lives under **`assets/`**. Pick the right subcategory:

- **`assets/Generators/`** — for new generator `.asset` directories.
  Use one of the subfolders (`Audio/`, `Math/`, `Network/`, `Output/`, `Utility/`).
- **`assets/Shaders/`** — for new GLSL shaders, under `Effects/`, `Sources/`, or `Utilities/`.
- **`assets/Fixtures/`** — for new fixture JSON definition files
  (e.g. `Bars/`, `MovingHeads/`, `Pars/`).
- **`assets/Views/`** and **`assets/Textures/`** — for UI view and image assets.

## The `.asset` folder format

Each new generator asset is a folder named `<Name>.asset/` with an entry point:

```
MyAwesome.asset/
└── src/
    └── __init__.shio    # Entry point for shizoscript assets
```

For shaders the entry point is a GLSL file instead:

```
MyShader.glsl/
└── src/
    └── __init__.glsl    # Entry point for GLSL shader assets
```

Fixtures are plain JSON files dropped into the right `Fixtures/` subfolder.

## Do NOT touch `engine/`

The `engine/` directory is internal glue code. It holds the universal generator
wrapper (`engine/generators/generatoritem.shio`) and the per-extension loaders in
`engine/generators/extensions/`.

- **`engine/assets/`** — engine-internal assets, **DO NOT CHANGE**.
- **`engine/processes/`** — subprocess code, **DO NOT CHANGE**.

Please keep all your new features in `assets/` only.

## Authoring guides

For the full details on creating a proper asset, read these docs:

- [`assets/ASSET_GUIDE.MD`](assets/ASSET_GUIDE.MD) — how to author a generator asset.
- [`assets/README.md`](assets/README.md) — asset categories and navigation.
- [`assets/Shaders/SHADER_GUIDE.MD`](assets/Shaders/SHADER_GUIDE.MD) — GLSL shader authoring.

## How to contribute

1. **Pick a category** under `assets/` and create a new `<Name>.asset/` folder
   (or a `.glsl/` folder / fixture `.json` file) in the correct subcategory.
2. **Add the entry point** — `src/__init__.shio` for script assets,
   or `src/__init__.glsl` for shader assets.
3. **Verify it compiles** — check your shizoscript files with the
   `shizoscript_syntax_checker` and `shizoscript_debugger` tools.
   When testing a standalone file, make sure to `import nanogui;` if your
   asset uses nanogui widgets.
4. **Never modify `engine/`** — it is internal and marked DO NOT CHANGE.

That's it! Drop your feature in `assets/`, make sure it compiles, and submit
your change. Thank you for building VibeVJ! 🎛
