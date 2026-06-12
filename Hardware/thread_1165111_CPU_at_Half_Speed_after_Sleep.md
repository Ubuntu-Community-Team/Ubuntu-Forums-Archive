---
title: "CPU at Half Speed after Sleep"
date: 2009-05-20
forum: Hardware
---

### Post by wtstommy on 2009-05-20
Running Ubuntu 9.04. This problem occurs inconsistently, but often after coming up from a nap my laptop (Thinkpad t60p) will run at 1Ghz CPU speed instead of the usual 2Ghz. I cannot change the CPU speed with the Gnome Panel applet or with cpufreq-selector. It will not let me change the governer either.

Here is the output of cpufreq-info:

```
tommy@tommyTop:~$ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 2.00 GHz:0.10%, 1.67 GHz:0.00%, 1.33 GHz:0.00%, 1000 MHz:0.01%  (194)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 2.00 GHz:0.00%, 1.67 GHz:0.00%, 1.33 GHz:0.00%, 1000 MHz:0.01%t
```

---

