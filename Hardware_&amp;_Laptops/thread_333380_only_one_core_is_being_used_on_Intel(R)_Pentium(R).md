---
title: "only one core is being used on Intel(R) Pentium(R) D Dual Core in Edgy"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by 21_adam_12 on 2007-01-07
hi, i have an Intel(R) Pentium(R) D CPU 3.00GHz Dual Core.
the problem that i have is i don't think both cores in my cpu are being used.
if some one could please help me to get both of the cores working that would be tops. Thanx

here is some info.

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 2400.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6005.08

it only lists one processor!?! 

$ uname -a
Linux UBunTU 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

---

### Post by PilotJLR on 2007-01-07
You're using the 386 kernel... try rebooting, and at the GRUB screen, choose the -generic kernel.

With Edgy -generic kernel is the one required for multiple cores.

---

### Post by 21_adam_12 on 2007-01-08
hey thanx for that it works perfectly now cheers:D

---

