# Hybrid Electric Vehicle (HEV) Powertrain & Dynamics Portfolio

This repository contains the comprehensive engineering workflows, mathematical models, and computational simulations developed during my **Hybrid Electric Vehicle Internship** (Feb 2026 – Apr 2026)[cite: 8]. The portfolio is divided into three core technical modules bridging multi-domain physics, electromechanical core actuators, and physical vehicle-terrain constraints[cite: 5, 6, 7].

---

## ⚡ Module 1: EV Motor Efficiency & Torque-Speed Mapping (MATLAB)

An analytical scripting framework designed to simulate and map the performance boundaries of an EV traction motor across highly diverse operational profiles[cite: 5].

### Core Architecture & Implementation
* **Vector-Based Processing:** Utilized array-based vector operations in MATLAB to simultaneously compute 100 localized speed evaluation points in a single runtime loop[cite: 5].
* **Efficiency Boundaries:** Modeled dominant resistive copper losses ($P_{\text{loss}} = I^2R$) to map torque degradation curves and track power constraints[cite: 5].
* **Multi-Scenario Validation:** Evaluated system performance across 4 distinct real-world operating conditions covering a 48–96V and 10–25A envelope[cite: 5]:
  * *Set 1:* Low Voltage, Light Load urban cruise profiling ($48\text{V}, 10\text{A}$) — achieved a **99.98% peak electrical efficiency** under a constant load torque configuration mapping the mechanical performance[cite: 5].
  * *Set 2:* Medium Voltage, Medium Load mixed-cycle profiling ($72\text{V}, 15\text{A}$)[cite: 5].
  * *Set 3:* High Voltage, Heavy Load highway demand profiling ($96\text{V}, 20\text{A}$)[cite: 5].
  * *Set 4:* Low Voltage, Heavy Load steep incline climbing profiling ($48\text{V}, 25\text{A}$)[cite: 5].

---

## 🏎️ Module 2: Multi-Force Vehicle Dynamics & Traversal Simulation (Simulink)

A continuous-time physical block-diagram plant engineered to trace the dynamic force chain of an EV moving along an unyielding, variable terrain profile[cite: 6].

### Core Architecture & Implementation
* **Mathematical Superposition of Forces:** Implemented parallel computation branches resolving the three primary resistive physical vectors opposing forward mobility[cite: 6]:
  * **Gradient Force ($F_h$):** Gravity-induced rollback forces parsed via road inclination angles[cite: 6].
  * **Rolling Resistance ($F_r$):** Continuous tire deformation losses tracking road surface friction[cite: 6].
  * **Aerodynamic Drag Force ($F_d$):** Velocity-squared air resistance scaling with frontal vehicle area[cite: 6].
* **Successive Integration Network:** Routed net effective force ($F_{\text{eff}} = F_{\text{motor}} - F_{\text{total}}$) through sequential Simulink integrator blocks to output continuous real-time changes in acceleration, velocity, and distance tracks[cite: 6].
* **Validation Baseline:** Confirmed absolute physical model correctness under a nominal 200 Nm motor torque constraint, validating a final steady-state velocity of **93.71 KMPH** over a 0.1302 KM track[cite: 6].

---

## 🤖 Module 3: Armature-Controlled DC Motor Plant Modeling (MATLAB & Simulink)

A dual mechanical-electrical coupled subsystem plant derived from basic physical principles to evaluate low-level actuator transient, steady-state, and frequency responses[cite: 7].

### Core Architecture & Implementation
* **First-Principles Derivation:** Formulated the coupled dynamic equations of the plant by combining Kirchhoff’s Voltage Law (for the electrical loop) with Newton’s Second Law of Motion (for rotational rotor inertia)[cite: 7].
* **Transfer Function Extraction:** Mapped the time-domain system into the Laplace domain to construct a continuous second-order transfer function relating output shaft angular velocity ($\omega$) directly to input armature voltage ($V$)[cite: 7]:
  $$P(s) = \frac{K}{(Js+b)(Ls+R)+K^2}$$
* **Stability & Frequency Tuning:**
  * Analyzed system roots to reveal two real, negative poles ($s_1 \approx -2.002, s_2 \approx -9.998$), proving an **overdamped, asymptotically stable system response** completely isolated from transient oscillations[cite: 7].
  * Deployed the MATLAB Control System Toolbox alongside graphical Simulink blocks to cross-validate open-loop step responses, Dirac delta impulses, and log frequency roll-off characteristics via Bode plots[cite: 7].
