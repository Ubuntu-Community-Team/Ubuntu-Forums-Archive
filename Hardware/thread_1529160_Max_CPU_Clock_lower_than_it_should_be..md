---
title: "Max CPU Clock lower than it should be."
date: 2010-07-11
forum: Hardware
---

### Post by Adam24367 on 2010-07-11
I have run int[FONT=Arial]o an [/FONT]odd problem with Ubuntu. It may not seem like a huge deal, but I would like to have a fix anyway.
I have a Toshiba X205 writh a T9300 2.5ghz CPU. In windows, I get all 2.5ghz when the CPU Is running at full speed. In Ubuntu ```
$cat /proc/cpuinfo
``` gives me 2401.00mhz for the max speed. 

when I run 
```
$cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```[FONT=Verdana]
[FONT=Arial]In terminal, it gives me the output[/FONT]
[/FONT]```
2401000 2400000 2000000 1600000 1200000 800000
```[FONT=Verdana]

[FONT=Arial]This is extremely odd as it is a 2.5ghz CPU[/FONT]
[FONT=Arial]Is there any way to fix this?
It is actually quite annoying to me.
[/FONT]

[/FONT]

---

### Post by Adam24367 on 2010-07-13
I have noticed that in order to get to 2.5ghz, The CPU Requires a 12.5x Multiplier. It appears for some reason, Ubuntu does not want to take that half step multiplier.

---

