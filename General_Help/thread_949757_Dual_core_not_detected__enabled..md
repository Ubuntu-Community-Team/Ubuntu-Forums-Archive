---
title: "Dual core not detected / enabled."
date: 2008-10-16
forum: General Help
---

### Post by gerases on 2008-10-16
Hello everybody, 

I'm running Hardy. And I have an Intel Duo processor. Well, the second core is not visible.

uname -a
Linux office 2.6.24-21-386 #1 Mon Aug 25 16:58:26 UTC 2008 i686 GNU/Linux.

Both the system monitor and /proc/cpuinfo show only one processor.

Here's cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3727.56
clflush size    : 64

Any ideas?

---

### Post by shawnrgr on 2008-10-21
you need to install the SMP kernel, i have dual core and it shows up heres my uname

Linux freedom 2.6.24-21-generic #1 _SMP_ Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

---

