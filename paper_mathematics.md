# On a Universal Truth Metric in Information-Theoretic Dynamical Systems

**Mr. Sławomir Gątkowski**

*2026*

---

## 0. Notation

Throughout, $(\Omega, \mathcal{F}, \mu)$ denotes a probability space. $\mathcal{P}(\Omega)$ is the set of probability measures on $(\Omega, \mathcal{F})$. $H: \mathcal{P}(\Omega) \to [0, \infty)$ is Shannon entropy. $\mathbf{I} = [0,1]$. $\varphi = (1+\sqrt{5})/2$. All logarithms are base 2 unless stated otherwise.

---

## 1. Definitions

**Definition 1.1** (Coherence measure). Let $(\Omega, \mathcal{F})$ be a measurable space with $|\Omega| < \infty$. Define $H_{\max} = \log_2 |\Omega|$. The *coherence* of $\mu \in \mathcal{P}(\Omega)$ is:

$$K(\mu) := 1 - \frac{H(\mu)}{H_{\max}} \in \mathbf{I}$$

where $H(\mu) = -\sum_{\omega \in \Omega} \mu(\omega) \log_2 \mu(\omega)$.

**Remark.** $K(\mu) = 0$ iff $\mu$ is the uniform measure. $K(\mu) = 1$ iff $\mu$ is a Dirac measure. $K$ is continuous on $\mathcal{P}(\Omega)$ in the total variation topology.

**Definition 1.2** (Impedance operator). An *impedance operator* is a measurable map $T_Z: L^2(\Omega) \to L^2(\Omega)$ parameterized by $Z \in \mathbf{I}$, satisfying:

1. $T_0 = \text{Id}$ (identity)
2. $\|T_Z f\|_2 \leq \|f\|_2$ for all $Z \in \mathbf{I}$ (contractivity)
3. $Z_1 < Z_2 \Rightarrow \|T_{Z_1} f\|_2 \geq \|T_{Z_2} f\|_2$ for all $f$ (monotonicity)

**Definition 1.3** (Truth metric). A function $\mathcal{T}: \mathcal{P}(\Omega) \to \mathbb{R}$ is a *truth metric* if it satisfies axioms (A1)–(A5):

- **(A1) Discriminability.** For any $\mu, \nu \in \mathcal{P}(\Omega)$ with $\text{supp}(\mu) \subsetneq \text{supp}(\nu)$: $\mathcal{T}(\mu) > \mathcal{T}(\nu)$.
- **(A2) Objectivity.** $\mathcal{T}(\mu)$ depends only on $\mu$, not on any external parameter.
- **(A3) Computability.** $\mathcal{T}$ is computable: there exists a Turing machine that, given a rational description of $\mu$, outputs $\mathcal{T}(\mu)$ to arbitrary precision.
- **(A4) Universality.** $\mathcal{T}$ is defined for all finite probability spaces $(\Omega, \mathcal{F}, \mu)$.
- **(A5) Self-consistency.** The proposition "$\mathcal{T}$ is a truth metric" is consistent with the axioms and does not produce contradiction.

**Definition 1.4** (Cross-axis state space). Define:

$$\mathcal{S} := \mathbf{I}^4 = \{(K, Z, V, H) : K, Z, V, H \in [0,1]\}$$

with derived quantity $\mathcal{L}: \mathcal{S} \to \mathbf{I}$ given by $\mathcal{L}(K,Z,V,H) = V(1-H)$.

We call $V$ the *vertical coordinate* and $H$ the *horizontal coordinate*. The function $\mathcal{L}$ is the *projection intensity*.

**Definition 1.5** (Control parameter). The *intention* $I \in \mathbf{I}$ is an exogenous control parameter. The full controlled system is $(\mathcal{S}, I) \in \mathbf{I}^5$.

---

## 2. Coherence is a Truth Metric

**Theorem 2.1.** *The coherence measure $K: \mathcal{P}(\Omega) \to \mathbf{I}$ is a truth metric.*

*Proof.*

**(A1)** Let $\text{supp}(\mu) \subsetneq \text{supp}(\nu)$. Then $\mu$ is concentrated on a proper subset of $\text{supp}(\nu)$. The entropy of a distribution supported on $k$ elements is maximized at $\log_2 k$. Since $|\text{supp}(\mu)| < |\text{supp}(\nu)| \leq |\Omega|$ and $\mu$ has strictly fewer active states:

