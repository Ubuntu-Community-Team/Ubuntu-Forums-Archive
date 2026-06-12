---
title: "Dell Pentium 4 HT SMP"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by Mabober on 2006-03-13
All,

I've just installed Breezy on my Dell Dimension. Updated to the SMP kernel, but I still can't see two processors in /proc/cpuinfo. The processor being a Pentium 4 3Gig.

Anyone have any ideas? Do I need additional motherboard drivers?

Cheers
M.

---

### Post by taurus on 2006-03-13
Which kernel version do you use right now?  Type this at the prompt...
```

uname -a

```

---

### Post by Mabober on 2006-03-13
This is the output I get from 'uname -a'.....

Linux Spinal-Tap 2.6.12-10-686-smp #1 SMP Mon Feb 13 12:23:58 UTC 2006 i686 GNU/Linux

This is my /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 4
cpu MHz         : 2994.049
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 5898.24


Cheers,
David

---

