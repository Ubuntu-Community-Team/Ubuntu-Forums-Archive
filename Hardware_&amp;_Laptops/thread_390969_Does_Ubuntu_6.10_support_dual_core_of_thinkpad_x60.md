---
title: "Does Ubuntu 6.10 support dual core of thinkpad x60s?"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by gnebro on 2007-03-22
I can't understand if my ubuntu 6.10 is recognizing the dual core intel cpu of my Thinkpad x60.

Here is the output of /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           L2400  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3329.59

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           L2400  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3325.12


The output it's quite confusing. I thought that cpu cores was supposed to be 2 instead of 1. It seems to see twice the same cpu. May you help me please?

Thanks a lot,
Lorenzo.

---

### Post by mcduck on 2007-03-22
Yes, it's working. You see CPU 0 and CPU 1, that makes 2 cores :D

---

