---
title: "CPU Speed Test"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by 42Wired on 2007-03-28
I looked everywhere online for a CPU Speed Test utility that would work in Ubuntu, but only found ones that work in Windows.

The reason I need this is because I think that my Pentium M is running as if my laptop were on battery power (which would be about 550 Mhz instead of 1.7 Ghz). I have a Toshiba Portege M200 with a dual monitor setup via Xinerama.

---

### Post by raja on 2007-03-28
```
cat /proc/cpuinfo
``` will give you the information about your cpu.

---

