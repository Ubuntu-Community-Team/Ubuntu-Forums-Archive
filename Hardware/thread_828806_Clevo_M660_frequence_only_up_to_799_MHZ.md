---
title: "Clevo M660: frequence only up to 799 MHZ"
date: 2008-06-14
forum: Hardware
---

### Post by Aruhn on 2008-06-14
Hello,
i use a Clevo M660 notebook with this contents:
Intel Core Duo 2 GHZ
2 GB DDR2 RAM
Geforce 8400M G 
Ubuntu 8.04

I use the p4-clockmod modul for the frequence regulation (it is the only modul that works) but the highest available frequence is 799 MHZ, the lowest available frequence is 99 MHZ! :confused:

I think the problem lies in the file "/sys/devices/system/cpu/cpu0/scaling_available_frequencies".
This file shows me 99 199 299 up to 799 MHZ!

I installed sysfs.conf (/etc/sysfs.conf) and tested this configuration:

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu0/cpufreq/scaling_min_freq=800000
devices/system/cpu/cpu1/cpufreq/scaling min_freq=800000
devices/system/cpu/cpu0/cpufreq/scaling_max_freq=1800000
devices/system/cpu/cpu1/cpufreq/scaling_max_freq=1800000
```

But it does not work!

I have tested powernowd, without sucess and now I don't know how to solve this problem. 
I'am sure the problem lies in the /sys/devices/system/cpu/cpu0/scaling_available_frequencies file but I don't know how to configure this file or any file in this directory.

If I don't load the p4-clockmod Modul works the CPU just with die highest available frequence (2 GHZ).

greetings,
Aruhn

---

### Post by SPiG on 2008-06-14
I am having a very similar problem. 

I have an older Dell Inspiron 1100 that I put a P4m 2.4Ghz with Kubuntu 8.10. The fastest it goes is 1200mhz. Same problem and my conf files look same except that it goes to 1200000. The laptop is SLOW because of this, but the battery lasts forever.

---

### Post by Aruhn on 2008-06-16
Knows no one an answer of this problem?

An acpi fix from Acpi4Linux didn't solve the problem either. :(

---

