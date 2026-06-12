---
title: "Dual Core in Ubuntu Feisty 64??"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ghandi69_ on 2007-04-23
AMD Opteron 165 Denmark 1.8GHz 2 x 1MB L2 Cache Socket 939 Dual Core Processor

I am currently using an AMD 3200+

I was looking into purchasing this processor, I haven't made any major hardware changes before under ubuntu, and I was wondering if there was anything I need to worry about when making the switch??

---

### Post by Fuzzgun on 2007-04-28
I'm running with an Opteron 180 (Toledo) & Asus A8V deluxe mobo and there haven't been any problems.



fuzzgun@fuzzgun-linux:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 180
stepping        : 2
cpu MHz         : 2403.150
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4811.78
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 180
stepping        : 2
cpu MHz         : 2403.150
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4806.49
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

