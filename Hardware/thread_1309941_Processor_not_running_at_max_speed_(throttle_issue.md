---
title: "Processor not running at max speed? (throttle issues?)"
date: 2009-11-01
forum: Hardware
---

### Post by zim2dive on 2009-11-01
I have an E5200.. dual core @ 2.5GHz... 

> >cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz

yet when I look at the CPU scaling menu (gnome tools I think) the only options I see are 1.9 and 1.2 GHz, which is reinforced by looking at>  >cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1900000 1200000

I started Firefox at fullscreen Hulu, top shows 120%+ for the process, but >  >cpufreq-info
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.20 GHz - 1.90 GHz
  available frequency steps: 1.90 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 1.90 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.90 GHz.
  cpufreq stats: 1.90 GHz:0.00%, 1.20 GHz:0.00%  (4)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.20 GHz - 1.90 GHz
  available frequency steps: 1.90 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 1.90 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
  cpufreq stats: 1.90 GHz:0.00%, 1.20 GHz:0.00%  (97)

still only shows 1.9GHz... 

what gives? (running 9.10)

EDIT: more info > >more /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1900000

EDIT2: This will sound like "my dog ate my homework", but my BIOS settings were changed (the CPU clock multiplier was set to 9.5 instead of 12.5.. giving me 1900 instead of 2500).  This was on a BIOS page that I have NEVER touched tho (I steer clear of the overclocking page, until I research it more), so I have no idea how/when/why that setting changed.

---

