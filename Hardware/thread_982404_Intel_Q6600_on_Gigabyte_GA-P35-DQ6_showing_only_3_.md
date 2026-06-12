---
title: "Intel Q6600 on Gigabyte GA-P35-DQ6 showing only 3 cores"
date: 2008-11-14
forum: Hardware
---

### Post by battlecyborg on 2008-11-14
I searched the forum already and the only other occurrence I found was someone complaining a bug in 'top' or system info.

Here is my /proc/cpuinfo.  This is very strange.  Is it possible one of the cores on my CPU is busted?

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping        : 7
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 3
core id         : 0
cpu cores       : 3
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4799.98
clflush size    : 64
power management:
processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping        : 7
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 3
core id         : 3
cpu cores       : 3
apicid          : 3
initial apicid  : 3
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4799.97
clflush size    : 64
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping        : 7
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 3
core id         : 2
cpu cores       : 3
apicid          : 2
initial apicid  : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4799.98
clflush size    : 64
power management:

```

---

### Post by battlecyborg on 2008-11-14
maybe relevant dmesg

```

[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017659] ACPI: Core revision 20080609
[    0.019030] ACPI: Checking initramfs for custom DSDT
[    0.296180] ENABLING IO-APIC IRQs
[    0.296386] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.336123] CPU0: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz stepping 07
[    0.340021] Booting processor 1/3 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4799.97 BogoMIPS (lpj=9599944)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.424601] CPU1: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz stepping 07
[    0.424942] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428107] Booting processor 2/2 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4799.98 BogoMIPS (lpj=9599960)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.520573] CPU2: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz stepping 07
[    0.520915] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.524038] Brought up 3 CPUs
[    0.524086] Total of 3 processors activated (14399.93 BogoMIPS).
[    0.524162] CPU0 attaching sched-domain:
[    0.524164]  domain 0: span 0-2 level CPU
[    0.524166]   groups: 0 1-2
[    0.524171] CPU1 attaching sched-domain:
[    0.524173]  domain 0: span 1-2 level MC
[    0.524175]   groups: 1 2
[    0.524178]   domain 1: span 0-2 level CPU
[    0.524180]    groups: 1-2 0
[    0.524184] CPU2 attaching sched-domain:
[    0.524186]  domain 0: span 1-2 level MC
[    0.524188]   groups: 2 1
[    0.524191]   domain 1: span 0-2 level CPU
[    0.524193]    groups: 1-2 0


```

---

