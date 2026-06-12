---
title: "Core Duo problem"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by alex686 on 2006-12-27
Hello all!
I have a little problem, searched everywhere here but didn't find any solution.
I have a core duo cpu, but ubuntu recognizes only one core:

```

laptop:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 4007.24

```

My kernel is linux generic...
```

laptop:~$ uname -a
Linux laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

```

Any ideas why my system doesn't recognize both cores? ](*,)

---

### Post by alex686 on 2007-01-06
Problem solved by restoring the default values in BIOS.
It is strange that in my Sony Vaio SZ2XP/C BIOS there is no option for CPU and restoring values to default solved the problem...

---

