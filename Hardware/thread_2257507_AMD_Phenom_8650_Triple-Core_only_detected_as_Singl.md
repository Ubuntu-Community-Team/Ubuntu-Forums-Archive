---
title: "AMD Phenom 8650 Triple-Core only detected as Single"
date: 2014-12-20
forum: Hardware
---

### Post by greg67 on 2014-12-20
Been running my computer for a while and noticed its only detecting a single core.  I've seen **some** threads that re-installing fixed, but is there way to utilize my other cores without re-installing?  I really don't want to go through all the work of re-configuring if might not work.
[B]
cat /proc/cpuinfo[/B]
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : AMD Phenom(tm) 8650 Triple-Core Processor
stepping        : 3
microcode       : 0x1000095
cpu MHz         : 2300.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips        : 4600.03
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

**uname -a**
```
Linux server 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by greg67 on 2014-12-20
Fixed my problem, enabling** ACPI 2.0 Support** and **ACPI APIC Support** in BIOS did the trick.

---

