---
title: "AMD 64bit 4000+ Problems"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by scgriffiths2000 on 2007-01-05
Hi,

Just installed 6.10, and my cpu is being recognised as 1000mhz, should be 2500mhz.

In the bios its showing correctly as 2500mhz.

Heres what I get if I run cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Athlon(tm) 64 Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 2043.86


Any ideas?

---

### Post by madmetal on 2007-01-05
well i think it has to do with amd cool n quiet which drops the cpu frequency..
:-k

---

