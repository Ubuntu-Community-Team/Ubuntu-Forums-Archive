---
title: "Thinkpad T30: CPU running slow"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by mority on 2006-06-16
I have Ubuntu 6.06 running on a Thinkpad T30. I noticed that the CPU is constantly running with 1200 MHz although it is a 1800 MHz CPU no matter whether it is running on battery or not.

Here's some output from my notebook:
```

root@ash:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
stepping        : 7
cpu MHz         : 1199.234
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 2399.76

```

I am able to set the frequency manually:
```

root@ash:~# cpufreq-selector -f 1800000
root@ash:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
stepping        : 7
cpu MHz         : 1798.851
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 3599.65

```

But I don't know what that implies. And of course I would like to have it adjust the frequency automatically (1800 MHz on AC power and 1200 MHz on battery).

Could anyone point me to some documentation or where to look to solve this?

---

### Post by compmodder26 on 2006-06-16
This [post]("http://www.ubuntuforums.org/showpost.php?p=1118239&postcount=3") shows how I control my cpu frequency.

---

### Post by mority on 2006-06-18
[QUOTE=compmodder26]This [post]("http://www.ubuntuforums.org/showpost.php?p=1118239&postcount=3") shows how I control my cpu frequency.[/QUOTE]

Thank you. I answered there...

---

