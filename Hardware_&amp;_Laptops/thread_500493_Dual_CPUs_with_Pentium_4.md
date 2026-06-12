---
title: "Dual CPUs with Pentium 4?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by mal on 2007-07-13
Just out curiosity, does anyone know why Ubuntu finds 2 CPUs when running on a Pentium 4 machine.

I have only recently noticed that dmesg shows CPU0 and CPU1 being found and lists the message "Brought up 2 CPUs".  Also the system monitor shows 2 traces on the CPU History trend.

Some dmesg outputs that have been posted in the forums also show that 2 CPUs have been found.

The only possibility that I can think of is that the FPU is seen as a second processor.

Any ideas?

Mal

---

### Post by duydaniel on 2007-07-13
> **mal said:**
> Just out curiosity, does anyone know why Ubuntu finds 2 CPUs when running on a Pentium 4 machine.

I have only recently noticed that dmesg shows CPU0 and CPU1 being found and lists the message "Brought up 2 CPUs".  Also the system monitor shows 2 traces on the CPU History trend.

Some dmesg outputs that have been posted in the forums also show that 2 CPUs have been found.

The only possibility that I can think of is that the FPU is seen as a second processor.

Any ideas?

Mal

Is it Hyper Threading Pentium 4? Windows XP sees Pentium 4 HT 2 CPUs too

---

### Post by mal on 2007-07-14
The processor is a Pentium 4 530J, which does apparently have Hyper-Threading technology, so I guess Linux also sees it as having 2 CPUs.  I still don't understand why.

Mal

---

### Post by ErusGuleilmus on 2007-07-14
I’m not really sure, but I think that it is because while there is only one physical processor, there are two virtual processors. I think this make the processor handle threads better.

---

### Post by Rui Pais on 2007-07-14
yes it's the HT (Hyper Threading) technology that allow P4 to work as 2 cpu (kinda... i believe they make more heat then productivity ;))

check with
```
uname -a
```
if it says SMP on name your kernel is using SMP to simulate 2 cpus. If you load the -386 Ubuntu kernel it wont have SMP and your cpu will be detected as a single kernel (some people prefer that way, cause they have performance issues and other bad behavior from SMP/HT)

---

### Post by ~~Tito~~ on 2007-07-14
Mine shows as 3.0ghz, 3.0ghz even in windows. Its not HT its just a regular Pentium 4. Maybe it is 2 processors? I've been wondering that since I bought it, I thought mine was cool when I bought it.

---

### Post by Rui Pais on 2007-07-14
> **~~Tito~~ said:**
> Mine shows as 3.0ghz, 3.0ghz even in windows. Its not HT its just a regular Pentium 4.  
well, regular P4 usually have HT. I think only old models don't have it, and 3Gh is not an old model...
> Maybe it is 2 processors? I've been wondering that since I bought it, I thought mine was cool when I bought it.
You can check in Linux by type:
```
 cat /proc/cpuinfo
```
and
```
lshw -C cpu
```

---

### Post by duydaniel on 2007-07-14
I believe there is no real "Dual Pentium 4". It should be Hyper Threading, which can be enable or disable in your Bios Setting. This tech has pro and cons...

Actually, I believe, the "Dual Pentium 4" was named Pentium D. Then Intel redesigned the whole architechture to produce Core 2 Duo... something like that.

---

### Post by ~~Tito~~ on 2007-07-14
Yea its a dual Pentium 4!!



```
tito@TITOS-LAPTOP:~$  cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6003.52
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6000.68
clflush size    : 64
```

```
tito@TITOS-LAPTOP:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Pentium(R) 4 CPU 3.00GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 15.4.1
       serial: 0000-0F41-0000-0000-0000-0000
       size: 18EHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 32 bits
          capabilities: logical
tito@TITOS-LAPTOP:~$ 
```

---

### Post by duydaniel on 2007-07-14
> **~~Tito~~ said:**
> Yea its a dual Pentium 4!!



```
tito@TITOS-LAPTOP:~$  cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6003.52
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6000.68
clflush size    : 64
```

```
tito@TITOS-LAPTOP:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Pentium(R) 4 CPU 3.00GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 15.4.1
       serial: 0000-0F41-0000-0000-0000-0000
       size: 18EHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 32 bits
          capabilities: logical
tito@TITOS-LAPTOP:~$ 
```

It would be P4 HT... do you see ```
cpu cores       : 1
``` on the list?
Try on Windows and run CPUID or Sisoft Sandra to see? In Linux... I am nooooob :KS

---

### Post by Rui Pais on 2007-07-15
> **~~Tito~~ said:**
> Yea its a dual Pentium 4!!



```
tito@TITOS-LAPTOP:~$  cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
**physical id     : 0**
siblings        : 2
**core id         : 0**
**cpu cores       : 1**
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6003.52
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3000.317
cache size      : 1024 KB
**physical id     : 0**
siblings        : 2
**core id         : 0**
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 6000.68
clflush size    : 64
```
...

Yes, its a single core that HT/SMP make acts like 2. They are listed as logicalcpus, not core cpus, at:           physical id: **1**.1 and           physical id: **1**.2.
And check it at cpuinfo too:
> cpu cores       : 1 and both processors:
>  core id         : 0

As a comparison, mine is a dual core, and the output of
```
cat /proc/cpuinfo | grep "core id"
```
is:
> core id         : 0
core id         : 1

---

### Post by duydaniel on 2007-07-15
> **Rui Pais said:**
> Yes, its a single core that HT/SMP make acts like 2. They are listed as logicalcpus, not core cpus, at:           physical id: **1**.1 and           physical id: **1**.2.
And check it at cpuinfo too:
 and both processors:


As a comparison, mine is a dual core, and the output of
```
cat /proc/cpuinfo | grep "core id"
```
is:

So be careful to deal with some tricky vendors!!! Especially, Ebay... :)

---

### Post by ~~Tito~~ on 2007-07-16
I said it is not HT. Just a regular Pentium 4.

---

### Post by Rui Pais on 2007-07-16
> **~~Tito~~ said:**
> I said it is not HT. Just a regular Pentium 4.

All *regular* Pentium 4 have (had) HT:
[http://www.intel.com/products/processor/pentium4/specs.htm](http://www.intel.com/products/processor/pentium4/specs.htm)
[http://support.intel.com/products/processor_number/chart/pentium4.htm](http://support.intel.com/products/processor_number/chart/pentium4.htm)

---

### Post by ~~Tito~~ on 2007-07-17
Its the older version not the newer one. The sticker isn't that design.

---

### Post by zgornel on 2007-07-17
The Pentium 4 530J has HT enabled.

---

