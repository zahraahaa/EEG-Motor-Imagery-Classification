# AI/ML Portfolio Mentorship Plan

*Prepared for Zahra — CS Master's (Computational Neuroscience), targeting Big Tech working-student / internship roles in Germany.*

---

## 1. Assessment of Your Current Situation

You're not actually a "beginner" in the way that term is usually used. You're a beginner *in deep learning*, but you have three things most self-taught beginners don't:

- **A real CS Master's foundation** — algorithms, data structures, software engineering instincts.
- **Mathematical maturity** — you said equations don't scare you. This is the #1 separator between people who copy tutorials and people who actually build things. Lean on this hard.
- **A domain.** Computational Neuroscience is one of the most respected academic neighborhoods of AI. Modern deep learning literally took attention, predictive coding, hierarchical representation, and Hebbian-style updates from neuroscience. Recruiters at DeepMind, Meta FAIR, and Google Brain *notice* this background.

**The honest gap:** you haven't shipped a deep-learning project end-to-end in PyTorch yet. Scikit-learn's `model.fit()` API hides almost everything that matters in DL — the gradient flow, the training loop, the device management, the data pipeline. The mental jump from sklearn to PyTorch is the biggest one you'll make, and it usually takes 2–3 weeks to feel comfortable.

**Time-budget reality:** 10 hours/week × 10 weeks = 100 hours. That's enough for one genuinely strong project, or two medium ones. Don't try to do five. One excellent repo beats five mediocre ones for hiring.

---

## 2. AI/ML Market Reality for Beginners in 2026

A few hard truths so you don't waste effort:

- **LLM-only projects are saturated.** "I fine-tuned Llama on my notes" is now what "I built a Titanic classifier" was in 2019. Don't make that your headline project.
- **PyTorch dominates** in research and increasingly in industry. Your instinct to prioritize it over TensorFlow is correct. The Udemy course is fine background, but PyTorch is what you ship in.
- **Engineering rigor > model complexity.** Recruiters at Big Tech can tell within 30 seconds whether your repo was built by an engineer or by someone running cells. Tests, config files, reproducibility, and clean commits matter more than fancier architectures.
- **For Big Tech in Germany specifically:**
  - Google has Munich (research, MLOps), Berlin, Hamburg offices.
  - Meta has a Berlin office; AI roles are limited but exist.
  - DeepMind is UK-based — being in Germany makes it harder unless you can relocate. Some remote/hybrid roles exist but are scarce.
  - You'll compete with students from TUM, LMU, ETH Zürich, EPFL, RWTH Aachen, and increasingly strong Eastern European programs. Your edge isn't *more* ML knowledge — it's the **neuroscience × ML intersection plus engineering discipline**.
- **Working student (Werkstudent) roles** are realistic targets. They pay well, are 20h/week during semester, and convert to full-time at decent rates if you perform.

What this means for your project choice: **pick something at the neuroscience-AI boundary, ship it like a software engineer would, and write it up like a researcher would.**

---

## 3. Project Ideas Table

Six ideas, ranked from most-recommended to most-ambitious.

### Project 1 — EEG Motor Imagery Classification with Deep Learning
- **Problem:** Classify which mental task (e.g., imagined left-hand vs. right-hand movement) a person is performing from raw EEG signals. This is the core building block of Brain-Computer Interfaces (BCIs).
- **Why it's strong:** Real-world biomedical application, your neuroscience background is directly relevant, well-defined benchmarks exist, runs on CPU/Colab without GPU bills, lets you compare CNNs vs Transformers on the same task.
- **Required skills:** PyTorch (Dataset, DataLoader, training loop), signal processing basics (filtering, epoching), CNN architectures, evaluation (cross-subject, k-fold), MNE-Python for EEG I/O.
- **Datasets:** BCI Competition IV Dataset 2a (gold standard), PhysioNet EEG Motor Movement/Imagery Dataset, OpenBMI.
- **Difficulty:** Beginner-to-intermediate. Excellent starting point.
- **GitHub visibility:** Reproducible training scripts, results table beating a known baseline (EEGNet), confusion matrices, attention/saliency visualizations on EEG channels, clean README with a hero figure.

