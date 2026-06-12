---
title: "Macbook 5,2 use both cores"
date: 2011-03-15
forum: Hardware
---

### Post by FuzZy2006 on 2011-03-15
I have just happily managed to install Ubuntu 10.10 on my Macbook 5,2. I have used the alternate amd64+mac image. I am booting with acpi=off. 

Two questions: 
Why am I not able to use both cores of the processor? 
Why does the system recognize only 3.6 of the 4gb of memory? 

This is the result of cat /proc/cpuinfo:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping	: 10
cpu MHz		: 1990.204
cache size	: 3072 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 3980.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Thank you.

---

### Post by khelben1979 on 2011-03-23
The answer is that you need to install the 64 bit version of Ubuntu. It includes a Linux kernel for 64 bit CPU:s and you also need to make sure you get a [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing") Linux kernel. (RECOMMENDED)

You can use the 32 bit version of Ubuntu, but then you need a [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") kernel so all your RAM memory can be used.

---

