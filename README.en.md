# Ratoon · 破竹 (PoZhu)

> **Let one non-programmer + a team of AI agents maintain multiple software projects over the long run — without being dragged down by three things: amnesia, rework, and bills.**

[中文](README.md) ｜ **English**

---

## What this is

Ratoon is a set of **Markdown protocols** (dozens of spec files) — not a code framework, not an app, not a tool. It defines one thing:

> **How one non-programmer and a group of AI agents collaborate to turn "an idea" into "software that keeps evolving".**

The core metaphor, in one line: **turn one conversation into one "node of bamboo"** — every node has a boundary, evidence, and can stop.

- The Chinese name **破竹** (PoZhu) means "splitting bamboo with unstoppable momentum" — and also "bamboo grows node by node, each node complete and independent".
- The English name **Ratoon** means the new shoot that regrows from the root after harvest — finish one project, grow the next from the same method.

---

## What problems it solves

If you've built personal projects with AI, you've hit these three:

| Pain | How Ratoon fixes it |
|---|---|
| 🧠 **Amnesia** | A new session forgets where things stood → each project keeps **a set of files as durable memory** (`00_根/` + `40_节/`); a new session resumes by reading files, not replaying a conversation |
| 🔁 **Rework** | Every change replays the whole context and re-does work → **one iteration = one node**, each node lands its own record when done (one session can contain several nodes); **restate + size grading + round-trip budget** catch misunderstanding before work begins |
| 💸 **Bills** | "Is it done?" is unclear; tokens keep burning → **done = a real artifact is produced** (something the user can see/click/hear), not an agent saying "done" |

Plus a fourth: **cross-project reuse** — something validated in one project carries into the next (`库/`).

---

## Quick start (3 steps)

You need **no coding knowledge and no passwords to memorize**. To start a new project:

1. Copy `bootstrap.md` into your new project folder (top level).
2. Tell the agent: **"Read bootstrap.md and do what it says."**
3. When it asks where Ratoon lives, paste the folder's path.

It then: verifies it can read → writes the entry into your project's `AGENTS.md` → runs **ideation** (gives you a plain-language blueprint) → you approve → starts building node by node.

> Why this step exists: when you switch agent tools, the agent won't find a protocol outside the project on its own. `AGENTS.md` is your project's own entry point, and it survives tool changes.

---

## Day to day, you only do two things

| # | What | How |
|---|---|---|
| **1** | **Say the requirement** | In plain words. The agent recognizes which scene you're in and reads the right spec; it re-reads on its own if unsure |
| **2** | **Review the output and decide** | The agent gives you a **real environment URL** → you open, click, look → say "OK" or "not right" |

**You don't need to**: read code, read files, or watch progress. Tech choices are explained in plain language by the agent, and **you decide**.

**When something breaks, just speak plainly**:
- Broke it → "**broke it, undo**" (the agent rolls back in one step and shows you the restored result)
- Can't say what's wrong → "**looks wrong, compare with the last version**"
- Don't know what to build → "**show me the overview, what's not done**"
- Too many ideas → "**I have a pile of ideas, take them all**"

**When to close a node**: you don't judge — the agent says "this node passed, suggest closing now", you say "yes". Then it hands you a handoff line: open a new conversation **in the project folder** and say "continue", or keep going in the same conversation with the next node.

**The one moment you personally approve**: the **blueprint** when starting a project — a plain-language page (including "how this plan is most likely to fail + what to guard against first"). You read it and say "OK" or "not right".

---

## Core design (for those who want to go deeper)

- **Facts to the agent, decisions to the user** — anything checkable the agent checks itself; only goals / trade-offs / taste are put to the user.
- **Single source of truth** — every piece of information has one authoritative place; duplicate records are defects.
- **Done is evidence, not self-claim** — no real artifact = not done, even if the code is written and tests pass.
- **One node of bamboo** — one iteration = one node; grow one node and you may stop (one session can contain several nodes).
- **The framework must not become a cost itself** — the injected layer stays short and rarely changes; methods come from measurement, prefer deleting mechanisms.

