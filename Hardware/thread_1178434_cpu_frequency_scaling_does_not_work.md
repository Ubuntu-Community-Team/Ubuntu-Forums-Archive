---
title: "cpu frequency scaling does not work"
date: 2009-06-04
forum: Hardware
---

### Post by cghl07 on 2009-06-04
Following an upgrade from 8.04 to 8.10 frequency scaling on my IBM T43 ceased to work.

Whatever I set in the frequency scaling  applet has no effect whatsoever; the machine consistently runs on minimum clock frquency (800MHz).

What is suspicious is that both /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq and /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq show 800000.

Likewise, cpufreq-info says
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [EMAIL="linux@brodo.de"]linux@brodo.de[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

So, any policy keeps the frequency between 800MHz and 800MHz, which is what I can observe.

Both manually editing the /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq file and using the cpufreq-set utility have no effect. It seems the file is immediately overwritten by some demon.

Last infos:
 cg@milos:/sys/devices/system/cpu/cpu0/cpufreq> cat scaling_setspeed 
<unsupported>
cg@milos:/sys/devices/system/cpu/cpu0/cpufreq> cat scaling_available_frequencies
2000000 1600000 1333000 1066000 800000 

As said before everything was fine under 8.04 before the upgrade.

Any ideas anyone?

---

