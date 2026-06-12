---
title: "Intel Speedstep"
date: 2008-07-09
forum: Hardware
---

### Post by Qinjuehang on 2008-07-09
Well, I am having a strange problem here. I am trying to get Intel Speedstep to work on my computer (it works in Vista and I enabled it in BIOS).

Some Info:
```
qinjuehang@UbuntuStudio:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 4 scalable units:  -- 1 'CPU' per scalable unit
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
qinjuehang@UbuntuStudio:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
qinjuehang@UbuntuStudio:~$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-19-rt/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
qinjuehang@UbuntuStudio:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
stepping	: 7
cpu MHz		: 3075.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6152.90
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
stepping	: 7
cpu MHz		: 3075.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6149.83
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
stepping	: 7
cpu MHz		: 3075.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6149.83
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
stepping	: 7
cpu MHz		: 3075.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6149.78
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

So...anyone has any idea what's going on? Help would be greatly appreciated, I've been at it for over 2 hours :lolflag:

My Motherboard is a GA-EP35-DS3L, and I built my computer myself, it that is of any help.

---

### Post by synchris on 2008-08-17
You must compile the kernel with:
> X86_ACPI_CPUFREQ=m
CPU_FREQ=y


and after:
> modprobe acpi-cpufreq

---

### Post by Master Chief on 2008-08-17
Have you checked your BIOS settings, because it looks like you forgot to enable Intel's SpeedStep in the BIOS.

This is what sudo powernowd should look like:

powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 4 'CPUs' per scalable unit
powernowd:   cpu0: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu1: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu2: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu3: 1998Mhz - 2497Mhz (2 steps)

See section 2-4 "Advanced BIOS Features" in your manual. The setting is called: "CPU EIST Function":

"[I]Enables or disables Enhanced Intel SpeedStep Technology (EIST). Depending on CPU loading,
Intel ® EIST technology can dynamically and effectively lower the CPU voltage and core frequency
to decrease average power consumption and heat production. (Default: Enabled)[/I]"

p.s. I do happen to have the same CPU in one of my many development systems and it "just worked" out of the box!

---

### Post by synchris on 2008-08-17
> **Master Chief said:**
> Have you checked your BIOS settings, because it looks like you forgot to enable Intel's SpeedStep in the BIOS.

This is what sudo powernowd should look like:

powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 4 'CPUs' per scalable unit
powernowd:   cpu0: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu1: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu2: 1998Mhz - 2497Mhz (2 steps)
powernowd:   cpu3: 1998Mhz - 2497Mhz (2 steps)

See section 2-4 "Advanced BIOS Features" in your manual. The setting is called: "CPU EIST Function":

"[I]Enables or disables Enhanced Intel SpeedStep Technology (EIST). Depending on CPU loading,
Intel ® EIST technology can dynamically and effectively lower the CPU voltage and core frequency
to decrease average power consumption and heat production. (Default: Enabled)[/I]"

p.s. I do happen to have the same CPU in one of my many development systems and it "just worked" out of the box!

if u check the code box you will see this:
> 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-19-rt/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

---

### Post by Master Chief on 2008-08-18
Oh dear. I wonder why I skipped the first line of the OP, who even wrote that he enabled it in his BIOS, and that it works with his Vista installation. 

I guess that I skipped it remembered my own error because I recently ran into this myself (setting up a new box for my youngest son).

Yes, it is a no-go without the acpi-cpufreq.ko module, but that is part of a normal -generic kernel installation which I use.

Back to my wakeup cappuccino...and thanks synchris for being awake while I wasn't!

---

