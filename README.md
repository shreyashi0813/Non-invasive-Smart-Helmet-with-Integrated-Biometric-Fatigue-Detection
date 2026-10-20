# Non-Invasive Smart Helmet System with Integrated Biometric Fatigue Detection

An embedded smart-helmet prototype combining biometric-signal acquisition, alcohol sensing, helmet-wearing verification, crash/impact detection, wireless communication, GPS-based incident location, and a receiver-side ignition interlock demonstration.

## Project Overview

The design is split into two embedded units:

- **Helmet-side transmitter:** Arduino Uno, biometric-signal front end, MQ-3 alcohol sensor, IR wear-detection sensor, SW-420 vibration sensor, NEO-6M GPS, and an nRF24L01 wireless transmitter.
- **Vehicle-side receiver:** Arduino Uno, nRF24L01 receiver, L298N motor driver, 12 V DC motor used to simulate ignition, and a push-button input.

The receiver evaluates the incoming status and demonstrates enabling or blocking the simulated ignition according to the configured safety checks.

## Main Functions Described in the Document

- Biometric signal acquisition and threshold-based fatigue indication
- MQ-3 alcohol sensing and alcohol-based ignition lockout
- IR-based helmet-wearing verification
- SW-420 vibration / crash-event indication
- nRF24L01 wireless communication in the 2.4 GHz band
- NEO-6M GPS coordinates associated with critical events
- Local LED / buzzer / vibration alerts as implemented
- Receiver-side ignition control demonstrated with an L298N and DC motor

## System Architecture

```text
HELMET-SIDE TRANSMITTER
Biometric sensor + AD620 amplifier
MQ-3 alcohol sensor
IR helmet-wear sensor
SW-420 vibration sensor
NEO-6M GPS
          |
          v
      Arduino Uno
          |
          v
   nRF24L01 transmitter
          |
          v
   nRF24L01 receiver
          |
          v
      Arduino Uno
          |
          v
     L298N motor driver
          |
          v
  12 V DC motor (ignition simulation)
```

This is a simplified summary of the architecture shown in the uploaded document, especially the transmitter and receiver diagrams (Figures 2–5). It is not a verified wiring diagram.

## Hardware Components

| Component | Role stated in the document |
|---|---|
| Arduino Uno (two units) | Helmet transmitter and vehicle-side receiver |
| AD8232 ECG module / biometric sensor | Signal acquisition front end as listed in the component table |
| AD620AN instrumentation amplifier | Amplification stage described in the document |
| MQ-3 alcohol sensor | Alcohol sensing |
| IR sensor module | Helmet-wearing verification |
| SW-420 vibration sensor | Vibration / crash indication |
| nRF24L01 modules (two) | Helmet-to-receiver wireless link |
| NEO-6M GPS | Location tracking for critical events |
| LED indicators | Visual status indication |
| L298N motor driver | Drives the motor used for ignition simulation |
| 12 V DC motor | Demonstration load representing ignition |
| Push button | Ignition-key input in the receiver demonstration |

The document uses inconsistent terms for the biometric input (EEG, ECG and EMG) in different sections. The implementation should be described using the actual sensor and signal measured; an ECG module does not by itself establish that EEG is being measured. Confirm the real sensor, electrode placement, conditioning circuit, and signal-processing method before making stronger claims.

## Operating Workflow

1. The helmet-side Arduino reads the biometric, alcohol, helmet-wear, and vibration sensor inputs.
2. The controller applies the implemented thresholds and prepares a status payload.
3. The nRF24L01 link sends status data to the receiver-side Arduino.
4. The receiver checks the configured safety conditions.
5. The L298N controls a 12 V DC motor to demonstrate ignition enabled/blocked behaviour.
6. GPS coordinates are intended to be associated with critical events, as described in the document.

Exact thresholds, sampling rate, RF packet format, GPS-trigger logic, and signal-processing details should be documented from the actual firmware rather than inferred from the invention disclosure.


## Safety, Accuracy, and Scope

- This is an educational prototype, not a certified helmet, medical device, breath-alcohol instrument, or production vehicle ignition system.
- The document describes a biometric threshold approach, but does not establish clinical fatigue-detection accuracy. Do not present the prototype as a validated drowsiness diagnostic.
- MQ-series sensor output depends on warm-up, calibration, environment, and interfering vapours; do not interpret raw values as a precise blood-alcohol or breath-alcohol concentration.
- SW-420 vibration events can be triggered by ordinary bumps and vibration; crash detection requires careful validation and filtering.
- GPS may not have a reliable fix indoors or immediately after startup.
- The L298N/DC motor arrangement is a demonstration of ignition logic only. Do not connect this prototype to a real vehicle ignition system.
- The uploaded file is marked as an invention disclosure and contains VIT IPR&TTCELL markings. Check ownership, institutional approval, and patent-disclosure status before publishing document figures or the full draft.

## License

No license has been selected yet. Add one only after confirming that all code and design files may legally be licensed for reuse.
