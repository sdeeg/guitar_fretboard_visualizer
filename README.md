# Guitar Fretboard

An interactive, browser-based fretboard reference tool for standard and baritone guitar. Visualize scales, modes, and diatonic triads across the full neck in any key, with flexible tuning, color, and display options.

---

## Features

- **12 keys** — all chromatic roots from C through B
- **12 scales and modes** — Major, Natural Minor, Major Pentatonic, Minor Pentatonic, Blues, Dorian, Mixolydian, Phrygian, Lydian, Harmonic Minor, Whole Tone, Diminished
- **6 low-string roots** — Bb, B, C, D, Eb, E
- **Two interval-based tuning systems** — Standard and All 4ths, each transposable by low-string root
- **4 alternate tunings** — Drop D, Open G, DADGAD, Open D
- **Label modes** — toggle between note names and interval degrees (1, b3, 5, etc.)
- **3 color modes** — Uniform, By degree, By role
- **6 color palettes** — Spectrum, Warm, Cool, High contrast, Colorblind safe, Monochrome
- **Triad highlighting** — select any diatonic triad; tones show R / 3 / 5, non-triad tones dim
- **Root-only view** — filter to show only root notes across the neck
- **Live scale readout** — note chips below the fretboard show every scale note with its interval name
- **Collapsible options panel** — advanced controls tucked away until needed

---

## Usage

No installation or internet connection required. Open `baritone_fretboard.html` directly in any modern browser.

```
# macOS
open baritone_fretboard.html

# Windows
start baritone_fretboard.html

# Linux
xdg-open baritone_fretboard.html
```

Or drag the file into a browser window.

---

## Controls

### Always visible

| Control | Options | Description |
|---|---|---|
| Key | C - B (all 12) | Sets the root / tonal center |
| Scale | 12 types | Selects the scale or mode |
| Triad | Diatonic triads | Highlights a triad within the scale |
| Labels | Notes / Intervals | Toggles note names vs. degree symbols |

### More options (collapsible)

| Control | Options | Description |
|---|---|---|
| Colors | Uniform / By degree / By role | Switches color mode |
| Palette | 6 themes | Sets the color palette for all modes |
| Show | All / Root only | Filters visible notes |
| String 6 | Bb / B / C / D / Eb / E | Sets the low-string root (Standard and All 4ths only) |
| Tuning | Standard / All 4ths / 4 alternates | Selects the tuning system |

---

## Tuning Systems

### Standard (by low string)

Each root produces a standard-interval tuning (P4 / P4 / P4 / M3 / P4 between strings).

| Root | Strings (low to high) |
|---|---|
| Bb | Bb Eb Ab Db F Bb |
| B  | B E A D F# B |
| C  | C F Bb Eb G C |
| D  | D G C F A D |
| Eb | Eb Ab Db Gb Bb Eb |
| E  | E A D G B E |

### All 4ths (by low string)

All string-to-string intervals are perfect 4ths, making scale and arpeggio shapes identical across all six strings.

| Root | Strings (low to high) |
|---|---|
| Bb | Bb Eb Ab Db Gb B |
| B  | B E A D G C |
| C  | C F Bb Eb Ab Db |
| D  | D G C F Bb Eb |
| Eb | Eb Ab Db Gb B E |
| E  | E A D G C F |

### Alternate tunings

These are fixed absolute tunings; the String 6 selector is disabled when any of these is active.

| Name | Strings (low to high) | Notes |
|---|---|---|
| Drop D | D A D G B E | Standard guitar, low string dropped to D |
| Open G | D G D G B D | Open G major chord; classic blues and slide |
| DADGAD | D A D G A D | Open Dsus4; Celtic and folk favourite |
| Open D | D A D F# A D | Open D major chord; slide guitar staple |

---

## Color Modes

### Uniform
Root notes use palette color 0; all other scale tones use palette color 1. Clean and simple.

### By degree
Each scale degree position (1st, 2nd, 3rd, etc.) receives its own color from the palette's degree array. Up to 8 degrees supported.

### By role
Notes are grouped by harmonic function, regardless of their degree position in the current scale.

| Role | Intervals | Description |
|---|---|---|
| Root | 1 | Tonal center |
| Chord tone | 3, 5, 7 | Core triad and seventh chord tones |
| Color tone | 2, 4, 6, b7 | Extensions and characteristic tones |
| Tension | b2, b5, #5 | Chromatic and altered tones |

---

## Palettes

All palettes apply consistently across all three color modes.

| Name | Character |
|---|---|
| Spectrum | Broad rainbow spread — the default |
| Warm | Reds, ambers, and burnt oranges |
| Cool | Navies, forest greens, and purples |
| High contrast | Maximum perceptual separation between degrees |
| Colorblind safe | Adapted from the Okabe-Ito palette |
| Monochrome | Single blue hue from near-black to mid-blue |

---

## Scales Reference

| Name | Intervals |
|---|---|
| Major | 1 2 3 4 5 6 7 |
| Natural Minor | 1 2 b3 4 5 b6 b7 |
| Major Pentatonic | 1 2 3 5 6 |
| Minor Pentatonic | 1 b3 4 5 b7 |
| Blues | 1 b3 4 b5 5 b7 |
| Dorian | 1 2 b3 4 5 6 b7 |
| Mixolydian | 1 2 3 4 5 6 b7 |
| Phrygian | 1 b2 b3 4 5 b6 b7 |
| Lydian | 1 2 3 #4 5 6 7 |
| Harmonic Minor | 1 2 b3 4 5 b6 7 |
| Whole Tone | 1 2 3 #4 b6 b7 |
| Diminished | 1 2 b3 4 b5 b6 6 7 |

---

## Triad Notation

Triads are computed diatonically from the selected scale and labeled with Roman numerals.

- Uppercase (I, IV, V) — major triads
- Lowercase (ii, iii, vi) — minor triads
- Degree symbol suffix (vii°) — diminished triads
- Plus suffix — augmented triads

When a triad is selected, dot labels switch to R / 3 / 5 regardless of the current label mode, and all non-triad scale tones dim out.

---

## Browser Compatibility

Tested in Chrome, Firefox, Safari, and Edge. Requires ES6 support (any browser released after 2016). The collapsible options panel uses the native details element, supported in all modern browsers.

---

## Technical Notes

- Single self-contained HTML file — no dependencies, no build step, no network requests
- All music theory (scale construction, interval naming, triad quality detection, role mapping) computed in vanilla JavaScript at runtime
- Fretboard renders as a CSS flexbox grid; string gauges, fret markers, and the nut divider are CSS-driven
- Color palettes defined as data objects; adding a new palette requires one new entry in the PALETTES constant
