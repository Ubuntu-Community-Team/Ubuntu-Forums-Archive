---
title: "Indicator cpu-freq not working"
date: 2014-10-18
forum: Hardware
---

### Post by darek4 on 2014-10-18
Can someone Please help with getting indicator cpufreq applet working in ubuntu GNOME? i really like it. Thanks.

---

### Post by tgalati4 on 2014-10-18
Open a terminal:

```
cat /proc/cpuinfo
```

Not all processors support frequency scaling.  

```
cpufreq-info
```

It might look like:

> 
tgalati4@Mint14-Extensa ~ $ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.47 GHz
  available frequency steps: 1.47 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.47 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.47 GHz.
  cpufreq stats: 1.47 GHz:17.30%, 1.07 GHz:0.71%, 800 MHz:81.99%  (1771170)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.47 GHz
  available frequency steps: 1.47 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.47 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.47 GHz:15.73%, 1.07 GHz:0.68%, 800 MHz:83.59%  (7764)


---

