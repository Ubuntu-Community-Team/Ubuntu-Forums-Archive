---
title: "Second CPU missing of Dual Core"
date: 2010-12-06
forum: Hardware
---

### Post by zardoz on 2010-12-06
Hello.

My Lenovo T61 has a dual core CPU. I just noticed that under Ubuntu 10.10 just only one CPU is recognized. I know that once both CPUs worked. Not sure since when the second CPU is missing. Maybe since the last kernel update.
Currently I am using linux-image-2.6.35-23-generic (for x86_64).

What can I do to enable the second CPU again?

Here the ouput of /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips	: 4189.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

Any help is welcome. I really need that CPU power for my work here.

Thanks,
Kai

---

### Post by zardoz on 2010-12-06
The current Nvidia driver (the one from Nvidia itself "NVIDIA-Linux-x86_64-260.19.21") leads to those problems. After uninstalling it and installing the one of Ubuntu again the second CPU shows up again. Not sure why that driver has this problem.

---