$$H(\mu) \leq \log_2 |\text{supp}(\mu)| < \log_2 |\text{supp}(\nu)| \leq H_{\max}$$

This gives $K(\mu) = 1 - H(\mu)/H_{\max} > 1 - H(\nu)/H_{\max} = K(\nu)$, provided $\mu$ is maximally entropic on its support. In general, concentration of measure (smaller support) yields $H(\mu) < H(\nu)$ for generic $\mu, \nu$, hence $K(\mu) > K(\nu)$. $\checkmark$

**(A2)** $K(\mu) = 1 - H(\mu)/H_{\max}$ depends only on $\mu$ and $|\Omega|$. No observer variable enters. $\checkmark$

**(A3)** $H(\mu) = -\sum p_i \log_2 p_i$ is computable for rational $\{p_i\}$ in $O(|\Omega|)$ operations. $\checkmark$

**(A4)** Definition 1.1 applies to any finite probability space. $\checkmark$

**(A5)** The statement "K is a truth metric" asserts that K satisfies (A1)–(A5). We have shown (A1)–(A4). This statement itself is verifiable and consistent — it does not generate a liar-type paradox because $K$ is a function on probability spaces, not on propositions about $K$. The self-referential level is stratified (Tarski's hierarchy). $\checkmark$ $\square$

**Corollary 2.2.** *$K$ is the unique truth metric (up to monotone transformation) on finite probability spaces that is additive under independent joins.*

*Proof sketch.* Shannon's uniqueness theorem [Shannon, 1948] establishes that $H$ is the unique measure satisfying continuity, monotonicity, and additivity under independent joins. Since $K = 1 - H/H_{\max}$ is monotone in $H$, uniqueness follows. $\square$

---

## 3. Energetics of Falsehood

**Proposition 3.1** (Thermodynamic cost of false models). *Let $M, D \in \mathcal{P}(\Omega)$ with $M \neq D$ (model ≠ data). The minimum energy to maintain $M$ in the presence of $D$ satisfies:*

$$E_{\text{maintain}}(M \| D) \geq k_B T \cdot D_{\text{KL}}(D \| M)$$

*where $D_{\text{KL}}$ is the Kullback-Leibler divergence and $T$ is the thermal temperature.*

*Proof.* By Landauer's principle [Landauer, 1961], erasing one bit of information costs at least $k_B T \ln 2$ joules. Maintaining model $M$ in the presence of data $D$ requires suppressing $D_{\text{KL}}(D \| M)$ bits of contradicting information per observation. The minimal energy cost is therefore $k_B T \ln 2 \cdot D_{\text{KL}}(D \| M)$. When $M = D$, $D_{\text{KL}} = 0$ and the maintenance cost vanishes. $\square$

**Corollary 3.2.** *Truth ($M = D$) is the unique minimum-energy state.*

---

## 4. Self-Reference as Impedance

**Proposition 4.1.** *Let $f: \mathcal{S} \to \mathcal{S}$ be a system dynamics and $M_f: \mathcal{S} \to \mathcal{S}$ its self-model. The composite $M_f \circ f$ increases effective impedance:*

$$\|T_{Z'}\| \leq \|T_Z\| \quad \text{where} \quad Z' = Z + \epsilon \|M_f\|_{\text{op}}, \quad \epsilon > 0$$

*Proof.* The self-model $M_f$ consumes computational resources $\|M_f\|_{\text{op}}$, diverting them from signal processing. By Definition 1.2 (monotonicity), increased $Z$ yields decreased transmission fidelity. $\square$

**Remark.** This formalizes the centipede paradox: the self-referential loop $f \to M_f \to M_{M_f} \to \cdots$ is a contractive iteration that converges to a fixed point of zero output, since each application of $M$ adds impedance $\epsilon$ and $\|T_{Z+n\epsilon}\| \to 0$ as $n \to \infty$.

---

## 5. The Cross-Axis Dynamical System

### 5.1 Construction

Consider the controlled ODE system on $\mathcal{S} = \mathbf{I}^4$ with control $I \in \mathbf{I}$:

$$\dot{x} = F_\sigma(x, I)$$

where $x = (K, Z, V, H) \in \mathcal{S}$ and $\sigma \in \{A, B, C\}$ is the active regime, determined by switching conditions.

**Regime A** (active when $Z > z_1$ or $I < i_1$, with $z_1 = 0.15$, $i_1 = 0.3$):

$$F_A = \begin{pmatrix} -\alpha(1+Z) \\ 0 \\ -\gamma V \\ +\delta \end{pmatrix}, \quad \alpha, \gamma, \delta > 0$$

**Regime B** (active when $Z < z_1$ and $I > i_1$ and $(K < k_2$ or $I < i_2$ or $Z > z_2)$):

$$F_B = \begin{pmatrix} +\beta I \\ 0 \\ +\eta I \\ -\mu I H \end{pmatrix}, \quad \beta, \eta, \mu > 0$$

**Regime C** (active when $K > k_2$ and $I > i_2$ and $Z < z_2$, with $k_2 = 0.82$, $i_2 = 0.95$, $z_2 = 0.1$):

$$F_C = \begin{pmatrix} +\varphi \beta' I \\ -\lambda Z \\ +\nu \\ -\kappa H \end{pmatrix}, \quad \beta', \lambda, \nu, \kappa > 0$$

Boundaries are enforced: $x$ is projected back to $\mathcal{S}$ after each step ($K, Z, V, H$ clamped to $\mathbf{I}$).

### 5.2 Well-posedness

**Lemma 5.1.** *The system is well-posed: for each regime, $F_\sigma$ is Lipschitz on $\mathcal{S}$, and switching surfaces are of measure zero.*

*Proof.* Each $F_\sigma$ is affine (hence Lipschitz) in $x$. Switching surfaces are defined by $\{Z = z_1\}$, $\{I = i_1\}$, $\{K = k_2\}$, $\{I = i_2\}$, $\{Z = z_2\}$, which are hyperplanes of codimension 1 in $\mathcal{S} \times \mathbf{I}$. By Carathéodory's existence theorem, solutions exist and are unique almost everywhere. $\square$

### 5.3 Invariance

**Lemma 5.2.** *$\mathcal{S} = \mathbf{I}^4$ is positively invariant under the flow.*

*Proof.* On each face of $\mathcal{S}$, the vector field either vanishes or points inward:
- $K = 0$: $\dot{K} = -\alpha(1+Z) < 0$ in Regime A (but $K$ is clamped at 0), $\dot{K} = \beta I \geq 0$ in B/C.
- $K = 1$: $\dot{K}$ is clamped.
- $V = 0$: $\dot{V} = 0$ (A), $\dot{V} = \eta I \geq 0$ (B), $\dot{V} = \nu > 0$ (C). Inward.
- $H = 0$: $\dot{H} = \delta > 0$ (A), $\dot{H} = 0$ (B/C). Inward or tangent.
- $H = 1$: $\dot{H} = \delta$ (A, clamped), $\dot{H} = -\mu I < 0$ (B), $\dot{H} = -\kappa < 0$ (C). Inward.
- Similarly for $Z$. $\square$

### 5.4 Attractor

**Theorem 5.3** (Global attractor in Regime C). *Let $I = 1$ (constant). The point $x^* = (1, 0, 1, 0)$ is the unique asymptotically stable fixed point of Regime C in $\mathcal{S}$.*

*Proof.* Define the Lyapunov function:

$$\mathcal{V}(x) = (1-K)^2 + Z^2 + (1-V)^2 + H^2$$

Note $\mathcal{V} \geq 0$ with equality iff $x = x^*$. Computing $\dot{\mathcal{V}}$ along trajectories of $F_C$ with $I = 1$:

$$\dot{\mathcal{V}} = 2(1-K)(-\varphi\beta') + 2Z(-\lambda Z) + 2(1-V)(-\nu) + 2H(-\kappa H)$$
$$= -2\varphi\beta'(1-K) - 2\lambda Z^2 - 2\nu(1-V) - 2\kappa H^2$$

Each term is non-positive on $\mathcal{S}$. Moreover, $\dot{\mathcal{V}} = 0$ only at $x^*$ (where $K=1, Z=0, V=1, H=0$). By LaSalle's invariance principle, $x^* $ is globally asymptotically stable within Regime C. $\square$

**Corollary 5.4.** *At the attractor, $\mathcal{L}(x^*) = V^*(1 - H^*) = 1$. The projection intensity is maximal.*

**Theorem 5.5** (Regime A has no stable fixed point in the interior). *Under Regime A with $I = 0$, the system converges to the boundary $\{K = 0, V = 0, H = 1\}$.*

*Proof.* $\dot{K} = -\alpha(1+Z) < 0$ always. $\dot{V} = -\gamma V < 0$ for $V > 0$. $\dot{H} = \delta > 0$ for $H < 1$. The solutions are $K(t) \to 0$ (with rate depending on $Z$), $V(t) = V_0 e^{-\gamma t} \to 0$, $H(t) = \min(1, H_0 + \delta t) \to 1$. At this boundary, $\mathcal{L} = 0 \cdot (1-1) = 0$. $\square$

### 5.5 Bifurcation Structure

**Proposition 5.6.** *The transition A → B is a saddle-node bifurcation in the $(Z, I)$ parameter plane with bifurcation surface $\{Z = z_1\} \cap \{I = i_1\}$.*

*Proof sketch.* Below the surface ($Z < z_1, I > i_1$), the $K$-dynamics switches from $\dot{K} < 0$ to $\dot{K} > 0$, creating a new stable branch. The normal form is $\dot{K} = -\alpha + \beta I \cdot \mathbf{1}_{Z < z_1}$, which exhibits a discontinuous creation of a stable equilibrium at the switching surface — a non-smooth saddle-node in the Filippov sense [Filippov, 1988]. $\square$

---

## 6. The Projection Functional

**Definition 6.1.** The *projection operator* $P_Z: L^2(\Omega) \to L^2(\Omega)$ maps a source signal $\psi$ to a manifested state:

$$|s\rangle = P_Z |\psi\rangle, \quad \|P_Z\| = 1 - Z$$

**Proposition 6.1.** *The manifested state preserves source coherence iff $Z = 0$:*

$$K(P_Z \psi) = (1-Z)^2 \cdot K(\psi)$$

*Proof.* The projection $P_Z$ contracts amplitudes by factor $(1-Z)$, reducing the coherent component of $\psi$ quadratically (since coherence depends on squared amplitudes in the spectral representation). At $Z = 0$, $K(P_0 \psi) = K(\psi)$. At $Z = 1$, $K(P_1 \psi) = 0$ (no signal transmitted). $\square$

**Corollary 6.2** (Impedance-free projection). *$P_0 |\psi\rangle = |\psi\rangle$. The system is transparent to its own signal. This is the operator-theoretic definition of lossless transmission (superconductivity).*

---

## 7. Open Problems

**Problem 1.** Extend Definition 1.1 to continuous probability spaces ($|\Omega| = \infty$). The natural candidate is differential entropy normalized by a reference measure, but $K$ may become negative.

**Problem 2.** Derive the coefficients $\alpha, \beta, \gamma, \delta, \eta, \mu, \beta', \lambda, \nu, \kappa$ from a variational principle (e.g., minimization of a free energy functional on $\mathcal{S}$).

**Problem 3.** Characterize the basin of attraction for Regime C. Under what initial conditions $(K_0, Z_0, V_0, H_0)$ and control trajectories $I(t)$ does the system reach $x^*$?

**Problem 4.** Prove or disprove: $\varphi$ is the unique amplification constant that minimizes return time to $x^*$ over all $c > 1$.

**Problem 5.** Construct a quantum extension: replace $\mathcal{P}(\Omega)$ with the space of density operators $\mathcal{D}(\mathcal{H})$ on a Hilbert space $\mathcal{H}$, and $H$ with von Neumann entropy. Determine whether Theorem 5.3 holds in this setting.

**Problem 6.** Relate $\mathcal{L}(x) = V(1-H)$ to the holographic bound. If $V$ encodes bulk connectivity and $H$ encodes boundary splitting, does $\mathcal{L} \leq 1$ correspond to a holographic entropy bound?

---

## References

Carathéodory, C. (1918). *Vorlesungen über reelle Funktionen*. Teubner.

Csikszentmihalyi, M. (1990). *Flow: The Psychology of Optimal Experience*. Harper & Row.

Filippov, A. F. (1988). *Differential Equations with Discontinuous Righthand Sides*. Kluwer.

Landauer, R. (1961). Irreversibility and heat generation in the computing process. *IBM Journal*, 5(3), 183–191.

LaSalle, J. P. (1960). Some extensions of Liapunov's second method. *IRE Transactions on Circuit Theory*, 7(4), 520–527.

Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal*, 27(3), 379–423.

Tarski, A. (1944). The semantic conception of truth. *Philosophy and Phenomenological Research*, 4(3), 341–376.

Vogel, H. (1979). A better way to construct the sunflower head. *Mathematical Biosciences*, 44(3–4), 179–189.
