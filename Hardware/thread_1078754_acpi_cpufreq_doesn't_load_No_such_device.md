---
title: "acpi_cpufreq doesn't load: No such device"
date: 2009-02-23
forum: Hardware
---

### Post by robisz on 2009-02-23
I have a Shuttle K48 barebone PC with Core 2 Duo E5200 CPU and I cannot get SpeedStep to work (CPU stays at max). I'm using Ubuntu 8.10.

Any ideas? Thanks in advance. 

$ sudo modprobe acpi_cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping	: 6
cpu MHz		: 2502.575
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5005.15
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping	: 6
cpu MHz		: 2502.575
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5005.14
clflush size	: 64
power management:

---

### Post by robisz on 2009-03-09
Now I'm trying with Ubuntu 8.04 and 2.6.24-23-generic kernel.
Same results: 

$ sudo modprobe acpi_cpufreq

FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-23-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

Any suggestions? Thx

---

