# Uttar Purv Abhivyakti
An interactive Twine game that explores the rich culture of Northeast India. Roam across the eight states, solve quizzes and puzzles, and collect points as you learn.

Play online
- https://skullfighter.github.io/Uttar-Purv-Abhivyakti/ (enable GitHub Pages; see “Deploy” below)

Overview
Uttar Purv Abhivyakti is designed as a cultural journey. Players can hop between states, discover facts, and take short quizzes and puzzles to earn points.

States covered
- Arunachal Pradesh
- Assam
- Manipur
- Meghalaya
- Mizoram
- Nagaland
- Sikkim
- Tripura

Key features
- Free exploration of each state’s passages
- Quizzes and puzzles with score tracking
- Replayable structure to improve your points
- Built with Twine (single HTML file, easy to host and share)

How to play
- Click through passages to travel between states.
- Read cultural snippets, images, and facts.
- Answer short quizzes/puzzles to earn points.
- Try to beat your best score while exploring all states.

Local setup (no install needed)
- If this repository contains an exported Twine HTML file (index.html):
  - Download or clone the repo
  - Double-click index.html to open it in your browser

Developing/updating the game
Option A: Twine GUI (recommended for content creators)
1) Open the Twine app (Desktop or Web).
2) Import your current HTML or Twine archive.
3) Edit passages and logic.
4) Export → Publish to File → Save as index.html at the repository root.
5) Commit and push.

Option B: Tweego (for source-first workflow, optional)
- Organize passages as .tw files and build via Tweego to index.html.
- Replace the built index.html in the repo and push.

Suggested scoring (SugarCube example)
If you’re using SugarCube, add this in the StoryInit/StartUp passage to track score:
```js
/* StoryInit (SugarCube) */
if (setup === undefined) { window.setup = {}; }
if (State.variables.score === undefined) { State.variables.score = 0; }
setup.addPoints = (n) => { State.variables.score += n; };
```
Use in a quiz passage:
```html
<<nobr>>
  Which state is famous for the Hornbill Festival?
  <<link "Nagaland">>
    <<run setup.addPoints(10)>>
    Correct! You earned 10 points.
    <<goto "Nagaland Hub">>
  <</link>>
  | 
  <<link "Another state">>
    Not quite—try exploring more!
    <<goto "Map">>
  <</link>>
<</nobr>>
```
Display score in your UI Bar or header passage:
```html
Score: $score
```

Repository structure (simple)
- index.html — exported Twine story (single file)
- assets/ — optional images/audio referenced by the story
- .github/workflows/deploy-pages.yml — auto-publish to GitHub Pages

Deploy to GitHub Pages
Option 1: GitHub Actions (included)
- The provided workflow publishes the repository root to Pages on every push to main.
- Make sure your exported Twine HTML is named index.html at the repo root.

Enable Pages:
1) Settings → Pages
2) Build and deployment → Source: GitHub Actions

Option 2: From branch (no workflow)
- Settings → Pages → Source: Deploy from a branch
- Branch: main, Folder: /(root)
- Ensure index.html is at the repository root.

Contributing
- Content: Ensure facts are accurate and culturally respectful. Add citations where possible.
- Accessibility: Prefer readable fonts, sufficient contrast, alt text for images, and keyboard-friendly navigation.
- Localization: Consider future support for Hindi/Assamese/other regional languages.

License
- Add a LICENSE file (e.g., MIT) if you want others to reuse or contribute.

Credits and acknowledgements
- List sources for cultural information, images, and any third-party assets used.

Questions or improvements?
- Open an issue with your suggestion or bug.
