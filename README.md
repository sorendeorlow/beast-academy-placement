# Beast Academy Placement Checks

A mobile-friendly, tap-to-answer set of readiness checks for **all 20 Beast
Academy levels (1A → 5D)** — a progressive, interactive adaptation of the Art of
Problem Solving placement tests, built as one self-contained `index.html`.

Successor to [beast-academy-1a-check](https://github.com/sorendeorlow/beast-academy-1a-check):
same look and mechanics, refactored into a **data-driven engine** so every level
is just an entry in a `LEVELS` array — no code changes to add content.

## What it does

- **Level picker** home screen: all 20 checks, grouped by level, with a
  Full-vs-Sample badge on each.
- **Progressive quiz**: one puzzle at a time, a progress bar of pips, a lightbulb
  mascot that lights up on a correct answer, and per-answer feedback.
- **Auto-scored parent report**: score, a per-question grid, a per-level "ready"
  verdict, and a grown-up tip.
- **Second-chance logic** and **read-aloud** (browser text-to-speech), both
  configurable per level.

## Question types (the engine's schema)

| type | for | shape |
|------|-----|-------|
| `compare` | Level 1 visual | two dot-boxes, tap the one with more |
| `count`   | Level 1 visual | count the dots, type the number |
| `connect` | Level 1 | tap numbered dots in order |
| `seq`     | any | fill missing numbers in a pattern |
| `word`    | any | a sentence with one blank, read-aloud friendly |
| `numeric` | any | type an answer (multi-digit, optional ± for negatives) |
| `mc`      | any | tap one of several text options |

Full authoring docs (every field, per-level knobs) are in the big comment block
at the top of the `<script>` in `index.html`.

## Content status

- **1A** — full transcription (matches the original AoPS check), `ready:'full'`.
- **1B → 5D** — **original sample problems**, `ready:'sample'`. They exist so the
  engine is playable end-to-end and you can see each format. **They are not the
  AoPS content.** To make a level a real check: open its object, replace
  `questions:[...]` with that PDF's problems, set `pass:` to the threshold on the
  PDF, and flip `ready:'full'`.

## Tech

Single self-contained `index.html` — no build, no dependencies, no external
requests. Works offline (open the file directly). Uses the system serif
(Georgia) as the headline face; to match the 1A repo's exact PT Serif, copy the
`@font-face` data-URI block from that repo's `<style>`.

Deploy anywhere static (e.g. GitHub Pages: push and enable Pages on the branch).

---

Unofficial interactive adaptation. The underlying readiness checks are
© AoPS Incorporated. This repo transcribes only 1A (as in the original project);
levels 1B–5D ship with original placeholder problems for you to replace with
content you have the right to publish.
