# 🩺 Dr. Test — Mobile Device Analyzer & Hardware Auditor

[![Platform: Android](https://img.shields.io/badge/Platform-Android-3DDC84.svg?style=flat&logo=android)](https://www.android.com/)
[![Min SDK: 24](https://img.shields.io/badge/Min%20SDK-24%20(7.0)-orange.svg)](https://developer.android.com/)
[![Target SDK: 37](https://img.shields.io/badge/Target%20SDK-37%20(Android%2015)-blue.svg)](https://developer.android.com/)
[![GitHub Release](https://img.shields.io/badge/Release-APK-blue.svg?logo=github)](https://github.com/smsajawalh/DrTest-APK)

**Dr. Test** is an enterprise-grade Android hardware diagnostic, anti-fraud verification, and device audit engine. Designed for secondhand smartphone marketplaces, repair technicians, refurbishers, and buyers, Dr. Test executes comprehensive real-time telemetry checks and interactive digitizer/sensor tests to generate verifiable, tamper-resistant health scorecards.

---

## ⚡ What's New in This Release

* **12 Comprehensive Hardware Modules**: Full-suite verification covering screen digitizers, acoustic loopback, physical volume rockers, multi-axis motion sensors, thermal thresholds, cameras, NFC, and biometric security.
* **Anti-Fraud Result Locking**: Automated mechanism that locks manual test overrides whenever root binaries (`su`, `test-keys`), overheating states ($\ge 48^\circ\text{C}$), or missing modules are detected.
* **Fair Telemetry Scoring Engine**: Normalizes health metrics strictly against actual hardware capabilities (devices missing optional sensors like Barometer/NFC are not penalized).
* **Native Single-Page A4 PDF Engine**: Generates auditable, digitally signed PDF reports formatted for thermal/A4 printing and instant sharing via Android `FileProvider`.
* **Adaptive Edge-to-Edge UI**: Process-level light branding, tactile haptic patterns, and gesture-aware responsive grid layouts for both phones and tablets/foldables.

---

## 🔍 Core Diagnostic Suite

| # | Diagnostic Module | Verification Method / Telemetry |
|---|---|---|
| **01** | **Root & Integrity** | Probes `su` binaries, build tags, and checks for tampering |
| **02** | **Display & Touch** | 7-color screen cycle (burn-in / dead pixels) + interactive touch digitizer grid |
| **03** | **Audio & Acoustics** | 440 Hz / 880 Hz tone output, microphone loopback recording, stereo separation |
| **04** | **Physical Keys** | Intercepts `onKeyDown` events for hardware Volume Up / Down rockers |
| **05** | **Motion Sensors** | Live telemetry for Accelerometer, Proximity, and Ambient Light sensors |
| **06** | **Connectivity** | Verifies state and signal availability for Wi-Fi, Bluetooth, and GPS |
| **07** | **Battery & Thermals** | Monitors charging rate (USB/AC), voltage, and alerts on thermals $\ge 48^\circ\text{C}$ |
| **08** | **Biometrics** | Evaluates `BiometricManager` capability and tests secure enrollment |
| **09** | **Camera & Flash** | Validates rear/front cameras and controls torch mode programmatically |
| **10** | **Secondary Sensors** | Tests Magnetometer ($\mu T$) vectors and Barometer ($hPa$) display seal integrity |
| **11** | **NFC Engine** | Modern asynchronous `enableReaderMode` for RFID, passes, and tags |
| **12** | **Wired Audio** | Verifies `ACTION_HEADSET_PLUG` state and dual-channel (L/R) stereo routing |

---

## 🛡️ Anti-Fraud Architecture

* **Hardware Failure Lockout**: Defective, missing, or compromised sensors automatically lock input checkboxes to **DISABLED**, preventing operators from marking broken hardware as passed.
* **Root Patch Detection**: Devices executing root modifications or custom ROMs with `test-keys` are permanently flagged as `PATCHED_SCAM / TAMPERED` on the final scorecard.
* **Dynamic Scorecard Math**:
  $$\text{Health Score } \% = \left( \frac{\text{Passed Supported Modules}}{\text{Total Supported Modules on Device}} \right) \times 100$$
  *Grading Thresholds*: **EXCELLENT** | **GOOD** | **FAIR** | **POOR**

---

## 📄 Native PDF Report Export

Dr. Test builds audit-ready single-page reports directly on-device using Android's native graphics and text layout engines:

* **Header & Metadata**: Device model, serial/IMEI baseline, OS version, hardware specifications, and audit timestamps.
* **Audit Certification Clause**: Standardized legal disclaimer verifying automated electronic hardware testing.
* **Instant Export**: Direct export via Android `FileProvider` to WhatsApp, Gmail, Google Drive, or Bluetooth print queues.

---

## 📦 System Requirements & Build Specs

* **Minimum OS**: Android 7.0 (API Level 24)
* **Target / Compile OS**: Android 15 (API Level 37)
* **Build Tooling**: Android Studio Jellyfish / Ladybug (2024.1+) or newer
* **Java Runtime**: OpenJDK 11+
* **Architecture**: Universal APK (ARM64-v8a, ARMeabi-v7a, x86_64)

