---
title: "CPU freq low"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by sect2k on 2006-01-19
I have a laptop with Pentium-M 1.6 Mhz cpu. When trying to get cpu freq scaling to work I, which i did, i noticed that the highest avaliable cpu freq is 600Mhz which sounds wrong.

running 
```
sudo lshw -class processor
```

produces this:

```
*-cpu
       description: CPU
       product: Intel(R) Pentium(R) M processor 1.60GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.13.6
       slot: U1
       size: 1600MHz
       capacity: 2400MHz
       width: 32 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2

```

if i run the same command as normal user (sans sudo) I get 

```
*-cpu
       product: Intel(R) Pentium(R) M processor 1.60GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.13.6
       size: 600MHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2

```

notice the size is now 600Mhz and not 1600Mhz!


Any ideas what, if anything is wrong??

---

