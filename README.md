# MyChessInsights

Interactive personal analytics for Chess.com games: track Elo trends, performance metrics, and blunder insights.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📖 Overview

**MyChessInsights** is a Dash/Plotly–powered analytics tool that pulls your Chess.com game archive, tracks your Elo over time, compares your White vs. Black performance, and runs Stockfish-driven accuracy/blunder analyses. Then, these analyses are ported to interactive visualizations so you can see your progress over time, plus pinpoint strengths, weaknesses, and improvement opportunities to improve your chess game.

---

## 🚀 Features

- **Elo Over Time**  
  Line chart of your Chess.com rating by game (X=datetime, Y=endingElo), or resampled daily/weekly/monthly.

- **Color Performance**  
  Circle chart breaking down win/draw/loss percentages for all games and when playing White or Black. Breaks down type of win/loss (by checkmate, timeout, etc).

- **Engine Analysis**  
  Stockfish per-half-move eval, with classification of each move accuracy (Brilliant, Best, Excellent, Great, Good, Inaccuracy, Miss, Mistake, Blunder, plus the played move and best move centipawn deltas). Additional metadata highlighting overall game-accuracy _Great_/**Brilliant**, plus biggest blunders, missed-chances, and  metrics. Results saved to a local database for fast queries.

- **Group Level Analysis**  
  Analyze an entire portfolio of games to describe style, point out weaknesses, and suggest areas to improve play (e.g. increase early rook movement, pawn play, development speed).

- **Blunder/Missed Tactics Explorer**  
  Table of your biggest mistakes and missed opportunities/forks/tactics (move, date, centipawn swing) with links back to the original game. Can also revisit Brilliant and Great moves, plus times where you successfully punished mistakes. Detect missed mates in ≤10 moves.

- **Custom Date Ranges**  
  Filter your archive by any date span and instantly regenerate all visuals.

- **Caching**  
  Memoized engine runs (SQLite or disk cache) keep your app responsive.

---

## 🛠️ Installation

### Prerequisites

- Python 3.8 or newer  
- [Stockfish](https://stockfishchess.org/download/) v15+ installed and on your `PATH` (or specify path via `STOCKFISH_PATH`)

### Clone & Setup

```bash
git clone https://github.com/<your-username>/mychessinsights.git
cd mychessinsights

# Option A: venv + pip
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

# Option B: Poetry
# poetry install
```

---

## ⚙️ Configuration

Set the following environment variables (or adjust in a `config.py`):

```bash
export CHESS_USERNAME="your_chesscom_username"
export STOCKFISH_PATH="/path/to/stockfish"
```

---

## ▶️ Usage

Launch the dashboard:

```bash
python -m mychessinsights.app
# then open http://127.0.0.1:8050
```

Use the date picker, depth controls, and filters to explore:

- Elo timeline
- Color-based win/draw/loss breakdown
- Engine-driven accuracy and blunder metrics
- Ranked tables of biggest mistakes

---

## 📁 Project Structure

```
mychessinsights/
├── LICENSE
├── README.md
├── requirements.txt      # or pyproject.toml / Poetry config
├── .gitignore

├── src/mychessinsights/
│   ├── app.py            # Dash layout & callbacks
│   ├── cache.py          # caching utilities
│   ├── data/
│   │   ├── fetcher.py    # Chess.com API client
│   │   └── loader.py     # archive loader & cleaning
│   ├── analysis/
│   │   ├── engine.py     # Stockfish interface & PGN parsing
│   │   └── metrics.py    # compute centipawn loss, blunders, aggregates
│   └── viz/
│       └── charts.py     # pure Plotly figure generators

├── notebooks/            # Jupyter prototypes
└── tests/                # pytest suite
```

---

## 🧪 Testing

```bash
pytest --cov=mychessinsights
```

---

## 🤝 Contributing

1. Fork the repo  
2. Create a branch (`git checkout -b feature/new-feature`)  
3. Commit changes (`git commit -m "Add feature"`)  
4. Push branch (`git push origin feature/new-feature`)  
5. Open a Pull Request  

Please run tests and adhere to PEP 8 + black formatting.

---

## 📝 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---

*Built with ♥ by Timothy Nolan Jr.*  
