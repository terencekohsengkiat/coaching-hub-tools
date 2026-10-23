# Coaching Hub Tools

Front-end pages for the Singapore Sailing Federation's Coaching Resource Hub, published with GitHub Pages and embedded in Google Sites.

| Page | What it shows | Where the data comes from |
|---|---|---|
| `training-venues/` | Map of training venues by boat class | Venues Google Sheet |
| `fdes-framework/` | FDES athlete development framework | FDES Google Sheet |
| `fdes-map/` | World regattas by boat class and FDES stage | Regattas Google Sheet |
| `rams-generator/` | AI risk assessment (RAMS) drafts | Gemini, via Apps Script |
| `coaching-philosophy/` | AI coaching philosophy drafts | Gemini, via Apps Script |

## Updating content

Edit the Google Sheet as before. Each page asks its Apps Script backend for fresh data every time it loads, so changes show up on the next page refresh. Nothing in this repository needs to change.

## How it works

Each Apps Script project is deployed as a web app and returns JSON (`?action=data`) or, for the AI tools, answers a POST. The pages call it with `fetch` and no cookies, which avoids Google's "Sorry, unable to open the file" error for people signed into more than one Google account.

No API keys are stored here. The Maps key is served by the backend from Script Properties; the Gemini key never leaves Apps Script. The AI tools are capped at 15 generations per day each.
