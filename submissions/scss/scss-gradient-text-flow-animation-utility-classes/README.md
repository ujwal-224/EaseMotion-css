# Gradient Text Flow & Animation Utility Classes

**EaseMotion CSS SCSS Utility** · `submissions/scss/scss-gradient-text-flow-animation-utility-classes/`

---

## What does this do?

This SCSS partial provides a comprehensive set of mixins, keyframe definitions, and pre-built utility classes for applying smooth, animated gradient text effects to any text element. It supports five distinct animation styles — left-to-right flow, diagonal sweep, breathe/pulse, hue-wheel rotation, and shimmer highlight sweep — across 10 curated gradient presets.

All classes use the `-um` suffix per CONTRIBUTING guidelines to avoid naming conflicts with other contributors' submissions.

---

## How is it used?

### Option A — SCSS Mixin (recommended)

Import the partial and call a mixin in your SCSS:

```scss
@use 'path/to/_gradient-text-flow-animation-utility-classes' as ease-grad;

// Two-stop gradient flow
.hero-title {
  @include ease-grad.gradient-text-flow-um(#06b6d4, #6366f1);
}

// Three-stop gradient flow with custom duration
.section-label {
  @include ease-grad.gradient-text-flow-um(
    $from:     #f97316,
    $to:       #9333ea,
    $via:      #ec4899,
    $duration: 3s
  );
}

// Diagonal sweep
.card-heading {
  @include ease-grad.gradient-text-diagonal-um(#4facfe, #f472b6);
}

// Pulsing breathe effect
.live-badge {
  @include ease-grad.gradient-text-pulse-um(#6ee7b7, #059669);
}

// Full hue-wheel rotation (60fps via filter: hue-rotate)
.rainbow-tag {
  @include ease-grad.gradient-text-hue-spin-um(#ec4899, #6366f1, $duration: 6s);
}

// Shimmer light sweep
.premium-label {
  @include ease-grad.gradient-text-shimmer-um(#fbbf24, #f97316);
}
```

### Option B — Utility Classes (HTML)

Compose classes directly in markup without writing any SCSS:

```html
<!-- Aurora gradient, medium-speed left-to-right flow -->
<h1 class="ease-gradient-text-um ease-gradient-aurora-um ease-gradient-flow-medium-um">
  Deep Space Telemetry
</h1>

<!-- Gold shimmer effect -->
<span class="ease-gradient-text-um ease-gradient-gold-um ease-gradient-shimmer-um">
  PRO
</span>

<!-- Neon hue-spin -->
<h2 class="ease-gradient-text-um ease-gradient-neon-um ease-gradient-hue-spin-um">
  Quantum Exchange
</h2>

<!-- Slow pulsing sunset gradient -->
<p class="ease-gradient-text-um ease-gradient-sunset-um ease-gradient-pulse-um">
  Loading mission data...
</p>
```

---

## Mixin Parameters

### `gradient-text-flow-um()` — Core mixin

| Parameter | Type | Default | Description |
|---|---|---|---|
| `$from` | Color | `#6366f1` | Gradient start color |
| `$to` | Color | `#ec4899` | Gradient end color |
| `$via` | Color \| null | `null` | Optional mid-stop (produces a 3-stop gradient) |
| `$direction` | String | `to right` | Gradient direction or angle (e.g. `135deg`) |
| `$duration` | Number | `4s` | Animation duration |
| `$easing` | String | `linear` | CSS timing function |
| `$keyframe` | String | `ease-gradient-flow-lr-um` | `@keyframes` name to drive the animation |

### `gradient-text-diagonal-um()` — Diagonal sweep

| Parameter | Type | Default | Description |
|---|---|---|---|
| `$from` | Color | `#f97316` | Gradient start color |
| `$to` | Color | `#9333ea` | Gradient end color |
| `$via` | Color \| null | `null` | Optional mid-stop |
| `$duration` | Number | `4s` | Animation duration |

### `gradient-text-pulse-um()` — Breathe/pulse

| Parameter | Type | Default | Description |
|---|---|---|---|
| `$from` | Color | `#4facfe` | Gradient start color |
| `$to` | Color | `#f472b6` | Gradient end color |
| `$via` | Color \| null | `null` | Optional mid-stop |
| `$duration` | Number | `4s` | Animation duration |

### `gradient-text-hue-spin-um()` — Hue-wheel rotation

| Parameter | Type | Default | Description |
|---|---|---|---|
| `$from` | Color | `#ec4899` | Gradient start color |
| `$to` | Color | `#6366f1` | Gradient end color |
| `$duration` | Number | `8s` | Animation duration |

### `gradient-text-shimmer-um()` — Light sweep

| Parameter | Type | Default | Description |
|---|---|---|---|
| `$from` | Color | `#fbbf24` | Gradient start color |
| `$to` | Color | `#f97316` | Gradient end color |
| `$duration` | Number | `2.5s` | Animation duration |

---

## Keyframes Defined

| Keyframe | Effect |
|---|---|
| `ease-gradient-flow-lr-um` | Pans `background-position` 0% → 100% → 0% horizontally |
| `ease-gradient-flow-diagonal-um` | Pans `background-position` diagonally 0%/0% → 100%/100% |
| `ease-gradient-pulse-um` | Scales `background-size` 200% ↔ 250% and fades `opacity` |
| `ease-gradient-spin-um` | Rotates hue via `filter: hue-rotate(0 → 360deg)` |
| `ease-gradient-shimmer-um` | Sweeps `background-position` −200% → +200% |

---

## Preset Color Classes

| Class | From | Via | To |
|---|---|---|---|
| `.ease-gradient-aurora-um` | `#4facfe` | `#a78bfa` | `#f472b6` |
| `.ease-gradient-sunset-um` | `#f97316` | `#ec4899` | `#9333ea` |
| `.ease-gradient-ocean-um` | `#06b6d4` | `#3b82f6` | `#6366f1` |
| `.ease-gradient-forest-um` | `#6ee7b7` | `#34d399` | `#059669` |
| `.ease-gradient-fire-um` | `#fde68a` | `#f97316` | `#dc2626` |
| `.ease-gradient-candy-um` | `#f9a8d4` | `#c084fc` | `#818cf8` |
| `.ease-gradient-neon-um` | `#00fff0` | `#a855f7` | `#ec4899` |
| `.ease-gradient-gold-um` | `#fbbf24` | `#f59e0b` | `#d97706` |
| `.ease-gradient-plasma-um` | `#e879f9` | `#818cf8` | `#22d3ee` |
| `.ease-gradient-cosmic-um` | `#1d4ed8` | `#7c3aed` | `#db2777` |

---

## Why is it useful?

Gradient text is one of the most visually impactful typographic effects in modern UI design, but implementing it with animations typically requires repetitive boilerplate (3–4 CSS properties + a keyframe). This partial eliminates that repetition entirely. A single `@include` call generates all necessary cross-browser rules (`background-clip: text`, `-webkit-text-fill-color: transparent`, `animation`) with sensible defaults and full customization via parameters.

It fits EaseMotion's philosophy of **human-readable, animation-first CSS** — developers declare intent (`gradient-text-shimmer-um`) rather than writing low-level animation mechanics. The `prefers-reduced-motion` guard is baked into every mixin so accessibility is automatic.

---

## Accessibility

All animations automatically disable when the user has enabled **Reduce Motion** in their OS:

```scss
@media (prefers-reduced-motion: reduce) {
  // animation: none on all animated classes
  // Static gradient preserved for visual contrast
}
```