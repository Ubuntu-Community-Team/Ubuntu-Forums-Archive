---
title: "Frequency scaling broken after Edgy upgrade (Pentium M)"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by uBo on 2006-11-24
Hi,

I just upgraded from my beautifully working Dapper to Edgy, and the upgrade was sweet, no problems at all. Very nice.

Apart from one.

I have a Toshiba Satellite A105 with a Pentium M 1.73Mhz processor and use it quite often on battery.

The frequency scaling of the processor got broke. It was working very well under Dapper. At least it is fixed at the maximum (that is what the frequency scaling monitor tells me after giving an error message that my hardware is either misconfigured or does not support frequency scaling).

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.73GHz
stepping        : 8
cpu MHz         : 1729.489
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 3463.50
```

and 

```
$ sudo powernowd
Password:
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
please email the author: clemej@alum.rpi.edu
```

Anyway I found this bug on Launchpad:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014")

but it seems to be a different one because I had no problems in Dapper with the old kernel.

The last but one poster in this bug has the same problem as me, but I cannot understand his solution.\

Please help me, I need my battery time. If this is solved, my positive Ubuntu experience will be cemented, especially after the smooth upgrade

Thanks!

---

### Post by uBo on 2006-11-25
just wanted to inform that this is a -386 kernel specific bug.

i installed the -generic kernel and now it is working fine.

---

### Post by kaurman on 2006-11-25
I am using generic kernel, but cpu scaling is still broken

---

### Post by WhiskoKid on 2006-11-26
test.  sorry

---

### Post by uBo on 2006-12-14
just short update on the issue.

it is not solved the right way yet. here is the 
[launchpad bug]("https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66812")

anyway, one solution is to use the -generic instead of the default -386 kernel. you can install it from synaptic and then select it from grub at startup.

---

