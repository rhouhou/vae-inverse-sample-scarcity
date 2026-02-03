# VAE Inverse Sample Scarcity
**Stability & uncertainty of amortized inverse reconstruction under data scarcity (biomedical imaging).**

This repository studies how training sample size affects the **quality**, **stability**, and **uncertainty** of **amortized inverse solvers** (variational autoencoders) for ill-posed reconstruction problems. We treat reconstruction as an inverse problem with a forward operator:
\[
y = \mathcal{F}(x) + \varepsilon
\]
and learn a fast (amortized) inverse mapping \( y \mapsto \hat{x} \), then evaluate its **sensitivity to perturbations**, **uncertainty calibration**, and **reliability** as a function of dataset size.

## Motivation
Deep amortized inverse models are widely used because they enable fast inference, but they can become **unstable** and **overconfident** under limited training data—particularly for ill-posed problems. This project provides a controlled study of:
- **Data scarcity** (sample size scaling)
- **Stability** (sensitivity of reconstructions to small measurement perturbations)
- **Uncertainty** (reconstruction variance via posterior sampling / ensembles)
- Optional: **operator consistency** via physics-constrained losses

## Research pillars
This project aligns with:
1. **Data-efficient inverse modeling**: sample-size scaling laws for reconstruction.
2. **Physics-constrained inverse modeling**: forward-operator consistency during training (optional).
3. **Stability, uncertainty & reliability**: stability metrics and uncertainty quantification for inverse reconstructions.

---

## Repository structure
vae-inverse-sample-scarcity/
├─ README.md
├─ requirements.txt
├─ .gitignore
├─ configs/
├─ data/ # not committed
├─ src/
├─ scripts/
├─ results/ # generated outputs
└─ paper/ # manuscript + bib


### Key components
- `src/operators.py`: forward operators (blur, downsampling, noise models)
- `src/models/vae.py`: VAE encoder/decoder (amortized inverse solver)
- `src/eval_stability.py`: perturbation-based stability metrics
- `src/eval_uq.py`: uncertainty estimation (posterior sampling / ensembles)
- `scripts/run_sweep.py`: sample size sweep experiments and logging
- `results/metrics/`: exported metrics files used for plots
- `results/figures/`: paper-ready figures

---

## Setup

### 1) Create environment
Using `venv`:
```bash
python -m venv .venv
source .venv/bin/activate          # macOS/Linux
# .venv\Scripts\activate           # Windows
pip install -r requirements.txt