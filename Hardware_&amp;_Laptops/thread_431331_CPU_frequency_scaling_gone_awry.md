---
title: "CPU frequency scaling gone awry?"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by cdeel77 on 2007-05-02
I tried to enable frequency scaling on my lightly-used home server (in hopes of lowering power consumption/heat generation).
It's a Pentium 4 (1.4 GHz; family 15 model 0 stepping 7) running Edgy Server.

I used the "p4_clockmod" module. I checked the CPU freq with 3 methods:
```
cat /proc/cpuinfo
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
cpufreq-info
```
Before loading module, freq was 1406.274 (seems normal, right?)
After loading module, was 2200.000

**Is my CPU *really* running at 2.2 GHz? **If so, that could be a bad (overheating) thing, right? And how did that happen?

Output of cpufreq-info:
```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 550 MHz - 2.20 GHz
  available frequency steps: 550 MHz, 825 MHz, 1.10 GHz, 1.38 GHz, 1.65 GHz, 1.93 GHz, 2.20 GHz
  available cpufreq governors: performance
  current policy: frequency should be within 550 MHz and 2.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.20 GHz.
```
Should I just use "cpufreq-set --max 1375000" to limit the top speed, or do I have an unusual problem?

I've also tried loading the generic "acpi-cpufreq" module, but I get "FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.17-11-server/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device"

I intend to use the "ondemand" governor.

Thanks for any help/advice!

---

