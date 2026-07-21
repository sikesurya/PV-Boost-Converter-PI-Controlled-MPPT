# 3 MW Photovoltaic Array with Closed-Loop Boost Converter and P&O MPPT

## Overview

This project presents the design and simulation of a utility-scale **3 MW photovoltaic (PV) energy conversion system** using MATLAB/Simulink. The system integrates a PV array, a DC-DC boost converter, and a closed-loop **Perturb and Observe (P&O) Maximum Power Point Tracking (MPPT)** controller to maximize solar energy extraction.

Unlike conventional implementations that use MATLAB Function blocks for MPPT, this project implements the complete P&O algorithm using native Simulink control blocks such as switches, delays, gains, and arithmetic operators. The boost converter duty cycle is regulated through a PI controller whose gains are tuned using MATLAB PID Tuner to achieve the desired transient response and robustness.

---

## Features

- Utility-scale **3 MW PV array** modeling
- PV array sizing based on module specifications
- Closed-loop **P&O MPPT** implemented entirely using Simulink blocks
- PWM-controlled DC-DC boost converter
- PI controller tuned using MATLAB PID Tuner
- Dynamic maximum power extraction
- Voltage, current, and power monitoring on both PV and converter sides

---

## System Architecture

```
Solar Irradiance & Temperature
              │
              ▼
        PV Array (3 MW)
              │
      Vpv, Ipv Measurements
              │
              ▼
      P&O MPPT Controller
              │
      PI Controller (PID Tuner)
              │
        PWM Generator
              │
              ▼
      DC-DC Boost Converter
              │
              ▼
      Regulated DC Output
```

---

## Project Description

The PV array converts solar irradiance into electrical energy. Based on the selected PV module characteristics, the number of series-connected modules and parallel strings is calculated to achieve a total system rating of **3 MW**.

The MPPT controller continuously measures the PV voltage and current to compute the instantaneous power output. Using the Perturb and Observe algorithm, the controller determines whether the operating point is moving toward or away from the Maximum Power Point (MPP). The duty cycle of the boost converter is adjusted accordingly to ensure maximum power extraction.

A PI controller is incorporated into the duty-cycle control loop to improve transient response and converter stability. The controller gains were tuned using MATLAB's PID Tuner to satisfy settling time and robustness requirements.

The boost converter increases the PV output voltage while presenting the appropriate input impedance to the PV array, enabling efficient energy transfer to the load.

---

## MPPT Algorithm

The controller performs the following operations every sampling interval:

1. Measure PV voltage and current.
2. Compute PV power.
3. Calculate:
   - ΔV
   - ΔI
   - ΔP
4. Determine whether the operating point has moved closer to or farther from the Maximum Power Point.
5. Increase or decrease the converter duty cycle accordingly.
6. Repeat until the operating point converges near the MPP.

The algorithm is implemented completely using Simulink logic blocks without any MATLAB scripting.

---

## PI Controller

The PI controller receives the MPPT output and generates the converter duty cycle.

The gains were optimized using MATLAB PID Tuner with the objectives of:

- Fast settling time
- Stable transient response
- Reduced steady-state error
- Improved robustness

The generated duty cycle is supplied to the PWM generator that drives the IGBT switch of the boost converter.

---

## Simulation Results

### PV Side

The first scope monitors:

- PV Voltage
- PV Current
- PV Output Power

The results demonstrate convergence to the maximum power operating point with stable electrical characteristics.

### Boost Converter Side

The second scope monitors:

- Output Voltage
- Output Current
- Output Power

The converter successfully boosts the PV voltage while maintaining stable output and efficient power transfer.

---

## Software Used

- MATLAB
- Simulink
- Simscape Electrical
- MATLAB PID Tuner

---

## Applications

This project demonstrates concepts widely used in:

- Utility-scale solar power plants
- DC microgrids
- Renewable energy systems
- Battery charging systems
- Electric vehicle charging infrastructure
- Power electronics control design
- Research and education in photovoltaic energy conversion

---

## Future Improvements

- Incremental Conductance MPPT
- Adaptive or fuzzy logic MPPT
- Bidirectional DC-DC converter
- Battery Energy Storage System (BESS)
- Grid-connected inverter with PLL synchronization
- Three-phase grid integration
- Hardware implementation on DSP/FPGA

---

## Author

**Surya Srinivas**

B.Tech. Electrical and Electronics Engineering  
National Institute of Technology Karnataka (NITK), Surathkal
