---
title: "CPU Clocking Problem"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by Tide on 2005-10-01
Hello everyone. I'm new to linux, and since I installed Kubuntu I've been having a problem with my CPU clock speed on my Compaq Presario 2590US. Upon running cat /proc/cpuinfo I am told the following:
```

owner@box:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Genuine Intel(R) CPU 2.30GHz
stepping        : 9
[COLOR=red]cpu MHz         : 1596.512[/COLOR]
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
bogomips        : 3137.53

```
Yet lshw tells me the following: 
```
 
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          version: 15.2.9
          slot: WMT478/NWD
          size: 1600MHz
[COLOR=red]          capacity: 2300MHz[/COLOR]
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
 
``` 

So I ought to be running my CPU at 2.3 ghz, not at 1.6. Does anyone know how I can correct this problem?  Thus far, cpuspeedy has not worked for me, and I'm pretty sure that this problem is not being caused by CPU throttling since I did not have that feature enabled and also due to the fact that that frequency never changes, even when programs are loading.

---

