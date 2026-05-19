# Liquid glass — iOS 26 prototype

An interactive frosted-glass navigation prototype with live material controls. Click between the labels to feel the pill morph; dial the sliders to tune the glass material in real time.

Built with vanilla HTML + CSS + JS. **No frameworks. No build step.** Just a single `index.html` you can drop anywhere.

## Run locally

```bash
# Any static file server works. With Python:
python3 -m http.server 8000
# Then open http://localhost:8000
```

Or just double-click `index.html` to open it in your browser.

## Deploy to Vercel via GitHub

1. Create a new GitHub repo (e.g. `liquid-glass-nav`) and push these two files to its root:
   - `index.html`
   - `README.md`

2. Go to [vercel.com/new](https://vercel.com/new) and import the repo.

3. When asked for project settings, leave everything at the defaults — Vercel detects this as a static site automatically. No framework preset, no build command, no output directory.

4. Click **Deploy**. You'll have a public URL in about 30 seconds.

Future pushes to `main` will auto-deploy.

## Sliders

| Slider | Range | Default | What it does |
| --- | --- | --- | --- |
| **Blur** | 0–50px | 26px | Backdrop blur on the nav. iOS "Regular Material" is 20px. |
| **Saturation** | 50–250% | 200% | Color pop behind the glass. 180% matches iOS UIBlurEffect. |
| **Base opacity** | 0–1 | 0.45 | Alpha of the white tint layered over the blur. |
| **Top highlight** | 0–1 | 0.50 | Intensity of the linear gradient that fades from white to transparent at the top — gives the glass a "wet" specular look. |
| **Edge highlight** | 0–1 | 0.55 | Inset top-edge highlight that makes the glass feel three-dimensional. |
| **Refraction** | 0–0.5 | 0.18 | Inset bottom highlight that simulates the refracted edge where light bends through the glass. |
| **Shadow** | 0–0.5 | 0.22 | Outer drop-shadow alpha. Higher = nav reads as more elevated. |

Click **Reset to defaults** to snap everything back.

## Browser support

- `backdrop-filter` works in all modern browsers (Chrome, Safari, Firefox, Edge).
- Safari uses `-webkit-backdrop-filter` (already included).
- Mobile Safari, iOS Chrome, and Android Chrome all render correctly.

## Customizing

Want to use this in your own project? The whole nav is in one file:

- **HTML:** the `<nav class="nav-glass">` element with 4 buttons.
- **CSS:** all glass styling is under `.nav-glass` and driven by CSS custom properties — change a default value in `:root` style or in the inline `nav` style.
- **JS:** the morph uses the Web Animations API (`element.animate()`), about 40 lines.

Change the nav items by editing the four `<button class="nav-glass__item">` tags. To make them real links, swap `<button>` for `<a href="…">`.

## Credits

Built by Thomas McCluskey. Inspired by Apple's Liquid Glass design language introduced in iOS 26.
