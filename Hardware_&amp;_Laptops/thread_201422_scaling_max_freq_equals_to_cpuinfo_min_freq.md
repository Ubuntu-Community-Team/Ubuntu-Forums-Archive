---
title: "scaling_max_freq equals to cpuinfo_min_freq"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by DietrichM on 2006-06-21
I've got ondemand CPU frequency scaling working. The kernel modules loaded for this purpose are speedstep-centrino and cpufreq_ondemand.

However, I need to put the CPU's max frequency (/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq) into /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq, because for some reason it equals to the minimal frequency (800 MHz), as well for ondemand as for the performance governor.

What may be the cause of this and how can I fix this?

PS: I'm using a Sony Vaio FS with a Centrino chipset.

---

