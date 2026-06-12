---
title: "How do I know if SpeedStep is working on Edgy?"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by Levander on 2006-12-29
I've got an Asus P5LD2 and a Core 2 Duo E6300 and I'm running Edgy.  How do I know if Intel's SpeedStep is working?

When I do an lsmod, there is some speedstep_centrino module loaded, but the Core 2 Duo doesn't have anything to do with Centrino does it?

---

### Post by evilghost on 2006-12-29
Install emifreqapplet or cat /proc/cpuinfo

---

### Post by Levander on 2006-12-29
What is /proc/cpuinfo supposed to tell me?  Here is what's in that file:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 255
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips	: 3746.00

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 2048 KB
physical id	: 1
siblings	: 1
core id		: 255
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips	: 3739.80

```

---

### Post by evilghost on 2006-12-29
You're speedstepping:

> 
model name	: Intel(R) Core(TM)2 CPU          6300  @ **1.86GHz**
stepping	: 6
cpu MHz		: **1596.000**


In this case you've throttled down ~300Mhz (1860Mhz to 1596Mhz)

---

### Post by elleP on 2007-01-19
Does anyone know if it is possible to set lower clockspeeds on a E6300? I mean, from 1.8 to 1.6 can't be that power saving.

---

