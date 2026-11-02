# Bruhn C11.34 — Diagonal Semi-Tension Field Design

An interactive, single-file web calculator for the **diagonal semi-tension field
(incomplete / semi-tension field) design of a curved fuselage skin panel**, following
Art. **C11.34** of E. F. Bruhn, *Analysis & Design of Flight Vehicle Structures*.

**Live tool:** https://volocchio.github.io/bruhn-c11-34-diagonal-tension/

## What it does

Given the applied loads and panel geometry, it computes the full C11.34 procedure live:

- Critical **shear** and **compression** buckling stresses of the curved panel
  (digitized Bruhn Fig. C9.4 / C9.1 coefficient charts)
- Combined-load buckling reduction ratio **Rc**
- Applied shear flows (bending + torsion) and nominal shear stress **fs**
- **Diagonal-tension factor k** — `k = tanh[(0.5 + 300·t·d/Rh)·log₁₀(fs/fscr)]`
  (Bruhn Fig. C11.19 / NACA TN 2661 Fig. 13)
- Iterative solution of the **tension-field angle α** from the web-strain relation
  `εE/fs = 2k/sin2α + sin2α(1−k)(1+ν)` (Fig. C11.36 / NACA TN 2661 Fig. 31)
- Resulting **stringer** and **ring/frame** stresses

It also shows a live tension-field panel schematic (with complementary shear flow on all
four edges and the solved angle α), the Fig. C11.19 `k` curve with the operating point,
and a full step-by-step calculation table.

## Verification

The engine is validated against the worked example in Bruhn C11.34 (as reproduced in a
1998 reference spreadsheet). With the example inputs it matches to **< 0.2 %**:

| Quantity | Reference | This tool |
|---|---|---|
| Fs,cr | 2989.3 psi | 2989.3 |
| Fc,cr | 2808.1 psi | 2808.1 |
| Rc | 0.2412 | 0.2412 |
| fs | 5250.3 psi | 5250.3 |
| k | 0.7544 | 0.7544 |
| α | 41.64° | 41.64° |
| F_str | 24,793 psi | 24,793 |
| F_ring | 6,528 psi | 6,528 |

> **Note on section inertia:** the reference example uses two different moment-of-inertia
> values — `I = 2382 in⁴` for bending stress and `I = 3257 in⁴` (from the section analysis)
> for shear flow. Both are exposed as editable inputs. See the in-app notes.

## Usage

Just open `index.html` in any modern browser — no build, no dependencies, no network.
Edit any input and all results, the diagram, and the chart update instantly.
"**Load Bruhn example**" resets to the textbook inputs; "**Print / PDF**" exports a clean report.

## References

- E. F. Bruhn, *Analysis & Design of Flight Vehicle Structures*, Art. C11.34, Figs. C9.1, C9.4, C11.19, C11.36.
- P. Kuhn, J. P. Peterson, L. R. Levin, *A Summary of Diagonal Tension, Part I: Methods of Analysis*, NACA TN 2661.

## Disclaimer

Engineering aid for preliminary analysis only. Verify against the source text and your own
checks before use in any certification or production context.

## License

MIT — see [LICENSE](LICENSE).
