---
title: "Ubuntu underclocking CPU"
date: 2011-04-22
forum: Hardware
---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Hi, im using an Intel Core 2 Quad (Q8400 @ 2.66ghz) and when i use 
cat /proc/cpuinfo all informatino is correct except my clock speeds, heres my output:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2003.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 5408.77
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

This is the same for the 3 other cores aswell :/ Any help will be greatly appreciated :)

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Fixed this :) After browsing around 80 threads, i finally found it was Intel SpeedStep enabled D=

---

