---
title: "Is incorrect my CPUINFO???"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by gohanUbuntu on 2006-03-08
Hello everyone :

I have installed Ubuntu 5.10 on my "HP Pavilion dv1000", where almost everything works perfectly :). I was checking the CPUINFO when I saw this:

gohan$ less /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor **1.60GHz**
stepping        : 8
*********************

**cpu MHz         : 598.675**

*********************
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe
nx est tm2
bogomips        : 1185.79

As I guess my cpu is working under frequency...Am I correct? How could I fix it?

Thanks a lot.

gohanUbuntu
Mexico.

---

### Post by gohanUbuntu on 2006-03-08
I've fixed it!!!

The problem as I saw it was because I used **powernowd**, but I changed it for **cpufreqd** as this [page]("http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavillon_dv1067#Cpu_Frequency_scaling") says.

I hope this can be helpful for someone else!!!

gohanUbuntu
Mexico.

---

