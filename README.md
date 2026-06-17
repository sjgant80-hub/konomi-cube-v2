# 紙 konomi-cube · v2 · the fold engine

> the interactive fold engine · v20.4 socket VI made visible
>
> prime **691** · sovereign single HTML · MIT · ◊·κ=1

konomi-cube v2 is the *operational geometry* of [konomigami-lib](../konomigami-lib) — the fold algebra rendered as real-time 3D mesh deformation. v20.4 §23 socket VI, made visible and interactive.

**v2 supersedes v1** (which was a private viz of nested cubes only). v2 is the actual fold engine: the algebra is the library, this is the geometry.

---

## For the practitioner

Open `index.html` in any modern browser (works from `file://`). No install, no server, no build step.

### What you can do

- **Type a fold sequence** like `●〜┃♡△◐◯` and watch it unfold in 3D
- **Click glyphs from the palette** — 7 base operators + 6 mutations
- **Load named forms** — primorial (510510), crane, mersenne tower, fibonacci, shield
- **Number → fold** — type any integer, get its glyph sequence. `42` → `●〜♡`. `127` → ◊ the shield holds.
- **Audio reactivity** — enable mic; bass-heavy = coherent (golden angle), treble-heavy = chaotic
- **Export** — download mesh as `.glb`, state as `.json`
- **Scrub history** — click any past step to rewind
- **Drive remotely** — other estate tools can `postMessage({target:'konomi-cube-v2',action:'fold',sequence:'…'})`

### The 7 base operators

| glyph | name | prime | ISA | fold |
|---|---|---|---|---|
| ● | GROUND   | 2  | L0 | base plane / octave |
| 〜 | WAVE     | 3  | L1 | valley fold (-θ) |
| ┃ | GATE     | 5  | L2 | mountain fold (+θ) |
| ♡ | SINK     | 7  | L3 | vertex collapse |
| △ | REVERSE  | 11 | L4 | direction flip |
| ◐ | PETAL    | 13 | L5 | open & flatten flap |
| ◯ | COLLAPSE | 17 | L6 | waterbomb |

The full primorial `●〜┃♡△◐◯` factors to **2·3·5·7·11·13·17 = 510510 = FOLD**.

### The 6 mutations

| glyph | name | effect |
|---|---|---|
| 火 | FIRE    | doubles next angle |
| 水 | WATER   | halves next angle |
| 空 | SKY     | skips next glyph |
| 雷 | THUNDER | snaps next θ → π (flat crease) |
| 響 | ECHO    | re-applies last base NOW |
| 華 | BLOOM   | undoes last fold NOW |

### Keyboard

- `1-7` base operators · `q w e r t y` mutations
- `Space` apply sequence · `Esc` reset · `Ctrl+E` export GLB · `Ctrl+K` Ω palette

### The shield (◊ · 127)

Any integer that is *not* expressible as `2^a · 3^b · 5^c · 7^d · 11^e · 13^f · 17^g` is **irreducible** in this algebra. The smallest such prime is **M₇ = 127** — Thomas Frumkin's break point. Type `127` into the number field and the shield holds. This is the geometric proof of v20.4 §18.

---

## For the builder

### Architecture

- **One HTML file** · all CSS + JS inline · sovereign, no build step
- **Three.js** via importmap from unpkg (the one declared CDN exception per build doctrine)
- **konomigami-lib inlined** verbatim at the top of the module script (`window.konomigami` for console access)
- **Three.js adapter** (`recordFor`, `applyRecordToBuffer`) turns glyphs into mesh transforms — visually convincing, deterministic per sequence
- **State** held in plain object `state`; settings persisted in `localStorage`
- **PWA manifest** baked via `data:` URL
- **fall-signal** BroadcastChannel for cross-tool messaging
- **postMessage API** lets sibling tools drive the cube remotely:
  ```js
  iframe.contentWindow.postMessage({target:'konomi-cube-v2', source:'mytool', action:'fold', sequence:'●〜┃'}, '*');
  ```
  Supported actions: `ping`, `fold`, `reset`, `export-glb`, `get-state`.

### What's not included

- No backend, no analytics, no telemetry — sovereign by construction
- No npm dependencies — vanilla JS + Three.js CDN only
- No LLM required — Ω palette has a T0 keyword router; T3 fallback if you add an API key in settings

### Files

```
index.html   — the tool (single sovereign file)
README.md    — this
LICENSE      — MIT
.nojekyll    — Pages legacy deploy
```

### Cosmology check

- prime **691** · 691 mod 127 = 56 = 2³·7 (spine product · clean per v20.4 §18)
- supersedes konomi-cube v1
- consumes konomigami-lib (prime 677) verbatim
- operationalises v20.4 §23 socket VI

### Estate plumbing baked in

- `Cascade` (T0/T2/T3) — Ollama probe + optional API keys
- `KONOMI` sovereign shim — `window.KONOMI = {active:true, tier:'sovereign', prime:691, ...}`
- `BroadcastChannel('fall-signal')` — sends `{source:'konomi-cube-v2', type:'hello', prime:691}` on boot
- PWA manifest data URL with ◊ icon

---

## Credits

- **Author:** Simon Gant · sjgant80-hub
- **Substrate:** Thomas Frumkin · 紙 KONOMIGAMI Geometric Fold Architecture
- **Spec:** v20.4 §23 · phi is home · ◊·κ=1
- **Licence:** MIT
