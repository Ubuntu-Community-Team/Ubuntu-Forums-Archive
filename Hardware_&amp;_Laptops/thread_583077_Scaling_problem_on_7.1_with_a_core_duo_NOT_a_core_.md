---
title: "Scaling problem on 7.1 with a core duo NOT a core 2 duo"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by joseness on 2007-10-20
Hi everybody

I have a Intel core duo (T2500) in an uniwill laptop, but i can't change CPU speed, it recognizes badly the processor, in /sys/devices/system/cpu/  there is very few info. (i'll attack ls -lahr) and cpu info.

All the time is at max frec, (2.0 in this processor). ¿any suggestion? it's a fresh non-beta installation of 7.10 (so the control should be provided by powernowd) at least that package is installed by default. if i try to start it i get:


root@jose-laptop:/proc# powernowd 
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
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

i manually load  cpufreq-userspace successfully but when i try to load module cpufreq i get:

root@jose-laptop:/proc# modprobe cpufreq
FATAL: Module cpufreq not found.

---

### Post by [knap] on 2007-10-20
What is the content of

```
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

?

What happens if you do

```
sudo cpufreq-selector -g ondemand
```

?

And

```
sudo cpufreq-selector -c 0 -f 1000000 && sudo cpufreq-selector -c 1 -f 1000000
```

?

---

### Post by joseness on 2007-10-20
Hi!

Thanks for answering so fast...

that's what i was trying to say... there is no that file... the system is not detecting the processor capabilities:

root@jose-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: No existe el fichero ó directorio (file not found)
root@jose-laptop:~# sudo cpufreq-selector -g ondemand
No cpufreq support
root@jose-laptop:~# sudo cpufreq-selector -c 0 -f 1000000 && sudo cpufreq-selector -c 1 -f 1000000
No cpufreq support


Have a loot at attached file the ls command on /sys/devides/sys...

root@jose-laptop:/sys/devices/system/cpu/cpu0# ls -R ./
./:
cache  crash_notes  topology

./cache:
index0  index1  index2

./cache/index0:
coherency_line_size  number_of_sets           shared_cpu_map  type
level                physical_line_partition  size            ways_of_associativity

./cache/index1:
coherency_line_size  number_of_sets           shared_cpu_map  type
level                physical_line_partition  size            ways_of_associativity

./cache/index2:
coherency_line_size  number_of_sets           shared_cpu_map  type
level                physical_line_partition  size            ways_of_associativity

./topology:
core_id  core_siblings  physical_package_id  thread_siblings

---

### Post by Oxymeron on 2007-10-20
make sure, you have cpufreqd and cpufrequtils installed.

apt-get install cpufreqd cpufrequtils

---

### Post by joseness on 2007-10-20
Hi, 

I have powernod intalled (by default) which says in description:
[I]control cpu speed and voltage using 2.6 kernel interface 
This simple client controls CPU speed and voltage using the sysfs interface
to the CPUFreq driver in v2.6 Linux kernels.  It does not depend on APM or
ACPI, and it doesn't try to do anything other than control the CPU.

The name is somewhat misleading, as any CPUfreq capable processor will work,
not just those from AMD.  However, it works better on CPUs that support more
than two speed steps, like those with AMD's PowerNow! or Intel's Pentium M
series.

This daemon _is less complicated than cpufreqd or cpudyn_, at the cost of
absolutely depending on a 2.6 kernel with the userspace governor and sysfs
support enabled.[/I]

As i understand powernowd replaces cpufreqd,
in fact if i try to install cpufreqd, **synaptys says that i must uninstall powernowd**
 are yo sure that i have to (should) install it?
I have cpufrequtils installed.

Than you all

---

