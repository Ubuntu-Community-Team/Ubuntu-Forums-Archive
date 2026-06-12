---
title: "Core 2 Duo problems"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by refactored on 2007-02-02
Hi, I have a Zepto 6615 laptop with a Core 2 Duo 2GHz which only runs at half speed. I have the SMP generic build and the laptop is not running on batteries. Anyone who have any ideas where to look further?

```

#uname -rv
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006

```

```

#cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4005.04

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4000.35

```

/refactored

---

### Post by Belyel on 2007-02-02
This is not really so much of a problem as it seems.  Ubuntu heavily manages your processor speeds, and will keep them low if nothing needs the power.  I have a Core Duo laptop, too, and I rarely see my procs spike above 1/2 speed.  You can add processor monitors to your panel with the clock by right-clicking and "add to panel..."  I'm assuming you knew that already, but just in case.  You can view both by adding two indicators then adjusting their settings.  Then, try something that eats processor power (type glxgears in a terminal) and see if they go up.  My guess is that they will.

---

### Post by refactored on 2007-02-02
And I guess you didn't even guess... :)

thanks
/refactored

---

