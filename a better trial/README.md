# Gene-ius · The Daily Dive for Rare Answers

A browser game: answer 7 open biology questions. Rarer correct answers fold your protein deeper.

## Files
- `index.html` – the whole game (no build step)
- `database.rules.json` – security rules for the shared leaderboard
- `README.md` – this file

## 1. Deploy on GitHub Pages
1. Create a public repo (e.g. `geneius`) and upload all three files.
2. Settings -> Pages -> Source: "Deploy from a branch" -> Branch `main`, folder `/ (root)` -> Save.
3. Your link: `https://YOUR-USERNAME.github.io/geneius/`

## 2. Turn on the shared leaderboard (Firebase, free)
1. Go to https://console.firebase.google.com -> Add project (skip Analytics).
2. Build -> Realtime Database -> Create Database. Pick a nearby location (e.g. Singapore) and start in **locked mode**.
3. Open the **Rules** tab, replace everything with the contents of `database.rules.json`, click **Publish**.
4. On the **Data** tab, copy the database URL (looks like `https://your-project-default-rtdb.firebaseio.com`).
5. In `index.html`, find `const FIREBASE_URL='';` and paste the URL between the quotes. Commit the change on GitHub.

Without step 5 the game still works, but the leaderboard is local to each player's browser and shows sample divers.

## Notes
- Only daily dives are posted to the leaderboard, once per day per player. Random dives are practice.
- Anyone can read scores and add a validated entry, but nobody can edit or delete entries through the game.
- Scores are computed in the browser, so a determined player could fake one. Fine for a casual game.
- Answers are checked against built-in answers, then live against the Wikipedia API (no key needed).
