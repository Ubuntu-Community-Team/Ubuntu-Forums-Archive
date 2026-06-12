---
title: "Hyperthreading"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by duffydack on 2005-09-07
I have used apt-get install linux-686-smp to install and add the kernel to my grub boot menu, then i added ht=on to boot to enable hyperthreading.  I am just curious to know wether my /proc/cpuinfo looks correct? (Took me Ages to get HT working!!)
--
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3193.419
cache size      : 1024 KB
physical id     : 0
siblings        : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor $
bogomips        : 6324.22

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3193.419
cache size      : 1024 KB
physical id     : 0
siblings        : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor $
bogomips        : 6373.37
--

Shouldnt there be just 1 Physical processor with "siblings=2" or is this correct..

---

