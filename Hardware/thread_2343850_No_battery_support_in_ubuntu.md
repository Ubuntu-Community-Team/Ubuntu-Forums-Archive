---
title: "No battery support in ubuntu"
date: 2016-11-19
forum: Hardware
---

### Post by lucianolin on 2016-11-19
Hello guys.
I am using a ubuntu system(version 16.04) in a HP laptop of HP Pavilion x2 - 10-n107nl (ENERGY STAR).
I now meet with a problem that i could not see the battery icon on the upper right corner of the screen, which means that i could't not see the current battery consumption.
I type in command line acpi and it shows that:

```
No support for device type: power_supply
```

Can somebody help me to solve this problem?

---

### Post by TheFu on 2016-11-20
Is **acpi** loaded?
Open a terminal, run **acpi -V**. Something like this should be returned.
```
$ acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 4000 mAh, last full capacity 4004 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 39.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 104.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 0: trip point 2 switches to mode active at temperature 75.0 degrees C
Cooling 0: x86_pkg_temp no state information available
Cooling 1: pch_wildcat_point no state information available
Cooling 2: intel_powerclamp no state information available
Cooling 3: Processor 0 of 17
Cooling 4: Processor 0 of 17
Cooling 5: Processor 0 of 17
Cooling 6: Processor 0 of 17
Cooling 7: Fan 1 of 1
Cooling 8: Fan 0 of 1

```
If that works, there is hope for a GUI thingy to monitor the battery.

---

### Post by lucianolin on 2016-11-20
It seems that i have different output with yours.
```
No support for device type: power_supply
No support for device type: power_supply
Thermal 0: ok, 26.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 200.0 degrees C
Thermal 0: trip point 1 switches to mode hot at temperature 200.0 degrees C
Thermal 1: ok, 0.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 90.0 degrees C
Thermal 1: trip point 1 switches to mode hot at temperature 120.0 degrees C
Cooling 0: soc_dts1 no state information available
Cooling 1: soc_dts0 no state information available
Cooling 2: PNIT no state information available
Cooling 3: INT3400 Thermal no state information available
Cooling 4: STR3 no state information available
Cooling 5: STR0 no state information available
Cooling 6: intel_powerclamp no state information available
Cooling 7: TCHG 0 of 4
Cooling 8: Processor 0 of 10
Cooling 9: Processor 0 of 10
Cooling 10: Processor 0 of 10
Cooling 11: Processor 0 of 10

```

Something goes wrong?

---

