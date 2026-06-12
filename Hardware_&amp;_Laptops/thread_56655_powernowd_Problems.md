---
title: "powernowd Problems"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by Dragonmantank on 2005-08-13
I've installed Ubuntu on my Compaq laptop with a Mobile Athlon, but I cannot get Ubuntu to allow me to scale the CPU frequency. I know it does work in general, as Windows and VidaLinux would allow me too. When I add in the Gnome applet it just says "--- ?", and when I try to run powernowd I get this:

```
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
```

How/what should I check to get this to work? I'm not sure how to check the modules loaded into the kernel.

---

### Post by PeP on 2005-08-13
[QUOTE=Dragonmantank]
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)l.[/QUOTE]

you are running a 2.6 kernel,to know your kernel version:
```
uname -r 
```

to check mounted volumes look in mtab,to have a selective output use grep:
```
cat /etc/mtab |grep sys

```

to check if a module is loaded with selective output:
```
 lsmod |grep cpufreq

```

to check dmesg for errors (messages from the kernel) with selective output:
```
 dmesg |grep cpu

```

---

### Post by Dragonmantank on 2005-08-13
OK, I ran the commands above and got this:

uname -r
```
2.6.10-5-386
```
cat /etc/mtab |grep sys
```
sysfs /sys sysfs rw 0 0
```
lsmod |grep cpufreq
```
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
```
dmesg |grep cpu
```
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
```

---

### Post by neoraptor on 2005-08-20
I have exactly the same problem.
Does anyone have a solution?
I have try cpufreqd and cpudyn, but it doesn't work.

---

### Post by mo_x on 2005-08-20
I think you must have the powernow_k8 module loaded. Check with the following command:
```
sudo lsmod | grep powernow
```
It is not working with the Ubuntu kernel for my CPU, an AMD64 3000+ Venice. I see the following error when I run dmesg:
```
powernow-k8: transition frequency failed
powernow-k8: vid trans failed, vid 0x3, curr 0x4
```
I think this is solved in newer kernels.

---