### Project 2 — fMRI Visual Response Prediction (Algonauts-style)
- **Problem:** Given an image a person looked at, predict their fMRI brain activity. Models that do this well are essentially learning what features the visual cortex computes.
- **Why it's strong:** Directly bridges deep CNN representations and brain activity. This is core DeepMind / Meta FAIR neuroscience-ML territory. Forces you to use pretrained models (ResNet, ViT, CLIP) — practical industry skill.
- **Required skills:** PyTorch, pretrained model feature extraction, regression (ridge, partial least squares), neuroimaging data formats (NIfTI), cross-validation with neuroscience care (e.g., across subjects).
- **Datasets:** Algonauts 2023 Challenge dataset, NSD (Natural Scenes Dataset — bigger, more advanced).
- **Difficulty:** Intermediate. Better as project #2 after EEG.
- **GitHub visibility:** Comparison table of different pretrained encoders, brain region heatmaps, prediction accuracy plots per cortical area.

### Project 3 — Vision Transformer From Scratch + Transfer Learning Study
- **Problem:** Implement a ViT (`patch embedding → transformer encoder → classification head`) from scratch in PyTorch, train on CIFAR-10/100, then study transfer learning behavior.
- **Why it's strong:** Forces you to internalize attention, the modern workhorse. Demonstrates you can read a paper (Dosovitskiy et al. 2020) and implement it. Pure PyTorch — no shortcuts.
- **Required skills:** PyTorch tensor manipulation, einops, attention mechanisms, learning rate schedulers, mixed precision training.
- **Datasets:** CIFAR-10, CIFAR-100, Tiny ImageNet.
- **Difficulty:** Intermediate. Mostly engineering once you understand the math.
- **GitHub visibility:** Side-by-side comparison with `torchvision.models.vit_b_16`, attention map visualizations, ablation tables (patch size, depth, heads).

