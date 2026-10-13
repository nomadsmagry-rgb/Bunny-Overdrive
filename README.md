# Bunny Overdrive

An original, single-level rabbit run-and-gun browser game inspired by 1990s platformers. No copied Jazz Jackrabbit characters, art, music, or levels.

## Play
Open `index.html` in a modern browser. It is completely self-contained and works offline, with no dependencies, accounts, API keys, paid assets, or game backend.

Alternatively, serve this folder with `python -m http.server 8000 --bind 0.0.0.0`.

## Controls
- Arrow keys or A / D: move
- Space, Up, or W: jump; press again for a double-jump
- X or Z: hold to fire
- Shift: dash (short cooldown)
- P or Escape: pause / resume
- Enter: start / restart / resume
- Music-note button: toggle synthesized sound effects (initially muted)
- Touch devices: on-screen move, dash, shoot, and jump buttons

Collect 88 gems, defeat bots, and reach the glowing exit at the far right. Spring pads boost your jump. Landing on a bot defeats it. The midpoint checkpoint restores one heart and becomes your respawn point after a fall. Five hearts per run; taking damage briefly grants invulnerability. Depleted hearts mean a full restart. Enemy defeats and remaining hearts add to the score.

## Build
All visuals are drawn with Canvas 2D, sound effects use Web Audio, and the interface uses inline CSS. Edit `index.html` to change everything. `platforms`, `springs`, and enemy spawn lists define the level. There is no build step.

## Checks
Browser smoke tests are in `tests/browser.cjs`. To rerun from this directory:

```sh
npm install --no-save playwright
npx playwright install --with-deps chromium
# With the local server running on port 8000:
node tests/browser.cjs
```

Checks cover start, movement, double-jump, shooting, pause/resume, checkpoint activation, falling and respawning, win and loss screens, replay reset, mobile overflow, and browser exceptions. They test state transitions, not a complete human playthrough.
