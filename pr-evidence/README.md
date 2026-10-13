# Captured real-data verification output

Captured 2026-10-13 on Windows x64, Python 3.14.6, torch 2.14.1+cu130,
zarr 3.4.1, RTX 5060. Base source: 4eecd08fd91d1afa2beedc0d2edc3b09d2d79bda.
Absolute personal workspace prefixes have been replaced with `<workspace>`;
other output is preserved. These are text transcripts, not terminal screenshots.

- `zero-workers`: actual PHerc0139 w035 hybrid 3D-to-2D training. Before:
  fresh discovery with workers=0 fails. After: workers=0 discovers 219 patches,
  completes 20 optimizer steps and saves a checkpoint. Smoke proof only, no
  held-out detector-quality claim. Independent publication-branch rerun also
  completed fresh discovery and 4 steps.
- `cpu-preview`: real published PHerc0139 umbilicus and unmocked
  `SpiralAndTransform`/`save_combined_preview` on CPU with CUDA available.
  The initial captured failure used 100 z slices; captured success used 260.
  These logs are not a same-settings quantitative comparison. The checked-in
  consumer regression uses z=3100..3360 and writes real TIFXYZ; the eight full
  publication-branch test modules passed (75 tests, 9 subtests).
  `UNEXPECTED SUCCESS` is the original diagnostic script's success label,
  not a failure. The model is initialized, not a fitted scroll reconstruction.
- `windows-cache`: same PHerc0139 w035 crop Z0:28,Y2176:2560,X2176:2432,
  4 spawned workers, 6 reads each, fresh shared cache per batch. Before is the
  isolated original module and fails in batch 2. After: 3/3 batches pass, all
  bytes hash-match uncached input. A second publication-branch run passed 3/3.

The three PRs are drafts: AI assistance is disclosed, the human attestation
is unchecked, and human-written motivation/review plus required terminal
screenshots remain necessary before marking ready under upstream policy.
