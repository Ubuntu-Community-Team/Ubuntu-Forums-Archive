---
title: "Why is my 2.4 GHz CPU clocked at 1.6 GHz?"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by miceagol on 2007-01-25
I have two cores on my Intel Core 2 Duo E6600 processor, each with at clock speed of 2.4 GHz. But lshw reports that these cores are clocked at 1.6 GHz (capacity and size). Can I trust this information? If so, why do my cores have a lower clock speed in Linux than what it shown in both BIOS and Windows?

```

     *-cpu:0
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx f
xsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx f
xsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical

```

---

### Post by mikewhatever on 2007-01-25
Mine looks the same, if it gives any consolation. 
```
cpu:0
          product: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits

```
I'd make an intelligent guess and say, it may be related to frequency scaling. Intel and AMD both scale down CPU frequencies, when the CPU is not active, to reduce heat output and save battery life.

I've just started playing a DVD movie in Totem and ran lshw, note the change
```
cpu:0
          product: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1667MHz
          capacity: 1667MHz
          width: 64 bits

```

---

### Post by harrisony on 2007-01-25
tried this? [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
or sudo apt-get install linux-general

---

### Post by miceagol on 2007-01-26
Todaraba, mikewhatever! Wasn't anything nasty at all. :) 

Wrote a program with an infinite loop. Ran it once: One core changed to 2.4 GHz. Ran another instance of same program: Other core ran at 2.4 GHz. Great!

---

### Post by miceagol on 2007-01-26
> **harrisony said:**
> tried this? [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
or sudo apt-get install linux-general

Don't think I'm in the mood to mess with the kernel at this time, but thanks anyway. ;)

---

