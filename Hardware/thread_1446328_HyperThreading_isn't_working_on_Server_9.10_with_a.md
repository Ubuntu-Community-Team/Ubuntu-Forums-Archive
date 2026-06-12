---
title: "HyperThreading isn't working on Server 9.10 with a P4 HT"
date: 2010-04-03
forum: Hardware
---

### Post by deathbypizza on 2010-04-03
Hi All,
I've seen post after post on getting HT working on Ubuntu, but everything seems to be out-dated. Has anyone got HT working on a P4 with Server 9.10?
I'm running the SMP kernel.

lscpu gives details as follows:
```
Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 2
Stepping:              9
CPU MHz:               2805.981
```/proc/cpuinfo gives details as follows:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 9
cpu MHz        : 2805.981
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips    : 5611.96
clflush size    : 64
power management:
```Any help is appreciated!
Thanks,
DBP

---

