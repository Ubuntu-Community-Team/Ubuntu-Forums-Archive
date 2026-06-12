---
title: "Too hot laptop and cpu freq scaling"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by Nano on 2005-11-15
Hi people.
I have installed all 3 versions of Ubuntu and I was never able to make powernowd work. This time I REALLY want at least to know if it's possible or not to do it.

First of all, I'm running breezy now with a Pentium4 2.8.
Whenever I try to run powernowd I get the famouse errors:
> 
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)


1) folder /sys/devices/system/cpu/cpu0/ is empty.
2) I'm running v2.6.7 kernel or later
3) I have modules loaded
> 
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/freq_table.ko
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/cpufreq_userspace.ko
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/cpufreq_stats.ko
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/cpufreq_powersave.ko
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/cpufreq_ondemand.ko
/lib/modules/2.6.12-9-686/kernel/drivers/cpufreq/cpufreq_conservative.ko

4) I can't find anything in dmesg that sounds like that error.

Please, guys, what can I do?

Thanks in advance

---

### Post by r0ll3r on 2005-11-15
Hi Nano,
please check this thread:
[http://www.ubuntuforums.org/showthread.php?t=86386](http://www.ubuntuforums.org/showthread.php?t=86386)

---

### Post by Nano on 2005-11-15
[QUOTE=r0ll3r]Hi Nano,
please check this thread:
[http://www.ubuntuforums.org/showthread.php?t=86386](http://www.ubuntuforums.org/showthread.php?t=86386)[/QUOTE]

Hi r0ll3r, 
Thanks a lot for your quick reply.
By loading the following modules:
> 
modprobe speedstep-lib
modprobe p4-clockmod
modprobe freq-table

and running 
> 
powernowd


I got the following output:

> 
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 2099Mhz - 2799Mhz (3 steps)


I also did: 
> 
 sudo /etc/init.d/powernowd start
 * Starting powernowd...                                                   [ ok ]


Should it be running now?

Thanks a lot for your quick answer and support.

---

### Post by r0ll3r on 2005-11-15
Yes. That means it is working in 3 steps. Try adding "CPU FREQ applet" to your gnome-panel. (right click on gnome-panel, add applet, scroll down, at the bottom at hardware you will find it). It should visualize your speedstepping. :)

---

### Post by Nano on 2005-11-15
[QUOTE=r0ll3r]Yes. That means it is working in 3 steps. Try adding "CPU FREQ applet" to your gnome-panel. (right click on gnome-panel, add applet, scroll down, at the bottom at hardware you will find it). It should visualize your speedstepping. :)[/QUOTE]

Thanks a lot. I now see it's switching between 2.1, 2.45 and 2.8 Ghz and it doesn't reach more than 80ºC.
Is it possible to make it even cooler?

---

### Post by r0ll3r on 2005-11-15
There's not too much left to do on your laptop :) Except one thing. ACPI in most cases handles the speed of your CPU fan. You can find the fan settings here:
```
/proc/acpi/fan/
```
All settings readable, just do a 'cat *' to see all.

Somehow, on some systems, this is controllable. Also if you check
```
/proc/acpi/thermal/
```
where you can find the temperature settings. Critical temp shouldn't be changed but you can play with passive/active cooling settings. Basically you can set what temperature should the fan start etc. Also other threads are already discussing this here, on ubuntuforums.org

---

### Post by funkenstein on 2005-11-17
note: On my Asus laptop, that last one is /proc/acpi/thermal_zone/ ... FYI :p

---

