# reel-releases

This repository is the **public release catalog** for Reel runtime stacks.

It contains **immutable, digest-pinned** container image sets for each release and environment.

## What is stored here

- `releases/<env>/<release_id>/images.env`
  - Environment variables mapping service names to Docker image digests:
    - `SERVICE_IMAGE=reelcommerce/service@sha256:...`
- `releases/<env>/<release_id>/release.json`
  - Minimal metadata/provenance (no secrets)
- `releases/<env>/<release_id>/notes.md`
  - Human-readable notes (optional)

### Environment pointers

- `releases/envs/<env>/latest.txt` — “current” release for that env
- `releases/envs/<env>/stable.txt` — last known good rollback target

## Security

This repository is **public**. It must never contain secrets.

Allowed:
- image digests
- commit SHAs
- timestamps
- non-sensitive notes

Not allowed:
- API keys / tokens
- credentials
- private URLs
- site-specific secrets

## Release ID format

Release IDs use UTC timestamps for uniqueness and ordering:

- `YYYY-MM-DDThhmmZ` (e.g. `2025-12-19T1815Z`)
- Optional hotfix suffix: `-hfN` (e.g. `2025-12-20T1030Z-hf1`)
