---
title: "Only 1 core being utilized on dual-core"
date: 2010-04-30
forum: Hardware
---

### Post by m4778 on 2010-04-30
I just recently installed ubuntu 10.04 on a partition of my harddrive so I am somewhat new to everything.

Basically I was worried when i noticed that when running ubuntu my computer fan was always working its hardest and is extremely loud. so I check the resource usage and one core is always at 100% and the other one is at 2-3%.

this is what is displayed when i do cat/proc/cpuinfo

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
stepping	: 10
cpu MHz		: 2667.000
cache size	: 6144 KB
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
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 5319.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


usually when im on windows both run around 15%ish

are they supposed to be running like this? if so why is my fan so loud

---

### Post by slvr42 on 2010-04-30
I notice this happening when a particular process is hung. It will eat up all the cpu on only one of the cores.  Run top and see what is taking up the most memory and kill it if you can without screwing up something else on the system.

---

### Post by m4778 on 2010-05-01
so ive been researching it and it seems like this is exactly whats happening. but now my problem is that i cant find the gtk-qt-engine package that they are refering too.  could it be called something else? im not seeing it in synaptic 

[http://ubuntuforums.org/showthread.php?t=581390](http://ubuntuforums.org/showthread.php?t=581390)

---

### Post by dino99 on 2010-05-01
sudo dpkg --configure -a

---

### Post by xrono on 2010-05-01
I have similar problem. At least the symptoms for CPU load are the same.
here is my thread with all screenshots.
[http://ubuntuforums.org/showthread.php?p=9209335](http://ubuntuforums.org/showthread.php?p=9209335)

I have Acer Aspire 5738G

---

