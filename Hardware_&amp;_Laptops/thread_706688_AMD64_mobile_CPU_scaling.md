---
title: "AMD64 mobile CPU scaling"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by ALSW123 on 2008-02-24
Hi this is the second time i've asked for help as I remember, but well everything else i've been able to solve "myself" by searching this forum! 

I'm running 64bit Ubuntu 7.10 on a Fujitsu amilo a 1630 laptop (Uniwill 258KA0) 

To get it ubuntu to boot at all I had to disable ACPI using the command no acpi acpi=off in the boot command. I believe this may be why my cpu is stuck at 798mhz (amd 3700+ m)  (in windows I could use 798, 1400ish and 2400mhz steps)

Without acpi disabled ubuntu hangs on boot at loading cpufreq

I've tried just about every guide going but can't get anything to work, usually it says that x directory doesn't exist, e.g.  powernowd gives the error; 

 > PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.


Anyone got any ideas?

---

