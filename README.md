# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Real platforms like Spotify and YouTube use hybrid filtering, which combines collaborative filtering (recommending what listeners with similar behavior enjoyed) with content-based filtering (recommending songs whose attributes resemble ones you already like). The **input data** is what the system knows about each song, such as its genre, mood, tempo, energy, and acousticness. The **user preferences** come from what a listener says and does: explicit signals like likes and playlist adds, and implicit signals like plays, skips, and replays. The **ranking** step scores every candidate song for how likely the listener is to enjoy it, sorts the list, and re-orders it for variety before showing the top results. VibeFinder is content-based only. It scores genre, mood, energy, and acousticness against one user's stated preferences. The tradeoff is that it can't learn from what a user actually plays or skips, and it can't discover cross-genre picks from other listeners' taste, so it only crosses genres when songs share attributes like energy.

### Features used in this simulation

**`Song`** (one row of `data/songs.csv`)

| Feature | Type | Used for scoring? |
|---|---|---|
| `genre` | text | Yes |
| `mood` | text | Yes |
| `energy` | 0.0–1.0 | Yes |
| `acousticness` | 0.0–1.0 | Yes |
| `tempo_bpm`, `valence`, `danceability` | numbers | Loaded, not scored yet |
| `id`, `title`, `artist` | labels | Shown in output only |

**`UserProfile`** (one listener's stated taste)

| Field | Example | Meaning |
|---|---|---|
| `favorite_genre` | `"pop"` | Genre the listener wants most |
| `favorite_mood` | `"happy"` | Mood the listener wants |
| `target_energy` | `0.8` | Energy level to get close to (not "the higher the better") |
| `likes_acoustic` | `False` | Whether acoustic songs should earn points or lose them |

---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

Paste a sample of your recommender's output here as a text block so a reader can see what it produces:

```
# e.g.:
# User profile: genre=indie, mood=chill, energy=low
# Recommendations:
#   1. ...
#   2. ...
#   3. ...
```

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this



