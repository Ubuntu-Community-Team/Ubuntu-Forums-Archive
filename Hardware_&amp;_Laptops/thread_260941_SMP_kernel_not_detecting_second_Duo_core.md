---
title: "SMP kernel not detecting second Duo core"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by martinjco on 2006-09-19
Hi,

I've just installed the latest 686 SMP kernel on a Vaio VGN-SZ2VP, but it is only picking up the first core - /proc/cpuinfo contents below. During POST the BIOS displays "1 CPU with 2 cores", so there's nothing odd going on hardware-wise. The laptop is brand new and before I trashed the Sony Win XP build it was displaying 2 cpus in task manager.

Has anyone got any suggestions? I'm tearing my hair out in a "but it should be SO simple" way here..

Thanks

---

### Post by martinjco on 2006-09-19
Woops, cpuinfo and uname output:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping        : 8
cpu MHz         : 2167.157
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 4342.18


Linux shrek 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

---

