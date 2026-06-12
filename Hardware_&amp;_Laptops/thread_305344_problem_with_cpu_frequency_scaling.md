---
title: "problem with cpu frequency scaling"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by dvd_it on 2006-11-23
I'll post below some "answers" to some commands... the problem is that cpu scaling is not working in powernowd's opinion... I have a centrino laptop. Please help me!

```
davide@ububook:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.40GHz
stepping        : 6
cpu MHz         : 600.144
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 1201.53

```

I've a 1.4GHz processor, but it's working costantly at 600MHz!

```
davide@ububook:~$ sudo powernowd 
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

and

```
davide@ububook:~$ sudo modprobe speedstep-centrino 
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

```


the last thing:
/usr/src/linux-headers-2.6.17-10-generic/drivers/cpufreq/Makefile 

```
# CPUfreq core
obj-$(CONFIG_CPU_FREQ)			+= cpufreq.o
# CPUfreq stats
obj-$(CONFIG_CPU_FREQ_STAT)             += cpufreq_stats.o

# CPUfreq governors 
obj-$(CONFIG_CPU_FREQ_GOV_PERFORMANCE)	+= cpufreq_performance.o
obj-$(CONFIG_CPU_FREQ_GOV_POWERSAVE)	+= cpufreq_powersave.o
obj-$(CONFIG_CPU_FREQ_GOV_USERSPACE)	+= cpufreq_userspace.o
obj-$(CONFIG_CPU_FREQ_GOV_ONDEMAND)	+= cpufreq_ondemand.o
obj-$(CONFIG_CPU_FREQ_GOV_CONSERVATIVE)	+= cpufreq_conservative.o

# CPUfreq cross-arch helpers
obj-$(CONFIG_CPU_FREQ_TABLE)		+= freq_table.o

```

I need an help!
thanks
d

---

### Post by Unicast on 2006-11-23
The solution isn't straight forward I'm afraid!

Have a read of my post here: [http://www.ubuntuforums.org/showpost.php?p=1753304&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1753304&postcount=17)

---

### Post by dvd_it on 2006-11-24
> **Unicast said:**
> The solution isn't straight forward I'm afraid!

Have a read of my post here: [http://www.ubuntuforums.org/showpost.php?p=1753304&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1753304&postcount=17)

ok thanks... I'll read and learn!
I'll give you my answers soon
d

---

