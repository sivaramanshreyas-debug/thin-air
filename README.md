# Thin Air

A Flappy Bird–style jetpack shooter that runs in the browser. A brick-built hero launches from the city at dawn and climbs through the real layers of the atmosphere, one sky per layer, until he meets an alien mothership in orbit.

**Play it:** https://sivaramanshreyas-debug.github.io/thin-air/ (or open `index.html` in a browser; no build step, no dependencies).

## How it plays

- **The jetpack climbs on its own.** You steer left and right. Hit nitro to climb much faster (it burns fuel quickly), or brake to slow down, save fuel and buy time to dodge.
- **The blaster fires by itself, but only when there's something to shoot** ahead of you.
- **Rival jetpackers want you out of the sky.** Some swoop in from above, track you, flash a `!` and dive. Higher up, others rocket up from below after a warning marker. Shoot the ones above you; dodge the ones coming from below.
- **Some things you shoot, some you dodge.** Birds, planes and ion gates are dodge-only. Balloons pop, meteors split, satellites take three hits, and asteroids split twice.
- **Fuel drains as you fly.** Refill cans appear more often the emptier your tank gets. Run dry and you start to fall, with one last chance to catch a can before you drop off the screen.
- **One hit and the run ends.** Your score is distance climbed plus everything you shoot down.
- **At 35,786 km (geostationary orbit) the mothership attacks.** Beat it and a new day starts: Loop 2, faster and denser.

## The climb

| Layer | Altitude | Sky | Obstacles |
| --- | --- | --- | --- |
| Troposphere | 0–8 km | Dawn | Birds and flocks |
| Jet stream | 8–12 km | Morning | Airliners (warning sign first) |
| Stratosphere | 12–50 km | Pink-blue noon | Weather balloons |
| Mesosphere | 50–85 km | Golden hour | Meteors |
| Thermosphere | 85–600 km | Sunset and aurora | Charged ion gates |
| Exosphere | 600–10,000 km | Twilight, Earth below | Satellites and space junk |
| Outer space | 10,000+ km | Night | Asteroids, then the mothership |

## Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Launch / retry | Space, Enter, W or ↑ | Tap |
| Steer | A / D or ← / → | Drag left / right |
| Nitro (fast climb, burns fuel) | W or ↑ | While dragging, drag up |
| Brake (slow climb, saves fuel) | S or ↓ | While dragging, drag down |
| Pause | P or Esc | Pause button (top right) |
| Sound on/off | M | Speaker button (top right) |

**Practice:** add `#l0` to `#l6` or `#boss` to the URL to start at that layer.

## Tuning

Everything lives in `index.html`:

- `LAYERS`: each layer's name, altitude range, sky gradient, sun position and effects (stars, clouds, aurora, Earth)
- `spawnLayer`: which obstacles appear in each layer and how often, plus how often rival jetpackers attack
- `rival`: how rivals track, aim and dive
- `updatePlay`: fuel drain, nitro and brake strength, climb speed and the fuel-can spawn chance
- `spawnBoss` / `updateBoss`: mothership health and attack patterns

The screen is a 180×320 canvas. All art is drawn in code and the sound effects are synthesised with the Web Audio API.

## Note on the file format

`index.html` is written as a page fragment (no `<!doctype>`/`<html>`/`<head>`/`<body>`), because it's also published as a Claude artifact, which adds that wrapper itself. The GitHub Pages workflow wraps it in a full page with a mobile viewport before deploying.
