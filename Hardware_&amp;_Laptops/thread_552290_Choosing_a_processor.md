---
title: "Choosing a processor"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by 315234 on 2007-09-16
I am not sure if this is the correct place to post this; apologies if I have erred.

I am running an AMD64 processor at the moment, but have finally gotten fed up of the general lack of support for this architecture. I am looking into buying a new laptop, however, since the processor world moved away from simple cache and clock-speed I (ashamedly) admit I have no idea what to buy. I would like the following:

32bit architecture.
Real multithreading (i.e. dual core)
Reasonable clock speed and cache.

Can anyone make a recommendation? Or even a brief summary of the features of the various processor "families" on the market?

Thanks in advance for any tips.

---

### Post by Linicks on 2007-09-16
I have a dell Inspiron 6400 with the Intel dual core 1.73 CPU.

Intersting info from /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3461.86
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3458.12
clflush size    : 64


So it looks like the core runs at the advertised speed but you have two (obviously) lesser processors running in parallel.

Anyhow, this machine is very fast (2GB ram helps), so I would say that dual core is pretty good.

Nick

---

### Post by 315234 on 2007-09-16
So does that mean that you effectively have two 800MHz processors? And are they 64bit or 32?

---

### Post by Linicks on 2007-09-16
These are 32bit.  Dual core _is_ two processors in sync, and GNU/Linux does indeed show two 800Mhz 'cores'.  I guess with the parallel setup, the extra speed (1773 - 1600) comes from that and the CPU[s] cache.

[http://www.intel.com/products/processor_number/chart/coreduo.htm](http://www.intel.com/products/processor_number/chart/coreduo.htm)

[http://www.intel.com/products/processor_number/flash/demo.html](http://www.intel.com/products/processor_number/flash/demo.html)

It is damn fast anyway.

Nick

---

### Post by Syke on 2007-09-17
My favorite processor with a nice balance of price and performance is the Intel Core 2 Duo T7300. The key specs are:

* Dual Cores - two full CPUs.
* 2 GHz clock speed.
* 800 MHz front side bus.
* 4 MB L2 cache.
* 32-bit and 64-bit architecture.
* Reasonable price.

Now, when you do something like "cat /proc/cpuinfo" on a processor like this and it shows up as "cpu MHz         : 600.000" what you're really seeing is the Intel SpeedStep in action - the clockspeed is lowered when idle to reduce power usage. Then when you start working the cpu, it increases the clock speed up to 2000 MHz.

If you have a few more dollars to spend, the T7700 cranks the clock speed up 25% to 2.4 GHz. That's pretty much top of the line for laptops.

---

### Post by Linicks on 2007-09-17
> **Syke said:**
> 

Now, when you do something like "cat /proc/cpuinfo" on a processor like this and it shows up as "cpu MHz         : 600.000" what you're really seeing is the Intel SpeedStep in action - the clockspeed is lowered when idle to reduce power usage. Then when you start working the cpu, it increases the clock speed up to 2000 MHz.



Ummm, dead right - I learnt something there.  here is the same with the machine loaded (running glxgears):

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping        : 12
cpu MHz         : 1733.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3461.94
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping        : 12
cpu MHz         : 1733.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3458.12
clflush size    : 64


Nick

---

### Post by Czar on 2007-09-17
Go w/ Intel Core 2 Dual.  The E6*50 set even features 1333 FSB (dunno about laptop support.)

TBH, it doesn't matter x86 Vs. x86_64 CPU as nearly every chip today is x86_64 enabled.  Just install a x84 distro and wait for 64bit distros to mature.

> **Linicks said:**
> Ummm, dead right - I learnt something there.  here is the same with the machine loaded (running glxgears)

Yeah, Ubuntu and the cpu scale modules are WONDERFUL, yet the OC ability is shait.  

[http://ubuntuforums.org/showthread.php?t=551749](http://ubuntuforums.org/showthread.php?t=551749)

---

### Post by 315234 on 2007-09-27
Thanks to everyone. I eventually bought a laptop with Intel Core Duo (I couldn't stand the thought of running a 32 bit OS on a 64 bit machine...) and I am very happy with it. The model is a T2350.

cat /proc/cpuinfo: (without speedstep)
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
stepping        : 12
cpu MHz         : 1867.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
stant_tsc pni monitor est tm2 xtpr
bogomips        : 3729.32

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
stepping        : 12
cpu MHz         : 1867.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
stant_tsc pni monitor est tm2 xtpr
bogomips        : 3724.19

```

Thanks again!

---

