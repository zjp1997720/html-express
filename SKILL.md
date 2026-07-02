---
name: html-express
description: "Create structured, readable, self-contained HTML reports from dense information: research notes, comparison matrices, checklists, data dashboards, timelines, and decision pages. Use when a user asks for an HTML report, visual summary, dashboard, comparison page, or a one-file web page they can open locally. The output is a single .html file with inline CSS and no runtime dependencies."
---

# html-express

Use this skill when dense information would be hard to scan in plain Markdown.

The goal is a single self-contained `.html` file that a user can open locally, share, or archive without a build step.

## Why HTML Instead Of Markdown

- HTML handles hierarchy, tables, metrics, timelines, and collapsible sections better than Markdown.
- A single `.html` file is portable, inspectable, and easy to share.
- Use HTML when the reader would otherwise need to work hard to scan the answer.
- Keep simple answers in Markdown.

## Route Or Skip

| Signal | Route |
|---|---|
| Research report, visual summary, comparison matrix, dashboard, checklist, timeline, decision page | Use this skill |
| One short answer or small list | Answer in Markdown |
| Production PDF, resume, slide deck, landing page, video, animation, deployment | Use a dedicated tool or skill for that medium |

## Component Library

Reusable snippets live in `assets/components/`.

| Component | Use for |
|---|---|
| `metric-card` | Key numbers and status metrics |
| `comparison-table` | Comparing options side by side |
| `data-table` | Structured data lists |
| `timeline` | Milestones and roadmaps |
| `checklist` | Steps, SOPs, readiness checks |
| `quote-card` | Judgments, quotes, or highlighted takeaways |
| `code-block` | Commands, config, code snippets |
| `details` | Long content collapsed by default |
| `badge` | Status labels |
| `columns` | Parallel views or grouped ideas |

Also use:

```text
assets/skeleton.html
assets/tokens.css
assets/demo-all.html
```

## Assembly Workflow

1. Identify the information shape: comparison, metric, timeline, checklist, quote, code, or decision.
2. Pick 2-5 fitting components from `assets/components/`.
3. Start from `assets/skeleton.html`.
4. Inline the full content of `assets/tokens.css` into the top `<style>` block so the final file has no external dependency.
5. Fill real content. Do not leave placeholders. If data is missing, mark it explicitly as `[data needed: reason]`.
6. Save one `.html` file and, when possible, open it locally to verify layout and readability.

## Design Contract

The bundled default visual system is Warm Paper:

- warm paper background, not pure white
- restrained terracotta accent
- trust-blue section structure
- readable serif body text and sans-serif UI labels
- minimal shadow and 8px-style card radius
- no gradient-heavy, neon, glassmorphism, or decorative noise

You may replace `assets/tokens.css` with another brand system, but keep the component classes and self-contained output rule.

## Output Rules

- Produce exactly one self-contained `.html` file unless the user asks otherwise.
- Inline CSS into the final HTML.
- Do not reference local machine paths.
- Do not invent metrics, statistics, quotes, or citations.
- Do not leave `TODO`, `TBD`, `Lorem`, or placeholder brackets in final user-facing content.
- Keep text readable on mobile.
- Use native HTML features such as `<details>` before adding JavaScript.

## Final Response

Return:

- the generated file path
- what information structure you used
- any missing data that was explicitly marked
- whether you verified the HTML locally
