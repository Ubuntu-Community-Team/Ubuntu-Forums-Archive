---
title: "core2duo - cpu cores   :1"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by mikewhatever on 2007-01-07
Can someone please confirm both cores of the CPU are recognized.
cat /proc/cpuinfo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
[COLOR="Red"]cpu cores       : 1[/COLOR]
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.81

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
[COLOR="Red"]cpu cores       : 1[/COLOR]
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3325.32

```

I am unhappy with two lines saying [COLOR="Red"]cpu cores   :1[/COLOR], other then that it's correct.
I should mention, that I've been trying to search the forums for this info, but found none. I have Edgy installed:

uname -a
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

---

### Post by melancholeric on 2007-01-07
but according to that it looks like you have two processors.

---

### Post by mikewhatever on 2007-01-07
Thanks for such a quick reply.
I have to say, I'm getting confused. If there are two, why doesn't it say [COLOR="Red"]cpu cores   :2[/COLOR]?

---

### Post by melancholeric on 2007-01-07
Two processors, each of them with one core.

edit: if it said "cpu cores:2" for both you'd have 4 cores altogether.

---

### Post by mikewhatever on 2007-01-07
prossesor :0, prossesor :1, of cause!:-D 

A load's of my shoulders. Thanks melancholeric.

---

