---
title: "CPU scaling max set to min"
date: 2008-09-04
forum: Hardware
---

### Post by genlee on 2008-09-04
I have a dell latitude D830 and my cpu will not scale past 800MHz. CPU is an intel core 2 duo T7500. Supports up to 2.2GHz but the range only shows 800MHz to 800MHz for any profile I set. Here is output:


cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

---

