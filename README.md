<!-- solve-problem:28c0ff68-9ada-452d-a877-fb391673bfc0 -->
# Gilbert–Pollak conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/28c0ff68-9ada-452d-a877-fb391673bfc0).

## What is the problem?

Given a finite set P of n points in the Euclidean plane, let L(MST(P)) be the length of a minimum spanning tree on P (edges are straight segments between points of P), and let SMT(P) be the length of a Steiner minimum tree: the shortest network connecting P, allowing extra vertices (Steiner points) placed anywhere in the plane. The **Steiner ratio** of the Euclidean plane is

ρ = inf over all finite P of L(SMT(P)) / L(MST(P)).

The **Gilbert–Pollak conjecture (1968)** asserts ρ = 2/√3 ≈ 0.8660. The bound 2/√3 is achieved (approached arbitrarily closely) by the three vertices of an equilateral triangle of side 1: its SMT is the classic 3-terminal Steiner tree of length √3, while its MST has length 2. So the conjecture reduces to proving: for every finite point set P in the plane, L(SMT(P)) ≥ (2/√3)·L(MST(P)), i.e., L(MST(P))/L(SMT(P)) ≤ √3/2... equivalently L(SMT(P)) ≥ (2/√3)L(MST(P)). The conjecture extends to the conjecture that the Steiner ratio of d-dimensional Euclidean space is attained by the regular simplex (value √(2d/(2d−... )); specifically conjectured ρ_d = √((2d)/(3d−1))? — the planar case is the flagship; higher-dimensional formulas should be verified before use.

## Why does it matters?

The Steiner ratio is exactly the worst-case approximation guarantee of the minimum spanning tree as a polynomial-time heuristic for the NP-hard Steiner tree problem in the plane; resolving the conjecture certifies the MST's 2/√3 ≈ 0.866 approximation factor as tight. It also calibrates all plane Steiner-tree approximation algorithms and matters in VLSI routing and network design, where Steiner trees model physical interconnect. Finally, the saga of the false 1990 "proof" is a canonical cautionary tale in computer-assisted and case-checking proofs.

## What's already known?

- Gilbert & Pollak (1968) posed the conjecture and proved it for point sets with ≤ 3 points and for points on a circle (verify the circle case).
- Du, Hwang, and Weng (1987) proved it for point sets on the vertices of a lattice / cocircular configurations (verify scope).
- **Du and Hwang claimed a full proof in 1990** ("A proof of the Gilbert–Pollak conjecture on the Steiner ratio", Algorithmica 7:3–21). The proof reduces the problem to a finite-dimensional minimization over the topology/geometry of "Steiner structures" and argues the minimum ratio is attained by an equilateral triangle. **The consensus today is that this proof is incorrect/incomplete** — a gap concerns whether the parametrized family of trees considered actually covers all configurations (issues around the differentiability/continuity of the length function in the parametrization used). Hence the problem is still listed as open.
- The best general lower bound: it is known that ρ ≥ some constant > 0.8 (e.g., results of Du–Hwang's framework give ρ ≥ 2/√3 under extra hypotheses; unconditionally ρ ≥ √3/2? — no: known unconditional bounds include ρ ≥ 0.7430…? verify). Do not cite a specific unconditional bound without checking (Graham–Hwang-type bounds and later improvements exist; confirm numbers).
- The MST upper bound ρ ≤ 2/√3 is trivial via the equilateral triangle. Generalizations to other norms (Gilbert shapes, λ-geometry) and higher dimensions are studied, largely open.

## What would count as solving it?

A rigorous proof that for every finite P ⊂ ℝ², L(SMT(P)) ≥ (2/√3)·L(MST(P)), with equality only for degenerate limits of equilateral triangles (equality is not attained by finite sets beyond n=3?). Referee criteria:
1. A complete, checkable proof (possibly computer-assisted, but with the computation and its soundness documented).
2. Alternatively, a disproof: a point set with ratio < 2/√3 (would be sensational; extensive computational searches have found none).
3. Partial wins: proof for all points in convex position; proof for fixed n; a correct repair of the Du–Hwang gap.

## How to start

1. Read Du & Hwang (1990, Algorithmica 7) carefully, then Ivanov's critique — A. O. Ivanov and A. A. Tuzhilin wrote papers/books (e.g., "The Steiner ratio Gilbert–Pollak conjecture is still open" (verify exact title), and the book *Minimal Networks: The Steiner Problem and Its Generalizations*) identifying the gap; understanding exactly where the argument fails is prerequisite.
2. Study the reduction to "Steiner structures": the length function ℓ(x₁,…,x_n) over a fixed topology with terminals moving, and the claim that a ratio-minimizing configuration can be assumed to be a locally minimal Steiner tree with all Steiner points of degree 3 at 120°.
3. Natural approaches: (a) fix the gap with a better parametrization/smoothing argument; (b) variational/compactness argument showing the infimum is attained at a "simple" configuration (few terminals), reducing to a finite case check; (c) a clean induction on n using Melzak-style structure of full Steiner trees.
4. Main obstacle: the ratio involves two competing optimization problems (SMT over Steiner points, MST over spanning trees); joint compactness arguments are delicate because minimizing sequences can degenerate (terminals colliding).

## Key references

- E. N. Gilbert, H. O. Pollak, "Steiner minimal trees," SIAM J. Appl. Math. 16 (1968), 1–29. Introduces the Steiner ratio, proves the conjecture for small cases, poses it in general. https://doi.org/10.1137/0116001
- D.-Z. Du, F. K. Hwang, "A proof of the Gilbert–Pollak conjecture on the Steiner ratio," Algorithmica 7 (1992/1990), 3–21. The claimed full proof now considered flawed. https://doi.org/10.1007/BF01758849 (verify identifier)
- A. O. Ivanov, A. A. Tuzhilin, "The Steiner ratio Gilbert–Pollak conjecture is still open" (Clarification statement; Algorithmica ~2002? verify). Documents the gap in the Du–Hwang proof.
- A. O. Ivanov, A. A. Tuzhilin, *Minimal Networks: The Steiner Problem and Its Generalizations*, World Scientific, 1994. Comprehensive geometric treatment of Steiner trees and the ratio problem.
- D.-Z. Du, F. K. Hwang, J. F. Weng, "A new lower bound for the Steiner ratio" / work on cocircular point sets (verify). Establishes the conjecture for special configurations.

## Warnings

- **Do not build on the Du–Hwang 1990 proof without reading the refutations.** Many published works implicitly assume it. The gap concerns the continuity/differentiability of the length of Steiner trees as a function of terminal positions in their minimax parametrization.
- The Wikipedia "unsolved" status is correct as of the census date; be skeptical of any source claiming it closed.
- The Steiner ratio is sometimes defined as MST/SMT (√3/2 ≈ 0.866) or SMT/MST (2/√3); check conventions in every paper you read.
- Minimizing configurations need not exist (infimum approached by degenerating families), so "attained by the equilateral triangle" must be stated carefully.
- Higher-dimensional and normed-space analogues have different conjectured constants; don't conflate them with the planar statement.

---
*`ALGO-000222` · unverified*

## Acceptance guidance

A rigorous proof that for every finite P ⊂ ℝ², L(SMT(P)) ≥ (2/√3)·L(MST(P)), with equality only for degenerate limits of equilateral triangles (equality is not attained by finite sets beyond n=3?). Referee criteria:
1. A complete, checkable proof (possibly computer-assisted, but with the computation and its soundness documented).
2. Alternatively, a disproof: a point set with ratio < 2/√3 (would be sensational; extensive computational searches have found none).
3. Partial wins: proof for all points in convex position; proof for fixed n; a correct repair of the Du–Hwang gap.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/28c0ff68-9ada-452d-a877-fb391673bfc0?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000222.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000222)
