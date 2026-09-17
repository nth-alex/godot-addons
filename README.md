# godot-addons

Small, self-contained addons for Godot 4. One folder per addon under `addons/`,
each installable on its own — nothing here depends on anything else here.

| Addon | What it does | Files |
| --- | --- | --- |
| [flycam](addons/flycam/) | Free-flying camera: WASD flies where you look, mouse turns, Shift is faster | 1 script |

## Install one addon

Each addon is a folder under `addons/`. Copy the folder into the target
project's own `addons/`, or pull just the script:

```sh
mkdir -p addons/flycam && curl -sL \
  https://raw.githubusercontent.com/nth-alex/godot-addons/main/addons/flycam/flycam.gd \
  -o addons/flycam/flycam.gd
```

Re-run the same command to update.

**Open the project in the editor once after installing.** These addons register
their node types with `class_name`, and Godot writes that registration into
`.godot/global_script_class_cache.cfg` during import. Until the project has been
imported, the type does not resolve — a script referring to `FlyCam` fails with
`Parse Error: Could not find type "FlyCam" in the current scope`. Opening the
editor once, or running `godot --headless --path . --import`, fixes it for good.

## Install everything, pinned

```sh
git submodule add https://github.com/nth-alex/godot-addons vendor/godot-addons
ln -s ../vendor/godot-addons/addons/flycam addons/flycam
```

## Adding an addon to this repo

Keep each one self-contained: its own folder under `addons/<name>/`, its own
`README.md`, and no imports from a sibling addon. `plugin.cfg` and `plugin.gd`
are optional — include them only so the folder shows up in the Plugins tab;
an addon that works through `class_name` alone needs nothing enabled.

## License

MIT — see [LICENSE](LICENSE).
