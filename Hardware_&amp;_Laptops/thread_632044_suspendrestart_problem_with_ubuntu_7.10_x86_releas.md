---
title: "suspend/restart problem with ubuntu 7.10 x86 release"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by samarjit on 2007-12-05
Hi all,

I have a laptop of samsung with the model number NP-Q35K001/SHK.
I have install ubuntu 7.10 x86 version and found a problem as mentioned below.

Steps.
1) Booted the machine in Ubuntu admin account.
2) Do SUSPEND( by clicking the power on/off button,placed top right corner).
3) Switch on the machine to wake up from the SUSPENDED mode.
4) Do RESTART( by clicking the power on/off button,placed top right corner).

The machine freezes after sending terminating signal to all. I have to do hard reboot then.

Output of uname -a:
Linux samar-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Output of cat /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2130  @ 1.86GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 1024 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3729.22
clflush size    : 64


processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2130  @ 1.86GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 1024 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3724.18
clflush size    : 64


Any light?

---

### Post by samarjit on 2007-12-09
Please let me know if anyone need some more info.

With regards,
Samarjit

---