Three phases: **① Ideation (direction, blueprint) → ② Development (node by node) → ③ Closing (compliance, license, publish, retro)**.

---

## Known boundaries (an honest statement)

Ratoon is a **"cost-control + truth-tracking"** protocol, not an "engineering-quality" system. Projects built with it need your attention on four layers:

- **Data**: the protocol does not automate database migrations / backups; back up your data yourself (especially before release).
- **Security**: it prevents "keys / personal info entering the repo", but auth, injection defense (SQL / XSS), CSRF, etc. need to be added per project — **especially if it touches other people's data or money**.
- **Testing**: acceptance relies on "the user sees the real output"; automated testing is not mandatory. Long-lived projects should add regression tests.
- **Operations**: no built-in monitoring / alerting / logging after release; configure online availability yourself.

These are **design trade-offs, not bugs** — the protocol optimizes "saving money + delivering real things" to an extreme, at the cost of engineering quality relying more on the user's diligence. Add the corresponding protections to important projects.

---

## Credits / sources

Ratoon's mechanisms borrow **ideas and forms** from the projects below (Ratoon's text and code are **independently written**; nothing was copied):

| Source | License | What was borrowed |
|---|---|---|
| [zeekmartin/vibe-coding-framework](https://github.com/zeekmartin/vibe-coding-framework) | MIT | prompt as first-class citizen, single source of truth |
| [azizakmal97/vibe-coding-template](https://github.com/azizakmal97/vibe-coding-template) | MIT | AGENTS.md as distribution point, file-line budgets |
| [vadim-works/vibe-coding-guide](https://github.com/vadim-works/vibe-coding-guide) | CC-BY-4.0 | DoR-DoD chain, five steps |
| [tradecatlabs/vibe-coding-cn](https://github.com/tradecatlabs/vibe-coding-cn) | MIT | five-layer model inspiration |
| [dui14/vibe-coding-workflow](https://github.com/dui14/vibe-coding-workflow) | Unlicensed | bootstrap flow shape (idea only) |
| [saneroen/vibe-coding-starter-kit](https://github.com/saneroen/vibe-coding-starter-kit) | Unlicensed | interface-first (idea only) |
| [Claude Code docs · memory](https://code.claude.com/docs/en/memory) | Official docs (conclusion cited) | ≤200-line threshold rationale |
| headroom · caveman · ponytail · cc-thinking-skills · skills · cot-lint | MIT / Apache-2.0 etc. | cache-prefix alignment (headroom), glossary _Avoid_ (skills), explanation-length ceiling (ponytail), no-compression-in-danger (caveman), proof-of-behavior four fields, absorb-not-add, whitelist, etc. |

> **Two unlicensed sources** (dui14, saneroen): Ratoon only credits them for "idea inspiration"; it is **not based on their content**, and **does not copy their text or code**.

---

## License

[CC BY-SA 4.0](LICENSE) · Author **wumohan**

You may freely **use, modify, and redistribute**, but you must: ① **give attribution**; ② release derivative works under the **same license** (share-alike).

---

## File structure

| File | Role |
|---|---|
| `bootstrap.md` | New-project bootstrap (copy & use, delete when done) |
| `00_协议.md` | Sole entry: ten iron rules + glossary + reading index + exclusion list |
| `01-需求链与节.md` | Development phase: one sentence → one node, the full chain |
| `02-证据与验收.md` | What "done" means, how to prove it, how to roll back |
| `03-根与模板.md` | Directory structure, templates, scene detection, Git discipline |
| `04-跨项目资产库.md` | Cross-project reuse mechanism |
| `阶段①_构思/` | Ideation phase (direction, blueprint) |
| `阶段③_收尾/` | Closing phase (compliance, license, publish, retro) |
| `库/` | Cross-project reusable assets |

> `99_版本记录.md` is the developer's **private reference** (version history + decision rationale), **not published with the repo**.