---
title: "Permanently 800Mhz?"
date: 2011-05-20
forum: Hardware
---

### Post by fireandfuel on 2011-05-20
Hi, at Natty (11.04) x64 I can not choose the CPU frequency mode on my Toshiba Satellite C660D notebook.
The CPU (AMD Athlon II X2 P340) runs permanently with 800Mhz instead of 2.2Ghz or 1.6Ghz. When I run "cpufreq-selector -c 0 -g performance" (and with "-c 1" option for the 2nd core, too) the CPU frequency doesn't increases to 2.2Ghz. Conservative, ondemand and userspace doesn't run, too.

I tested to adjust the CPU frequency while running Natty from LiveCD - no change :(. Than I booted from Ubuntu 10.04.1 (Lucid) x64 LiveCD - and (tada! :D) I can adjust the CPU frequency!
Ubuntu 10.10's version of Linux kernel have ACPI problems on my notebook. Thus I can't test it at Ubuntu 10.10.

**Does anybody have a idea how to get the CPU working with 2.2Ghz** (at least in ondemand or conservative mode)?

PS: I think that's not a hardware problem, because it runs on Lucid.
I already thought about downgrade Natty to Lucid (reinstall Lucid ;)), but on Lucid I doesn't have a working wlan driver and unity.

Some helpful information from the system:
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2200000 1600000 800000
```

---

### Post by fireandfuel on 2011-05-23
**UPDATE:** I created a bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/786897](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/786897)

---

