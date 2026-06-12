---
title: "MT-40 CPU upgrade and ACPI / CPU throttling issue"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by mysql101 on 2005-12-12
I've got an issue with ubuntu on my laptop. The problem is that I upgraded my laptop from a MT-30 (1.6ghz) to a MT-40 (2.2ghz) and cpu throttling no longer works. powernowd in dmsg says it's not supported.

> root@turion64:/usr/src/linux# dmesg | grep powernow
[17179620.876000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179620.876000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects

I tried to compile 2.6.14 (2.6.13 includes amd's powernowd-k8 code) and still no luck. 

> root@turion64:/usr/src/linux# uname -a
Linux turion64 2.6.14.2averatec #1 Fri Dec 9 16:10:56 EST 2005 i686 GNU/Linux


root@turion64:/usr/src/linux# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology MT-40
stepping        : 2
cpu MHz         : 2195.507
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4393.16

root@turion64:/usr/src/linux# /usr/share/powernowd/cpufreq-detect.sh
root@turion64:/usr/src/linux#


root@turion64:/usr/src/linux# /sbin/modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device


root@turion64:/usr/src/linux# modprobe -l | grep powernow
/lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
/lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko
/lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k6.ko


root@turion64:/usr/src/linux# powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory


Anyone else know about this issue or have a workaround?

TIA

---

### Post by mysql101 on 2005-12-15
The company who makes the laptop doesn't want to help me. The amibios.com site, as well as Uniwill (company who makes the mobo) both have nothing on their sites in regards to bios updates.

Is there a solution short of a full bios update?

---

### Post by mysql101 on 2005-12-22
*cries*

---

### Post by .t. on 2005-12-23
Sorry mate, but do you actually *need* CPU throttling? Why not just use the AMD version of SpeedStep; that's more supported, so it should work just as well.

---

### Post by fordfan753 on 2005-12-23
From cpuinfo you can see that there are two steppings, so the kernel is reading the processor fine (if, of course, it's only meant to have two speeds).

Have you tried cpufreqd with this processor?

---

### Post by fordfan753 on 2005-12-23
Have you tried:

```
sudo insmod /lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
```

??

---

### Post by mysql101 on 2005-12-23
[QUOTE=fordfan753]From cpuinfo you can see that there are two steppings, so the kernel is reading the processor fine (if, of course, it's only meant to have two speeds).

Have you tried cpufreqd with this processor?[/QUOTE]

The Turions should have a 800mhz setting, and a full speed setting (At least that was what the 1.6ghz cpu had).

As you can see from the ACPI files, throttling is not a possible option currently:

root@turion64:/proc/acpi/processor/CPU1# cat info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no


root@turion64:/proc/acpi/processor/CPU1# cat throttling
<not supported>

---

### Post by mysql101 on 2005-12-23
[QUOTE=fordfan753]Have you tried:

```
sudo insmod /lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
```

??[/QUOTE]

root@turion64:/proc/acpi/processor/CPU1# insmod /lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
insmod: error inserting '/lib/modules/2.6.14.2averatec/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko': -1 Invalid module format



I've tried cpufreqd and a few others, but nothing will work simply because the kernel doesn't appear to see the cpu as being capable of throttling.


Without throttling, my little laptop goes into the 140 degree range. I need to run a laptop cooler to keep it around 125. If the laptop throttled, I wouldn't need the cooler, and it would run around 115 degrees (As it does in windows with exactly the same hardware configuration - dual booting)

---

### Post by mysql101 on 2006-01-11
the company who made the laptop wrote back to me about bios updates saying they don't support cpu upgrades and they aren't going to tell me any information about the system.

---

