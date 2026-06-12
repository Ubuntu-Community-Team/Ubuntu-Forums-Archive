---
title: "cpu frequency cannot be detected after upgrading to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by damarius on 2009-04-25
After upgrading to kubuntu 9.04 the system didn't recognise the battery.
I installed kde-guidance-powermanager and the battery problem was fixed.
But now, it cannot detect de cpu frequency and I cannot enable the scaling
capability.
I'm using a Toshiba Satellite A200-23K.
I attached the output for /proc/cpuinfo.

---

### Post by graysky on 2009-04-25
Are the right kernel modules loaded (i.e. modprobe acpi-cpufreq).  I dunno which modules are needed for your battery.  Perhaps 'battery'?

---

### Post by damarius on 2009-04-25
I've found a solution.
After installing the **cpufrequtils** package everything worked fine.

---

