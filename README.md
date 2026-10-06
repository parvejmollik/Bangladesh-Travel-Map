# Bangladesh-Travel-Map
Interactive Bangladesh travel map: mark visited districts and download your map as PNG, JPG or PDF. Includes a 64-district guide, a quiz and a trip planner with route and budget estimates.

# আমার বাংলাদেশ — Bangladesh Travel Map

An interactive Bangladesh travel toolkit in a single HTML file. Mark the districts you've visited and download your map as **PNG, JPG or PDF**, browse a 64-district guide, play a quiz, and sketch a trip with route and budget estimates.

**Live demo:** https://apnar-username.github.io/amar-bangladesh-map/

## Features

### My map
- Real-shape map of all 64 districts with Bangla names
- Click a district on the map, or pick from a list grouped by the 8 divisions
- Search by name, 5 colour themes, live counter and progress bar
- Download a share-ready image as PNG, JPG or PDF
- Your selection is saved in your browser (localStorage), nothing is sent to a server

### Explore (কোথায় ঘুরবেন)
- A card for each of the 64 districts: what it's known for and its main places to visit
- Filter by division, search by district, place or famous item
- Mark a district as visited, or add it to your trip, straight from the card

### Quiz (খেলা)
- 10 fresh questions every round: spot the highlighted district on the map, match places and famous things to districts, name the division
- Instant feedback and a final score

### Trip planner (ট্রিপ প্ল্যানার)
- Choose a starting district, the districts to visit (on the map or from the list) and which places to see in each
- Auto-sorts the stops into the shortest route (exact search for up to 8 districts), or you pick the first stop
- Set the number of days, an optional budget, trip type, number of travellers and whether to return to the start
- Get a day-by-day plan, total distance and a cost estimate for three comfort levels
- Print or save the plan as PDF

Works on mobile and desktop, with light and dark mode.

## Run locally

It is a single static file. No install and no build step.

**Option 1: open the file.** Double-click `index.html`.

**Option 2: local server.** In the project folder run:

```
python -m http.server 8000
```

then open http://localhost:8000. Stop it with `Ctrl + C`.

An internet connection is needed to load the Bangla fonts from Google Fonts. Without it, the page falls back to system fonts.

Note: browsers store saved selections separately for `file://` and `localhost`, so they won't show the same visited districts.

## Deploy on GitHub Pages

1. Push `index.html` to the `main` branch
2. Go to **Settings → Pages**
3. Under **Source**, choose **Deploy from a branch**, then `main` and `/ (root)`
4. Save. The site will be live in a minute or two.

## Customise

Everything lives in `index.html`.

- **Themes:** edit the `T` array in the script
- **Guide content:** edit the text block inside `E0` (one line per district: `name|famous for|place, place, place`)
- **Cost estimates:** edit the `TI` array (cost per km, hotel, food and local costs for each level)
- **Download layout:** edit the `render()` function
- **Page colours and fonts:** edit the CSS variables at the top

## How it works

- The map is inline SVG, one `<path>` per district, reused by the explore cards, quiz and planner.
- The download image is drawn on an HTML canvas from the same paths. PNG and JPG come straight from the canvas. The PDF is built in the browser by embedding the JPG in a one-page PDF, so no library is needed.
- Trip distances are straight-line distances between district centres, multiplied by 1.3 to approximate road distance.

## Data and credits

- District boundaries and Bengali names come from the [`bangladesh-geo-data`](https://pypi.org/project/bangladesh-geo-data/) Python package, simplified to keep the file small. Shapes are approximate and not for navigation or survey use.
- Fonts: [Hind Siliguri](https://fonts.google.com/specimen/Hind+Siliguri) and [Tiro Bangla](https://fonts.google.com/specimen/Tiro+Bangla) via Google Fonts.

## Disclaimer

Guide entries are short summaries and may be incomplete. Distances and costs are rough estimates, not quotes. Check fares, hotels, road conditions and local rules before travelling, especially for hill and protected areas.

## License

MIT for the code. See `LICENSE`. The map data keeps the license of its original source.
