---
title: "Edgy/AMD64: dmesg errors-should I care"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by mibadt on 2006-11-07
Hi,

I have a fresh installed Edgy Kubuntu 32b, running on an AMD  Athalon 64b.
IN order to utilize my CPU, yet maintain 32b, I recompiled the latests kernel (2.6.18.2) for a K8 type processor.

Upon reboot, everything seems fine except for the following dmesg errors?
Should I care? How do I fix those?

TIA

----------copy of /proc/cpuinfo--------------
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm ts fid vid ttp tm stc
bogomips        : 2010.88



---------end--------------------------------------

--------copy of dmesg error------------------------
powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   36.032939] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[   36.032942] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[   36.032945] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[   36.032948] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[   36.032951] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   36.032953] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
--------------end-------------------------------------------------

---

### Post by mibadt on 2006-11-12
Problem solved by installing Linux drivers from AMD's site.

---

