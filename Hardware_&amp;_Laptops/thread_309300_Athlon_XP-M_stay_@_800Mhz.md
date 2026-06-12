---
title: "Athlon XP-M stay @ 800Mhz"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by sadako on 2006-11-29
Hi,

First, sorry for my english..

Second :

I have a Asus A7N8X-VM/400 with a Athlon 1600+ with Ubuntu 6.10 (is working very good)
And recently i ahve try to put an Athlon XP-M 2800 on this configuration, but the CPU stay @800Mhz and the CPUfreq doesn't work (the applet on Gnome tell me the CPU is always to max @800Mhz)

Is a Hardware Problem, or can i Reinstall Ubuntu ?

```
sadako@sadako-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) MP 
stepping        : 0
cpu MHz         : 798.883
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid
bogomips        : 1599.83
```

```
sadako@sadako-desktop:~$ sudo powernowd
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

Thanks a lot !

---

### Post by dimonic on 2007-12-29
> **sadako said:**
> Hi,

First, sorry for my english..

Second :

I have a Asus A7N8X-VM/400 with a Athlon 1600+ with Ubuntu 6.10 (is working very good)
And recently i ahve try to put an Athlon XP-M 2800 on this configuration, but the CPU stay @800Mhz and the CPUfreq doesn't work (the applet on Gnome tell me the CPU is always to max @800Mhz)


As the message states, you need to insert a module to control your cpu (hardware specific). The module for your CPU is the powernow-k8 module, which you insert on the fly by running:

# modprobe powernow-k8

You will then need the governor you plan to use, such as "ondemand"

# modprobe cpufreq-ondemand

Then you will be able to control your CPU speed. Take note however, I found your message because I was looking for why my CPU (an Athlon XP-M 2800) locks up sporadically when using power management. Your mileage may vary, your car may not run.

---

### Post by uwishurockedthishxc on 2007-12-29
could be a fsb compatability issue as well

---

