# Multi-Skill Agentic Framework for IPL Cricket Analytics

**Google × Kaggle AI Agents Intensive Capstone 2026 — Freestyle Track**

A conversational AI agent that answers natural language questions about 17 seasons
of IPL cricket data (260K+ ball-by-ball delivery records) using Google Gemini
function-calling with a local Pandas fallback engine for error resilience.

---

## Architecture
User Question
↓
Gemini reads question + available tool schemas (auto-generated from type hints)
↓
Gemini decides which tool to call (get_top_batsmen / get_top_bowlers / analyze_venue / ...)
↓
Python executes the function locally on 260K+ Pandas records
↓
Result sent back to Gemini for natural language interpretation
↓
Answer returned to user

If API returns 503 / quota error:
↓
Local keyword-matching fallback engine activates
↓
User still gets an answer — zero crashes

## Key Insight Discovered

**Wankhede Stadium: 74.6% win rate for teams that field first** (118 matches analyzed).
This venue-level strategic pattern was surfaced entirely by the agent — not pre-coded.

## Tool Functions

| Function | What it does |
|---|---|
| `get_top_batsmen(n)` | Top n run-scorers across all seasons |
| `get_top_bowlers(n)` | Top n wicket-takers |
| `get_team_stats(team_name)` | Win rate and match record for any team |
| `analyze_venue(venue_name)` | Fielding-first vs batting-first win rates |
| `plot_top_batsmen_trends(n)` | Season-by-season run trend chart |

## Tech Stack

- Python, Pandas, NumPy
- Google Gemini API (`google-generativeai`)
- Kaggle Secrets (secure API key management)
- Seaborn / Matplotlib (visualization)

## Dataset

[IPL Complete Dataset 2008-2020](https://www.kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020)
— 260,920 deliveries across 816+ matches, 17 seasons

## Submission

- **Competition:** [Google × Kaggle AI Agents Intensive Vibe Coding Capstone](https://www.kaggle.com/competitions/vibecoding-agents-capstone-project)
- **Writeup:** [Multi-Skill Agentic Framework for IPL Analytics & Strategy](https://www.kaggle.com/competitions/vibecoding-agents-capstone-project/writeups/multi-skill-agentic-framework-for-ipl-analytics)
- **Track:** Freestyle
- **Badge Earned:** 5-Day AI Agents: Intensive Vibe Coding Course — Kaggle × Google (July 30, 2026)

## How to Run

1. Open the notebook on Kaggle
2. Add the IPL dataset (linked above)
3. Add your Gemini API key as a Kaggle Secret named `GEMINI_API_KEY`
4. Run all cells
