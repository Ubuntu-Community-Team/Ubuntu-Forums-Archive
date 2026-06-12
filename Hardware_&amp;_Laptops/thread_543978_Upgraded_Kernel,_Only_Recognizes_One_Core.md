---
title: "Upgraded Kernel, Only Recognizes One Core"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Mr. Smiley on 2007-09-05
I upgraded my kernel to 2.6.22.6 using this guide:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

For some reason it won't recognize my dual core cpu. Also, it broke my ati drivers which I fixed using envy but when ever I go to system>administration>restricted drivers manager, I get an error:

You need to install the package

  linux-restricted-modules-2.6.22

for this program to work.

I have a dell e1505 laptop with a T7200 core 2 duo. Here is some info:

ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3993.20
clflush size    : 64

ubuntu:~$ cat /proc/cpuinfo | grep '^processor' | wc -l
1

Any help would be very much appreciated.

---

