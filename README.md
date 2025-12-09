# AOSP-SimulateAFakeHardwareSensor
**## Task: Add a Virtual Hardware Sensor with Full Stack Integration**
**Simulate a fake hardware sensor ("Proximity++") that outputs a value from 0.0 to 1.0, and expose it to a custom Android app via the Android sensor framework.**

**## Deliverables**
**- Working AOSP build (x86 or ARM emulator)**
**- Fake HAL for `android.hardware.sensors@2.1::ISensors`**
**- System service or JNI bridge, if needed**
**- App or CLI that reads sensor values**
**- Instructions to build, run, and test**
**- \*\*Short design document\*\* explaining architecture decisions**
**---**

**## Requirements**
**1. \*\*Fake Sensor HAL\*\***
   **- Implement a fake proximity sensor in AIDL or HIDL.**
   **- Output sinusoidal values (e.g., `0.5 + 0.5 \* sin(t)`) every 500ms.**

**2. \*\*Integration with SensorManager\*\***
   **- Modify HAL and VINTF manifest to register the sensor.**
   **- Ensure it shows up in `/sensors\_list` via `adb shell`.**
   
**3. \*\*Optional:\*\* Add a JNI call or use AIDL to expose the sensor to a system app directly.**

**4. \*\*Test App or CLI Tool\*\***
   **- Create a minimal app or script that logs the current sensor value every second.**

**5. \*\*Design Document\*\***
   **- Write a short (1–2 page) explanation of your architecture and decisions.**
   **- Discuss why you chose AIDL vs HIDL, polling vs event-driven, etc.**
**---**

**## Bonus Task: Debugging Scenario**

**You must also diagnose and resolve a specific issue: the sensor \*\*does not appear in `/sensors\_list`\*\*.**
**- Cause: An \*\*SELinux policy violation\*\* is silently blocking sensor registration.**
**- Fix the issue and document your debugging steps.**
**- Include any SELinux rule modifications or audit log findings.**
**---**

**## Bonus Task: Challenge Extension**
**Modify the fake sensor so that:**
**- Its value can be controlled via `adb shell setprop my.proximity.override 0.7`**
**- Your app reflects the new value within 1s**

