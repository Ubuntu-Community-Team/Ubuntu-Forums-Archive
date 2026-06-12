---
title: "One processor is heating more than others."
date: 2021-01-16
forum: Hardware
---

### Post by realt3ch on 2021-01-16
Hola all! :)

anyone know why one "Thermal" have 127 degree...? And is possible to fix this? is possible conected with ubuntu and upgrade from 16.04 to 20.04 ?

$ acpi -V
Battery 0: Discharging, 82%, 02:07:30 remaining
Battery 0: design capacity 1238 mAh, last full capacity 1238 mAh = 100%
Adapter 0: off-line
Thermal 0: ok, 25.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 128.0 degrees C
Thermal 1: ok, 0.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 128.0 degrees C
Thermal 1: trip point 1 switches to mode passive at temperature 102.0 degrees C
Thermal 2: ok, 33.0 degrees C
Thermal 2: trip point 0 switches to mode critical at temperature 128.0 degrees C
Thermal 3: ok, 127.0 degrees C
Thermal 3: trip point 0 switches to mode critical at temperature 128.0 degrees C
Thermal 4: ok, 32.0 degrees C
Thermal 4: trip point 0 switches to mode critical at temperature 128.0 degrees C
Thermal 4: trip point 1 switches to mode hot at temperature 100.0 degrees C
Thermal 5: ok, 31.0 degrees C
Thermal 5: trip point 0 switches to mode critical at temperature 128.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: pch_skylake no state information available
Cooling 2: iwlwifi_1 no state information available
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: intel_powerclamp no state information available
Cooling 6: x86_pkg_temp no state information available
Cooling 7: Processor 0 of 10


Thanks.! :)

---

### Post by TheFu on 2021-01-16
Don't assume any of those numbers are accurate. It could be a problem with the sensors library.  That is common for AMD CPUs.

If the core hasn't self-throttled, I wouldn't worry much, unless it ran at high temperatures all the time. Different CPUs have different operating temperatures. My Ryzen 5 should stay below 95 degC.  It is VERY busy now, but peaked at 78 degC.  Idle, it sits between 40 and 50 degC. It just finished a transcoding job that was running the last 90 minutes and has dropped by over 30 degC in about 2 min.

If you like, pull the CPU out, remove the heatsink, clean both contacts (lots of how-tos online), properly apply a quality CPU thermal grease, and put it all back together.

I doubt you have more than 1 CPU.  CPUs tend to have multiple "cores" these days. Call me "Mr. Pedantic" today. ;)

---

### Post by Yellow Pasque on 2021-01-19
127C is not accurate. It's probably a disconnected temperature sensor. (127 is the largest number for a signed 8-bit integer)
0C is definitely not accurate unless you live in Antarctica.

What is output of:
```
sensors
```

---

