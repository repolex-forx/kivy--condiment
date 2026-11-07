# Repolex Knowledge Graph of kivy/condiment

RDF knowledge graph data for [kivy/condiment](https://github.com/kivy/condiment), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download kivy/condiment
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 64727710aec95cc52d00bff9b27807473f0bc70f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 64727710aec95cc52d00bff9b27807473f0bc70f
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d20b6487c61e7d1bde93acf4a14b7a89083a16d.nq.gz
│   ├── 110f93c75b08e4abf01ed5a71b91360a49d32de2.nq.gz
│   ├── 290d3a409fff5c22eaa4f8eaa5a8cace7a1346f5.nq.gz
│   ├── 3b385665b420942e0e572d50604f509b29d2b818.nq.gz
│   ├── 7a52fa45ab7cdad4c944dc4f529aa8f94fa40032.nq.gz
│   ├── b789e2f11f57608cb00f55b63d916cf77099aa18.nq.gz
│   ├── d707dacd27139766a01cb47044eb9b5681859ccf.nq.gz
│   └── f139af93f032cebc45d479f5132a99612225d061.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 64727710aec95cc52d00bff9b27807473f0bc70f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[kivy/condiment](https://github.com/kivy/condiment)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
