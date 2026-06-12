---
title: "nvidia: cannot slow down cpu, always at maximum clock"
date: 2009-10-29
forum: Hardware
---

### Post by ildella on 2009-10-29
Hi. 

I have tried many ways: disabling powermizer in nvidia-settings and saving conf in ~/.nvidia-settings-rc or addding some configuration in xorg.conf, even enabling "coolbits" so I have the control to set manually the clock in nvidia-settings. Nothing change the fact that

Adaptive Frequency is enabled. 
Clock is always at maximum, perf level 2. 
CPU goes quickly to 95 Celsius, fan at maximum.

Does anyone have an idea how to force CPU to a slower clock or, better, to make adaptive frequency really work?

nvidia 8600m gt, 190.42, ubuntu 9.10.

---

### Post by willv on 2009-10-31
did you just recently update ubuntu to karmic koala?

i used to have my gpu at the lowest clock speed but now its always at the highest after i updated

---

