---
title: "CPU Fan wouldnt go off, powernowd makes problems."
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by amityak on 2008-01-27
Hallo guys and gals

Gusty on an Amilo V2035D machine. working perfectly except for the cpu fan, kinda driving me mad.

running powernowd provides me with that:

===================================================
jts@Jake-the-Laptop:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
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
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]

===================================================

id be grateful for any help or directions.

Cheerz , Amít.

---

