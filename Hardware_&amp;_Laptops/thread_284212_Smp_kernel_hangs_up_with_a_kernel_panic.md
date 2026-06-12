---
title: "Smp kernel hangs up with a kernel panic"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by flapane on 2006-10-25
I've just bought a x2 3800+ but I have the problem I wrote in [http://bugzilla.kernel.org/show_bug.cgi?id=7414](http://bugzilla.kernel.org/show_bug.cgi?id=7414)

Maybe some one has the same problem

---

### Post by Aberrix on 2006-10-25
did you every try the generic kernel?

([link]("http://www.ubuntuforums.org/showthread.php?t=283638"))

---

### Post by flapane on 2006-10-25
sure, I was going to tell you, in the other thread. no way (2.6.17-generic from edgy repos)

---

### Post by flapane on 2006-10-25
it works if I disable ACPI fro the bios, but I need acpi for saving power...

flapane@a64:/etc/init.d$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2565.551
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext
3dnow pni lahf_lm cmp_legacy
bogomips        : 5136.42
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2565.551
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext
3dnow pni lahf_lm cmp_legacy
bogomips        : 5136.42
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

