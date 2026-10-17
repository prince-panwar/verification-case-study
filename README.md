# What Each Verification Method Catches: A Case Study of a Uniswap v4 Token Launchpad

**Prince Panwar** · Independent technical report · October 2026

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23432763.svg)](https://doi.org/10.5281/zenodo.23432763)

**[Read the report (PDF)](./Panwar_2026_Verification_Methods_Case_Study.pdf)**

## Abstract

Smart contracts are usually checked with several kinds of verification at once: unit tests, fuzzing, symbolic execution, static analysis and manual review. Little is known about which of these methods actually finds the defects in a real system, and why the others miss them. This report studies that question on one production system: a token launchpad of about 3,200 lines of Solidity in eight contracts and two libraries at the reviewed version. It sells new tokens along a bonding curve and then moves their liquidity into a Uniswap v4 pool. I designed, implemented and verified the contracts between July and September 2026. Verification used 298 unit tests, 34 stateful fuzz and invariant tests, 6 symbolic proofs (Halmos), two analysers (Slither and Mythril), fork tests against live Uniswap v4 deployments on three chains, and a written internal security review.

From the project's records I traced 22 defects to the method that first exposed each one, and recorded which methods had missed it. The two automated analysers detected none of the defects. The two most severe ones, a liquidity calculation that would have stopped every launch on one chain from graduating and a 13.33% price drop at graduation, were found by fork tests run at each chain's real parameters and by end-to-end price measurement. Manual review found 7 of the 22, including all five medium-severity design and logic defects. I also report three ways verification evidence silently stopped meaning anything: an analyser that only ever examined an inert contract, a test whose expected values came from the same constants as the system it tested, and proofs that timed out but were described as proven. The report closes with practices that prevent these failures.

**Keywords:** smart contract verification, fuzzing, symbolic execution, static analysis, decentralised finance, Uniswap v4, empirical case study

## Status

This is an independent technical report. It has not been peer reviewed.

## Citation

```bibtex
@techreport{panwar2026verification,
  author      = {Panwar, Prince},
  title       = {What Each Verification Method Catches: A Case Study of a Uniswap v4 Token Launchpad},
  institution = {Independent},
  type        = {Technical report},
  year        = {2026},
  month       = oct,
  doi         = {10.5281/zenodo.23432763},
  url         = {https://doi.org/10.5281/zenodo.23432763}
}
```

## License

The report is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
