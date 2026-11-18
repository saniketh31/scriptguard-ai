# ScriptGuard AI

A deterministic screenplay quality-control prototype for identifying potential character-name, alias and speaker-label inconsistencies across multi-episode scripts.

## What it does

ScriptGuard reads a ZIP archive or folder of screenplay text files, parses episodes and extracts speaker labels, names in dialogue/action text and scene-heading locations. It generates candidate inconsistencies, applies contextual checks, verifies quoted evidence against the source, and writes review-oriented reports.

It does not edit scripts or make final identity decisions. Uncertain cases are left for human review.

## Implementation

- Ruby standard library; no third-party runtime dependencies.
- Safe in-memory ZIP ingestion.
- Deterministic candidate and context rules.
- Line-referenced evidence checked against original source text.
- Markdown, CSV and JSON outputs.
- No LLM or external API calls in this build.

## Quick start

```sh
ruby -v
bin/scriptguard --help
rake test
```

To scan a ZIP archive:

```sh
bin/scriptguard scan path/to/episodes.zip --out runs/pack --expect 1-50
```

To analyse an existing parsed run:

```sh
bin/scriptguard detect --run runs/pack
```

See `README.md` inside the `ScriptGuard_AI/` directory for full usage, supported input format, output descriptions, and limitations.

## Tests and examples

The repository includes invented synthetic screenplay fixtures and example outputs. The public archive intentionally excludes confidential real-screenplay text, private research files and real-dataset output files.

## Scope and limitations

This is an MVP supporting one screenplay text layout. It flags potential name and speaker-label drift; it does not resolve plot contradictions, relationships, timelines, props, appearance or voice identity. Detection metrics were exploratory on the same 50-episode show used during rule development and should not be interpreted as an unbiased benchmark. Run against a second show and have an editor label findings before making accuracy claims.

## Privacy

Do not commit source screenplays, raw run outputs, confidential research, submission documents, credentials or API keys to this public repository.
