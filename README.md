# A Family Voyage · Columbia, SC

A self-contained, single-file web app: an interactive agenda for a family vacation
in **Columbia, South Carolina** (Fri July 24 – Fri July 31, 2026), for four
families staying together at the "Port of Call." Phone-shaped, with a cruise /
ports-of-call aesthetic, one photo per stop, and a venue map with directions.

## Run it

There is **no build step and no dependencies to install** — it's one HTML file.

```bash
# Option A — just open it
open index.html

# Option B — serve it (recommended; some browsers block CDN loads on file://)
python3 -m http.server 8000   # then visit http://localhost:8000
```

To deploy, drop `index.html` + `images/` on any static host (Vercel, Netlify,
GitHub Pages, S3 — anything that serves files).

## What's inside

- **`index.html`** — the entire app: styles, trip data, and React components.
  React 18 + `@babel/standalone` are loaded from a CDN and transpiled in the
  browser; there's no bundler.
- **`images/`** — trip cover, one hero per day, and one photo per stop. These
  are placeholder stock photos (cruise/activity themed) meant to be swapped for
  the family's own photos. Naming: `trip-hero.jpg`, `day-{N}-hero.jpg`,
  `stop-{day}-{n}.jpg`. Filenames must match the references in `index.html`
  exactly — there's no fallback image.
- **`CREDITS.md`** — source and license for every placeholder image.

## Editing the trip

The whole itinerary is plain-JS data near the top of `index.html`: `TRIP_META`
(title, dates), `DAYS[]` (each day's stops, addresses, descriptions, fun facts),
and `MEAL_IDEAS[]`. Change the trip by changing that data — the components
render whatever it contains.

## Replacing the photos

Drop your own JPEGs into `images/` using the existing filenames (overwriting the
placeholders). Aim for ~1200px on the long edge. No code changes needed.
