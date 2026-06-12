---
title: "CPU speed misrepresented on Gateway 450SX4"
date: 2008-08-14
forum: Hardware
---

### Post by ERIC H on 2008-08-14
Recently got this laptop for free and am diving back into using linux. Specs are as follows for this laptop:

1.60GHZ Pentium 4 Mobile
256MB PC1600 DDR
20GB HDD

BIOS states that is in fact the correct cpu speed, but does cat /proc/cpuinfo does  not:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz
stepping	: 4
**cpu MHz		: 1200.000**
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
bogomips	: 2395.38
clflush size	: 64

```

Conky is also turning up the same results. I'm currently dual-booting with XP pro and windows reports CPU speed correctly. I just installed xubuntu 8.04 yesterday and have finished updating through Synaptic this morning. This is in fact when I noticed the discrepency. Can't say if it was like this before the update.

This would go along with my assumption that something was awry as the system seems to be operating much more sluggish in linux than in windows. I also pressume that can be the little amount of RAM I've inherited but I intend to remedy that in the near future.

Anyway, what can I do?

---

