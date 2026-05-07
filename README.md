# Foresight Proof Ledger

This repository is the public external anchor surface for Foresight's prediction ledger.

Foresight seals predictions into an internal hash-chained ledger before outcomes are known. Periodically, the current ledger height and chain root are published here. The public GitHub commit timestamp gives an external reference point: this exact ledger root existed no later than the commit time.

## Current Anchor

- Ledger height: `639`
- Chain root: `72022dfc2bdfcbf5907c8d17f78e02cdef1bb0cd5081760cc9a8c86146c214d0`
- Anchor file: [`anchors/639.json`](anchors/639.json)
- First anchor commit: [`bbc292147ad87670704a0cda4224ddff6f8d19fb`](https://github.com/superelan/foresight-proof/commit/bbc292147ad87670704a0cda4224ddff6f8d19fb)
- Ledger format version: `2`

## What This Proves

This repository does not claim that every Foresight prediction was correct. It proves that a specific ledger root was published to an external system at a public timestamp. If the underlying ledger is later changed, the recomputed root will no longer match this published root.

In plain terms: it makes prediction history tamper-evident.

## Verification Model

1. Recompute the Foresight ledger chain root from the local ledger rows.
2. Compare the recomputed root with the root in the corresponding `anchors/<height>.json` file.
3. Confirm the GitHub commit timestamp for that anchor file.
4. Confirm future anchors continue the same height/root publication trail.

## Files

- `anchors/<height>.json`: immutable anchor payload for a specific ledger height.
- `latest.json`: pointer to the latest known public anchor.

## Anchor Payload Shape

```json
{
  "chain_root": "sha256 root",
  "height": 639,
  "ledger_format_version": 2,
  "ts": "UTC timestamp from the Foresight anchor cycle"
}
```

## Public-Claim Discipline

Foresight can say the ledger is externally anchored only for roots that have a successful public receipt here. Accuracy, calibration, or baseline-edge claims require separate outcome sufficiency and should not be inferred from this repository alone.
