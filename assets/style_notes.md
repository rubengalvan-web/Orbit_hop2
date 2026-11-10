# ORBIT HOP — Style Notes

Mood: cozy, luminous, friendly 2D space adventure. No heavy outlines.

## Palette
- Background: `#080d20`, `#0c1631`, `#142249`
- Cyan: `#71f5f1`; pink: `#ff7da5`; purple: `#b99cff`; gold: `#ffe49d`
- Planets: blue `#70def7 → #2767aa`; orange `#ffb47a → #c65b7c`; purple `#c2a4ff → #6652b8`; teal `#7ae9bf → #319a89`; tan `#ffe096 → #b78a53`; magenta `#ed94c6 → #904685`

## Rendering and developer guidance
- PNGs are RGBA where transparency is needed; SVGs are resolution-independent. Ships are centered in 128×128 canvases, point right, and should be displayed at roughly 30×30 CSS pixels (visible hull ~15×8 CSS px at 128→30 scaling). Tune actual visible size to desired hitbox.
- All planet spheres use a soft upper-left highlight and lower-right shade. Planet sprites are 256×256.
- `planet_glow.png` is a white tintable radial glow; draw behind each planet with additive or screen blending. Suggested opacity 0.25–0.5.
- Gravity rings and goal ring are 512×512; draw centered around planets. Unvisited ring dim; visited cyan.
- Backgrounds are 2048×2048. Their low-frequency wash is periodic; stars are sparse. Parallax images are transparent and can be translated at ~0.2–0.35 foreground speed. For exact seamless parallax wrapping, render repeated copies and crop at boundaries.
- Flame sprite sheets use three 128×128 frames in a single row. Other sheets have 5 columns maximum. Every sheet includes a JSON atlas with frame rectangles.
- UI 9-slice guides are in `ui/nine_slice.json`. Button gradients are baked in, so stretch the center sparingly or replace with a shader for very wide buttons.
- Glow blur reference: ship engines radius ~11px, Gaussian blur ~9px at 128px sprite scale; planet glow uses quadratic radial alpha. Use premultiplied alpha where supported to avoid fringes.
- `art_world_clear.png` and `art_game_over.png` are illustrations without text, to allow localization; `banner_world_clear.png` is separate.
- Ships are intentionally pure visual skins: gameplay physics and hitboxes must remain identical.
