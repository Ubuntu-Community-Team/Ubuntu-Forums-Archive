---
title: "ACPI, Opteron unable to Throttle"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by theycallhimtom on 2007-06-19
I have a Sun Ultra 20 M2 which has a Opteron 1210 in it. In /proc/acpi/processor/CPU0/throttling it says <not supported> while I'm pretty sure that the opteron 1210 does support CPU throttling. Whats happening? On a different issue there is no performance file in /proc/acpi/processor/CPU0/, but from /sys/devices/system/cpu/cpu0/cpufreq I can enter p-states by echoing to scaling_setspeed. Is that the way that p-states were meant to be setup?

On a slightly different issue it does list in /proc/acpi/processor/CPU0/power all of my C-states. Is there anyway to force the processor into certain C-states? Thanks for the help.

My LInux kernel version is: 2.6.20-15
My version of Ubuntu is 7.04

---

