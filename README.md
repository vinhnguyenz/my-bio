# my-bio

Personal cinematic bio of **Nguyen Van Vinh** — a night walk through a Kyoto mountain temple, rebuilt as a one-page about site.

Built from the [Kage](https://threeui.com/browse) landing page on [ThreeUI](https://threeui.com), then rewritten and wired up with [Grok](https://grok.com) (xAI): copy, education cards, photo lightbox, and the HANU / Trần Văn Bảo story on top of the live WebGL scene.

> FIT · Hanoi University · third-year Software Engineering student.

---

## What it is

A **static** HTML page. No build step, no npm, no framework.

- Fixed full-viewport **Three.js r149** canvas (`three.min.js`, vendored)
- Scroll-driven camera through a procedural temple: lanterns, vermilion moon, fog, falling leaves
- Onest type, vermilion `#e0231c`, layered WebP foreground cutouts
- Overlay chapters for the bio: About, Education, Courses, Afterlight
- Education frames hold real photos; the corner arrow opens a lightbox

Open it over **HTTP**, not `file://` — the local fonts and WebP paths need a server.

```bash
git clone https://github.com/vinhnguyenz/my-bio.git
cd my-bio
python3 -m http.server 4173
# then http://127.0.0.1:4173
```

GitHub Pages works the same way: set the root of this repo as the site source.

---

## Chapters

| # | Section | Content |
|---|---------|---------|
| 00 | Hero | “Code that turns ideas into form.” |
| 01 | About | Bio, hometown, FIT |
| 02 | Education | Trần Văn Bảo High School · Hanoi University · Honors |
| 03 | Courses | Semester work at FIT |
| 04 | Afterlight | Quote + close |

Click the **↗** on an Education card to open that photo full-size. `Esc`, the ×, or a click on the dimmed backdrop closes it.

Swap photos by replacing files in `photos/` (`highschool.jpg`, `hanu.jpg`, `honors.jpg`). The lightbox reads whatever is in the card.

---

## Repo layout

```
my-bio/
├── index.html          # page + CSS + scene + lightbox
├── three.min.js        # Three.js r149 (vendored)
├── fonts.css           # Onest
├── photos/             # education card images
├── generated/          # chapter stills from the Kage kit
├── foreground/png/     # pine, maple, lantern, grass cutouts
└── README.md
```

Single HTML file on purpose. The original Kage kit ships the same way.

---

## Stack

- **ThreeUI — Kage landing page** — scene, camera path, post-processing, cloth/peek (peek + giant wordmark removed here)
- **Three.js r149** — `three.min.js` in this repo
- **Grok (xAI)** — integration, copy, card photos, lightbox, this README
- **Onest** + CSS variables (`--ink`, `--vermilion`)

No package manager. Prefer `prefers-reduced-motion` is already respected by the scene.

---

## Notes

- Hard-refresh after swapping images (`Ctrl+Shift+R`).
- The WebGL canvas sits behind the document (`#gl`). Cards with `.card-photo` skip the live blit and the dark cloth overlay so the photo stays readable.
- Lightbox markup is `#photo-lb` at the bottom of `index.html`; styles live in the same file under `/* photo lightbox */`.

---

## Credits

- Scene and interaction design: **Kage** on [ThreeUI](https://threeui.com)
- Renderer: [Three.js](https://threejs.org)
- Adaptation + extra UI: Nguyen Van Vinh, with Grok

Not affiliated with ThreeUI or xAI. Kage is used as a starting template.

---

© 2026 Nguyen Van Vinh · HANU FIT
