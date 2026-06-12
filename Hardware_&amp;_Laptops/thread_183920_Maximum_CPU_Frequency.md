---
title: "Maximum CPU Frequency"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by Kishore Sundara-Rajan on 2006-05-28
I have p4-clockmod and powernowd loaded and my CPU tops out at 1.5GHz. How do I fix this problem? Here is the output of cat /proc/cpuinfo

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 8
cpu MHz         : 1995.705
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 3994.13

```

Thanks!

---

### Post by s0cket on 2006-05-31
[QUOTE=Kishore Sundara-Rajan]I have p4-clockmod and powernowd loaded and my CPU tops out at 1.5GHz. How do I fix this problem? Here is the output of cat /proc/cpuinfo
Thanks![/QUOTE]

First off you should be using the speedstep_centrino module.  The module p4-clockmod does not regulate voltage scaling... which is 1/2 the point of having a P-M.

Second how are you watching your CPU freq?  Also you need to pike your CPU usage above %80 for at least 5-6 seconds to see it top out.  My Dell 9300 scales it CPU freq beautifully.

---

### Post by Sutekh on 2006-06-05
[quote=Kishore Sundara-Rajan]I have p4-clockmod and powernowd loaded and my CPU tops out at 1.5GHz. How do I fix this problem? Here is the output of cat /proc/cpuinfo

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 8
** cpu MHz         : 1995.705**
...


``` 
Thanks![/quote]
When you posted the cpuinfo your proc was running at 2GHz.

A useful command for keeping an eye on the CPU speed is the **watch** command.  This command will update the output from **cat /proc/cpuinfo** every 2 seconds.
```
watch -n 2 cat /proc/cpuinfo
```

---

