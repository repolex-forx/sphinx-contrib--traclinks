# Repolex Knowledge Graph of sphinx-contrib/traclinks

RDF knowledge graph data for [sphinx-contrib/traclinks](https://github.com/sphinx-contrib/traclinks), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/traclinks
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 590ef6c1378e512afbfdbd46cce8ebb007382ebc
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 590ef6c1378e512afbfdbd46cce8ebb007382ebc
│           └── chunk-001.nq.gz
├── blob
│   ├── 2d74c58f248790e34e482eb07e20ec6c753c9d2d.nq.gz
│   ├── 43ec418afc530b518826a2e63eca47b4406c1f0d.nq.gz
│   ├── 45dd5f5b51e10661a6b6699e050c4ab23d721804.nq.gz
│   ├── 5709b41bcecfd496f6222964203b8452ecfe9b90.nq.gz
│   ├── 63308a321ba64359837f2a0503949d1a5ef17117.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   └── c5040a39f36bb186b79f5802854babdaa89c15d8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 590ef6c1378e512afbfdbd46cce8ebb007382ebc.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 13 files
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

[sphinx-contrib/traclinks](https://github.com/sphinx-contrib/traclinks)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
