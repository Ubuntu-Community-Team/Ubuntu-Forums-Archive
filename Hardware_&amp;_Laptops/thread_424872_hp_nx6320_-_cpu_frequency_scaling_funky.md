---
title: "hp nx6320 - cpu frequency scaling funky"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by dumbkiwi on 2007-04-27
I've just installed kubuntu feisty on an hp nx6320 laptop.  It's a core duo laptop.  The guidance power monitor in the systray shows that both processors are running at 0 MHz.  

cat /proc/cpuinfo shows:

```
matt@matt-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.674
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3328.96
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.674
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3325.24
clflush size    : 64

```

Can anyone explain why I've got no cpu frequency scaling?  It appears that the powernowd package is installed (if that's of any assistance).

Cheers

Matt

---

### Post by tomasz2006 on 2007-04-27
Hey, I had the same, check out for more info:

[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/102345](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/102345)

---

