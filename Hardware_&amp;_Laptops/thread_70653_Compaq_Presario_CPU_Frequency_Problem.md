---
title: "Compaq Presario CPU Frequency Problem"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by Tide on 2005-09-30
Hello everyone.  I'm new to linux, and since I installed Kubuntu I've been having a problem with my CPU clock speed on my Compaq Presario 2590US.  Upon running KInfoCenter I am told that my CPU is clocked at 1596.512 mhz.  I am lead to believe that this is not due to CPU throttling since I did not have that feature enabled, and also due to the fact that that frequency never changes, even when programs are loading.  However, lshw tells me the following:
```

*-cpu
description: CPU
product: Genuine Intel(R) CPU 2.30GHz
vendor: Intel Corp.
physical id: 4
version: 15.2.9
slot: WMT478/NWD
size: 1600MHz
capacity: 2300MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep
mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid
xtpr

```
So I know that I ought to be running my CPU at 2.3 ghz, not at 1.6.  Does anyone know how I should correct this problem (the program cpuspeedy has not worked for me)?

---

