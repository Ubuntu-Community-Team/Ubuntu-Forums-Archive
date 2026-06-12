---
title: "CPU temperature and usage."
date: 2011-05-12
forum: Hardware
---

### Post by norm.h on 2011-05-12
I have an Intel Pentium 4 631 3 GHz processor on a Foxconn 945G7AD-8KS2H motherboard, running Ubuntu 10.10, and I am confused by the Hardware Sensors Monitor applet, and the System Monitor.

My Hardware Sensors Monitor applet shows two temperatures, temp 1 and CPU, both registering 40c, even when starting from cold.

When I run the command "sensors", I get:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +125.0°C) 

no mention of the CPU temperature.

I only have one CPU, and hovering the pointer over the System Monitor applet just shows processor usage percentage, but in System Monitor on the System Menu, CPU History shows CPU 1 and CPU 2, both registering on the moving graph, with slightly different usage.

Can anyone explain this please?

---

### Post by Yellow Pasque on 2011-05-12
The 2 CPU's are virtual cores (because of intel hyperthreading feature), and they will have different usage. The ACPI and CPU temp measure the temp of your CPU and should be the same (assuming they're accurate).

---

### Post by doas777 on 2011-05-12
you may have incompatible sensors (foxxcon is the bottom of the barrel after all), but those readings don't seem too far off from what i saw with my old P4HT@2.8 . it was one of the coolest running chips I have ever had (below 20C during the winter, even under a load). I also noticed it;s temp fluctuated far less than those I've had since (my pentium D experience was diasterous...). HT chips present a virtual core, as Temujin said, so the sensors may read two CPUs, with differant usage, but since it;s the same physical chip (and theres no such thing as virtual temperature), the reading will be teh same per "core".

just to confirm, you have run 
```
sudo sensors-detect
``` and walked through the setup, and loading the kernel modules, right?

---

### Post by norm.h on 2011-05-12
Thank you both for your explanations
Kernel module loaded OK
n

---