### Project 4 — Small-Scale Diffusion Model From Scratch (UNet)
- **Problem:** Implement DDPM (Ho et al. 2020) from scratch — UNet, noise scheduler, training loop, sampling — and generate digits/faces.
- **Why it's strong:** Generative modeling is hot, and diffusion is the dominant paradigm. Shows you can implement a non-trivial paper end-to-end.
- **Required skills:** PyTorch, UNet architecture, stochastic processes (you'll be fine with this), time embedding, EMA, mixed precision.
- **Datasets:** MNIST, FashionMNIST, CelebA (64×64).
- **Difficulty:** Intermediate-to-advanced. Training stability is the main pain.
- **GitHub visibility:** Generated sample grids over training steps, FID scores, sampling time comparisons (DDPM vs DDIM).

### Project 5 — Neural Spike Sorting with Self-Supervised Learning
- **Problem:** From multi-electrode neural recordings, identify and cluster spikes belonging to individual neurons. Use self-supervised contrastive learning to learn waveform embeddings.
- **Why it's strong:** Combines neuroscience domain expertise, modern SSL methods (SimCLR/BYOL), and a real bottleneck in systems neuroscience. Few candidates do this — it's a *real* differentiator.
- **Required skills:** PyTorch, signal processing, contrastive losses, clustering (HDBSCAN), evaluation against ground-truth.
- **Datasets:** SpikeForest benchmark, simulated MEArec data, Neuropixels public datasets (Steinmetz et al.).
- **Difficulty:** Advanced. Save for project #2 or #3.
- **GitHub visibility:** Embedding UMAP plots, comparison vs Kilosort, scientific writeup.

### Project 6 — Paper Reproduction: Predictive Coding / Brain-Score
- **Problem:** Pick one paper from the neuro-AI intersection (e.g., Whittington & Bogacz 2017 predictive coding, or Schrimpf et al. Brain-Score) and reproduce its results in clean PyTorch.
- **Why it's strong:** "Can reproduce a paper" is one of the highest-signal capabilities for research-leaning roles, especially DeepMind. Forces close paper reading.
- **Required skills:** Paper comprehension, PyTorch, scientific writing, plotting (matplotlib/seaborn).
- **Datasets:** Whatever the paper uses.
- **Difficulty:** Variable. Pick a paper with code already available so you can verify yourself.
- **GitHub visibility:** Side-by-side figures (theirs vs yours), commentary on discrepancies, your "what I learned" notes.

---

## 4. Best 2 Recommendations for Your Profile

Given your time budget (10 h/week), neuroscience background, and target of Big Tech in Germany:

**Recommendation #1 (Flagship): EEG Motor Imagery Classification**
This is the right starting project for you because:
- It's tractable in 8–10 weeks at 10h/week without becoming a slog.
- It uses PyTorch deeply (your stated goal) without requiring an A100.
- It cleanly leverages your neuroscience background — you can talk about it intelligently in interviews.
- The dataset is small enough to iterate fast, large enough to be non-trivial.
- It has clear, defensible evaluation metrics (accuracy, Cohen's Kappa).
- It naturally extends to professional-tier work (cross-subject generalization, transformers, self-supervised pretraining).

**Recommendation #2 (Follow-up after flagship): fMRI Response Prediction**
Save this for project #2, ~3 months later. Once you have the first repo polished, this one cements you as a "deep learning + neuroscience" candidate and is *exactly* the kind of work DeepMind / Meta FAIR neuro-aligned teams care about.

---

## 5. Selected Flagship Project

**Title:** "Deep Learning for EEG Motor Imagery Classification: CNNs vs Transformers"

**Goal:** Build a reproducible PyTorch pipeline that classifies 4-class motor imagery EEG from BCI Competition IV Dataset 2a, compares an EEGNet-style CNN baseline against a Transformer-based model, and rigorously evaluates cross-subject generalization.

**Why this exact framing works:**
- "CNN vs Transformer comparison" is a *story* — recruiters and interviewers can talk to you about it.
- "Cross-subject generalization" is a real research problem that signals scientific maturity.
- You'll learn both classic and modern architectures.
- You can extend with self-supervised pretraining as a stretch goal.

**Final deliverables:**
- A polished GitHub repo with `pip install`-able training scripts.
- A results table that meets or beats EEGNet's published accuracy.
- A 1-page methods writeup in the README.
- A 5-minute demo notebook for non-technical viewers.

---

## 6. 10-Week Roadmap

Each week assumes ~10 hours. Adjust ±1 week if needed; this is *your* timeline, not a contract.

### Week 1 — PyTorch Fundamentals + EEG Domain Onboarding
- **Learning goals:** Understand tensors, autograd, the canonical training loop, GPU/CPU device handling. Understand what EEG signals are (frequency bands, electrode positions, artifacts).
- **PyTorch concepts:** `torch.Tensor`, `requires_grad`, `.backward()`, `nn.Module`, `optim.SGD`/`Adam`, `to(device)`.
- **ML/DL concepts:** Loss functions, gradient descent, batches vs epochs.
- **Implementation tasks:** Walk through the official PyTorch 60-minute blitz. Re-implement linear regression *without* using `nn.Linear` (raw tensors only), then with `nn.Linear`. Read 1–2 pages on EEG preprocessing from the MNE-Python docs.
- **Experiments:** None yet — just exercises.
- **Deliverables:** GitHub repo initialized, `README.md` with project pitch, `.gitignore`, `requirements.txt`. First commit pushed.

### Week 2 — Data Pipeline
- **Learning goals:** Build a proper PyTorch data pipeline. Understand epoching, channel ordering, train/test splits in time-series.
- **PyTorch concepts:** `Dataset`, `DataLoader`, `collate_fn`, `transforms`, persistent workers.
- **ML/DL concepts:** Why leakage matters in time-series; subject-aware splitting.
- **Implementation tasks:** Download BCI IV 2a dataset, load with MNE, write a `EEGDataset` class that returns `(epoch, label)`. Write tests for shape and label correctness.
- **Experiments:** Sanity-check class balance; visualize average evoked response per class.
- **Deliverables:** `src/data/datasets.py`, `notebooks/01_data_exploration.ipynb`, unit tests in `tests/test_dataset.py`.

### Week 3 — Baseline Model: EEGNet
- **Learning goals:** Read the EEGNet paper (Lawhern et al. 2018). Implement it from the paper, not from someone's copy.
- **PyTorch concepts:** `Conv2d`, `DepthwiseConv2d`, `BatchNorm`, `Dropout`, parameter counting.
- **ML/DL concepts:** Receptive fields, why depthwise convolutions, inductive biases.
- **Implementation tasks:** Implement EEGNet in `src/models/eegnet.py`. Print model summary. Make sure forward pass produces correct output shape.
- **Experiments:** Forward pass on one batch; verify no NaNs.
- **Deliverables:** `src/models/eegnet.py`, a markdown note `docs/eegnet_notes.md` summarizing the paper.

### Week 4 — Training Loop + Logging
- **Learning goals:** Build a production-quality training loop with logging, checkpointing, and early stopping.
- **PyTorch concepts:** `model.train()`/`eval()`, `torch.no_grad()`, learning rate schedulers, `state_dict` save/load.
- **ML/DL concepts:** Train/val/test discipline, when to checkpoint, learning curves.
- **Implementation tasks:** Write `src/training/train.py` with a config-driven main loop. Add Weights & Biases (W&B) or TensorBoard logging. Add early stopping.
- **Experiments:** Train EEGNet on one subject; sanity-check that loss goes down.
- **Deliverables:** `train.py`, `configs/eegnet_baseline.yaml`, W&B dashboard link in README.

### Week 5 — Evaluation Framework + First Real Results
- **Learning goals:** Evaluate like a scientist, not a Kaggler.
- **PyTorch concepts:** Model inference modes, batched evaluation.
- **ML/DL concepts:** Accuracy vs Cohen's Kappa, confusion matrices, within-subject vs across-subject evaluation, statistical significance.
- **Implementation tasks:** Build `src/training/evaluate.py`. Run within-subject 5-fold cross-validation on all 9 subjects.
- **Experiments:** Generate a results table: per-subject accuracy and average. Compare to published EEGNet numbers (~70–76% mean).
- **Deliverables:** Results table committed in `results/`, confusion matrix plots, methodology writeup section.

### Week 6 — Hyperparameter Sweeps + Reproducibility
- **Learning goals:** Run principled sweeps; ensure reproducibility (seeds, deterministic mode).
- **PyTorch concepts:** `torch.manual_seed`, `torch.backends.cudnn.deterministic`, generator seeding in DataLoader.
- **ML/DL concepts:** What hyperparameters actually matter; the curse of overfitting to validation.
- **Implementation tasks:** Run a W&B sweep over learning rate, batch size, dropout. Document findings honestly.
- **Experiments:** 20–30 sweep runs. Pick top config.
- **Deliverables:** `docs/hyperparameter_study.md`, sweep results visualized.

### Week 7 — Transformer Architecture
- **Learning goals:** Implement a Transformer encoder for EEG (e.g., EEG-Conformer or a simpler ViT-style model on EEG patches).
- **PyTorch concepts:** `nn.MultiheadAttention`, positional encoding, layer norm, residual connections.
- **ML/DL concepts:** Self-attention, why transformers can struggle with small datasets, inductive bias trade-offs.
- **Implementation tasks:** Write `src/models/transformer.py`. Read the EEG-Conformer paper (Song et al. 2022) or similar.
- **Experiments:** First training run with transformer; compare against EEGNet baseline.
- **Deliverables:** `transformer.py`, comparison run logged on W&B.

### Week 8 — Cross-Subject Generalization
- **Learning goals:** Run the experiment that tells the actual scientific story.
- **PyTorch concepts:** Custom samplers, leave-one-subject-out (LOSO) splits.
- **ML/DL concepts:** Why models generalize poorly across subjects in EEG (inter-subject variability), the "calibration problem" in BCIs.
- **Implementation tasks:** Implement LOSO evaluation. Run on both EEGNet and Transformer.
- **Experiments:** 9 LOSO runs per model. Build a results table comparing within-subject vs cross-subject performance.
- **Deliverables:** Cross-subject results in `results/`, plot showing the performance drop.

### Week 9 — Analysis, Visualization, Writeup
- **Learning goals:** Tell the story clearly. This is where most candidates fail.
- **PyTorch concepts:** Hook-based intermediate activation extraction, integrated gradients (optional).
- **ML/DL concepts:** Model interpretability, what attention maps tell you (and what they don't).
- **Implementation tasks:** Generate attention-map visualizations over EEG channels and time. Produce a final results figure for the README.
- **Experiments:** Optional ablation — how does performance scale with training data?
- **Deliverables:** `notebooks/03_final_analysis.ipynb`, hero figure for README, results section drafted.

### Week 10 — Polish, Demo, Documentation
- **Learning goals:** Make the repo *look* like something a senior engineer would write.
- **PyTorch concepts:** `torch.jit.script` / `torch.onnx.export` if you want to demo deployment.
- **ML/DL concepts:** Model cards (Google's framework for documenting model limitations).
- **Implementation tasks:** Polish README, add badges, add a Colab notebook demo (so anyone can re-run results in 1 click), write a `MODEL_CARD.md`, tag a `v1.0.0` release.
- **Experiments:** None — finalize.
- **Deliverables:** Polished README, tagged release, optional LinkedIn post draft.

### Stretch Goals (only if you finish early)
- Self-supervised pretraining (BYOL / Barlow Twins) on unlabeled EEG.
- Comparison to a Riemannian-geometry baseline (classic but strong on EEG).
- A simple Streamlit/Gradio demo where someone can upload EEG and get a prediction.

---

## 7. Recommended Datasets

In order of recommendation:

- **BCI Competition IV Dataset 2a** — the canonical benchmark. 9 subjects, 4 classes, 22 channels, ~5–6 GB. Use this as your primary dataset because results are comparable to literature. Available via [BNCI Horizon 2020](http://bnci-horizon-2020.eu/database/data-sets) and easily loadable with `moabb` (an open-source Python library that already wraps it).
- **PhysioNet EEG Motor Movement/Imagery Dataset** — 109 subjects, simpler 64-channel setup. Good for cross-subject experiments because of the larger N.
- **OpenBMI Dataset (Lee et al. 2019)** — 54 subjects, modern recording. Excellent stretch dataset.
- **MOABB** — not a dataset but a Python library that gives you uniform access to ~20 EEG datasets. **Strongly recommended** — using it shows you know the ecosystem.

A practical detail: use `moabb` to load BCI IV 2a in 5 lines, but then write your *own* `Dataset` class around it. Don't hide the data work — show it.

---

## 8. Suggested GitHub Repository Structure

```
eeg-motor-imagery-pytorch/
├── README.md                    # the front door — most important file
├── LICENSE                      # MIT is fine for portfolio repos
├── pyproject.toml               # OR requirements.txt — pinned versions
├── .gitignore                   # ignore data/, *.pth, __pycache__, .venv/
├── .github/
│   └── workflows/
│       └── tests.yml            # GitHub Actions running pytest on push
├── configs/                     # YAML configs — no hardcoded hyperparams
│   ├── eegnet_baseline.yaml
│   └── transformer.yaml
├── src/
│   ├── data/
│   │   ├── datasets.py
│   │   └── preprocessing.py
│   ├── models/
│   │   ├── eegnet.py
│   │   └── transformer.py
│   ├── training/
│   │   ├── train.py
│   │   └── evaluate.py
│   └── utils/
│       ├── logging.py
│       └── seed.py
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_baseline_results.ipynb
│   └── 03_final_analysis.ipynb
├── tests/                       # even a few tests >> none
│   ├── test_dataset.py
│   └── test_models.py
├── scripts/
│   ├── download_data.sh
│   └── run_loso.sh
├── results/                     # tables + figures generated by your code
│   ├── tables/
│   └── figures/
├── docs/
│   ├── eegnet_notes.md
│   └── hyperparameter_study.md
└── MODEL_CARD.md
```

**On your Jupyter question — short answer: yes, you can absolutely push `.ipynb` files to GitHub, and they render beautifully there.** The professional pattern is:

- **Notebooks** for exploration, visualization, and final analysis (anything where the *output* is the point).
- **Plain `.py` files** in `src/` for anything that is reused: models, training loops, datasets, evaluation.

Why this matters: if your training logic lives in a notebook, you can't run it from the command line, can't include it in CI, can't reuse it. Recruiters strongly prefer the split. Workflow: prototype in a notebook, refactor into `.py` files once the idea works.

A couple of practical tips for committing notebooks cleanly:
- Always restart the kernel and clear outputs before final commits (`Kernel → Restart & Clear Output`) — large outputs bloat the repo.
- Install `nbstripout` (`pip install nbstripout && nbstripout --install`) — it auto-cleans notebook outputs from git.
- Or use [Jupytext](https://github.com/mwouts/jupytext) to keep notebooks paired with `.py` files automatically.

---

## 9. README Outline

A README that gets you hired follows roughly this skeleton:

1. **Title + one-line description.** "Deep Learning for EEG Motor Imagery Classification — a PyTorch comparison of CNN and Transformer architectures with cross-subject evaluation."
2. **Badges.** Python version, PyTorch version, license, optional: tests passing, code coverage.
3. **Hero figure.** One clean, well-captioned figure that summarizes the project — e.g., the cross-subject results bar chart, or an attention-map visualization.
4. **TL;DR results table.** Your method, baseline, dataset, metric. Three rows max.
5. **Problem statement.** 2–3 paragraphs. What is motor imagery? Why is it hard? Why does it matter (BCI, prosthetics, accessibility)?
6. **Method.** What architectures, what training regime, what evaluation protocol. Cite the relevant papers.
7. **Installation.** `pip install -e .` should be enough.
8. **Usage.** Exact commands to reproduce the headline numbers: `python -m src.training.train --config configs/eegnet_baseline.yaml`.
9. **Project structure.** Tree view with one-line descriptions.
10. **Results.** Full results table, confusion matrices, ablations.
11. **What I learned.** Optional but very effective — 3–4 bullet points of honest insights.
12. **Limitations & future work.** Shows scientific maturity.
13. **Citations.** Papers you used, datasets, libraries.
14. **Contact.** Email, LinkedIn.

Two things that single-handedly elevate READMEs above 80% of beginner projects:
- A **reproducible** install + run command that actually works on a clean machine.
- A **proper figure** in the first scroll, with axis labels and a caption.

---

## 10. Resume and LinkedIn Positioning

### Resume bullets
Write 2–3 bullets per project. Use the **Action — Tools — Result** pattern. Numbers are non-negotiable.

Examples (placeholders for your actual numbers):
- "Designed and implemented a PyTorch pipeline for EEG-based motor imagery classification on BCI Competition IV-2a, achieving **78.4% mean accuracy (Cohen's κ = 0.71)** across 9 subjects — matching the published EEGNet baseline and improving cross-subject generalization by **+4.2 pp** with a Transformer-based architecture."
- "Built reproducible experiment framework with YAML-configured training, W&B experiment tracking, automated leave-one-subject-out cross-validation, and CI tests; documented in a paper-style README."
- "Compared CNN, attention-based, and self-supervised pretraining approaches; analyzed inter-subject variability as a generalization bottleneck."

Avoid: "Used PyTorch to make a model." That's invisible.

### LinkedIn
Three places to surface this:
1. **Featured section:** pin the GitHub repo with a custom thumbnail (your hero figure).
2. **Projects section:** title, dates, description, link, skills tagged.
3. **A post when you ship v1.0.** Format: a short story (problem → what you tried → what worked → 1–2 figures → link). Posts with figures get ~5× more engagement than pure text. Tag relevant authors (e.g., the EEGNet authors are active on Twitter/LinkedIn).

Add to your headline once you've shipped: "MSc Computational Neuroscience · Deep Learning for Neural Signals (PyTorch)".

### Internship/Job Applications
In cover letters and "Why this team" essays:
- Connect the neuroscience angle to the team's work. For DeepMind: cite their neuroscience-aligned papers. For Google Health / Brain: cite biosignal work. For Meta FAIR: their world-model and self-supervised work.
- Reference *one* specific paper from the team and how your project relates.
- Don't oversell. Say "I'm an early-stage practitioner who has built X end-to-end and want to learn Y here." Honesty signals maturity.

---

## 11. Common Mistakes Beginners Make

In rough order of how often they cost interviews:

1. **Single 47-cell notebook is the entire project.** No reusable code, no reproducibility. Always have a `src/` directory.
2. **"It works on my machine."** Hardcoded paths, no requirements file, no version pinning. Always test on a clean venv or Colab before shipping.
3. **Reporting only training accuracy.** A model that memorizes the training set will get 100%. Always report validation/test, and ideally with confidence intervals or multiple seeds.
4. **One giant "Initial commit."** Your commit history is read like a CV. Small, frequent, well-messaged commits are evidence of how you work.
5. **No README, or a 5-line README.** This is the single biggest determinant of whether anyone reads further.
6. **Copy-pasted code without understanding.** Interviewers ask "why did you choose this loss?" If you can't answer, the project actively hurts you.
7. **Trying transformers before getting MLP/CNN baselines right.** Always build the simplest baseline first.
8. **Ignoring data preprocessing.** In EEG especially, preprocessing matters more than model choice. Show that you know this.
9. **No tests, no CI.** Even one trivial test that the model returns the right output shape signals engineering taste.
10. **Overclaiming.** "State-of-the-art" when it isn't. "Novel" when it isn't. Recruiters can tell.
11. **Skipping the writeup.** A repo with no narrative is a repo no one understands.

---

## 12. Your First Concrete Task (This Week)

Do exactly this, in order:

1. **Create the GitHub repo** named `eeg-motor-imagery-pytorch`. Add a one-line description and a README with just the project title and a "Status: Week 1 of 10" line. Push.
2. **Set up a clean Python environment.** Either `conda create -n eeg python=3.11` or `python -m venv .venv`. Add `requirements.txt` with `torch`, `numpy`, `mne`, `moabb`, `scikit-learn`. Commit.
3. **Add `.gitignore`** — copy GitHub's Python template. Commit.
4. **Run the PyTorch 60-minute blitz.** Do it in a notebook in `notebooks/00_pytorch_blitz.ipynb`. Commit when done.
5. **The actual brain-stretch task:** in a new notebook, *without using `nn.Linear`*, implement linear regression on a small synthetic dataset using raw PyTorch tensors. Initialize weights manually, write the forward pass as `y = X @ w + b`, compute MSE, call `.backward()`, update with `w -= lr * w.grad`, zero grads. Train for 1000 steps. Plot loss curve. Commit.
6. **Reflection.** Write a 5-line note `notes/week1.md` answering: "What does `.backward()` actually do? What does `optimizer.zero_grad()` prevent?" Commit.

If you finish step 5 understanding *why* you call `zero_grad()`, you've crossed the biggest conceptual barrier in PyTorch.

---

## 13. Five Follow-Up Questions to Personalize Further

These will help me sharpen the plan after week 2 or 3:

1. **Research vs Applied:** Do you lean toward research-style roles (papers, NeurIPS/ICLR-flavored teams like DeepMind, Meta FAIR) or applied ML engineering (production systems, ML infra, MLOps at Google/Meta)? The roadmap shifts — research roles weight paper reproduction higher; applied roles weight clean engineering and deployment higher.

2. **Specific teams:** Are there 2–3 specific teams you fantasize about working on (e.g., Google DeepMind's neuroscience team, Meta AI Research SSL group, Google Health, Brain Team Munich)? Knowing this lets me align project framing to what they cite and publish.

3. **Relocation flexibility:** Are you strictly Germany, open to EU-wide (London, Paris, Zurich), or fully flexible globally? DeepMind in particular is London-based; if relocation isn't possible, we should de-emphasize that angle and lean more toward Google Munich and Meta Berlin.

4. **Neuroscience commitment:** Is neuro-AI your long-term career identity, or are you comfortable taking a non-neuroscience Big Tech role to break into the industry first? If it's identity, we lean fully into the brain-signal angle for both projects. If it's pragmatic, we balance one neuro project with one "pure ML" project (e.g., the ViT) to broaden your fit.

5. **Timeline:** When do you need to start applying? Summer 2026 working-student? Fall 2026? Full-time after graduation? Working backwards from your earliest application deadline determines whether the flagship needs to be shipped in 8 weeks or 12, and whether we run a second project in parallel or sequentially.

---

*One last thing: you said you're a beginner. I want you to take that label off this document the moment you commit your first working `train.py`. You're a CS Master's student with mathematical fluency and a real domain. You're not a beginner. You're early.*
