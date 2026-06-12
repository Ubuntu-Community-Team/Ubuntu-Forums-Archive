---
title: "powertop [C0 nearly 100% all the time]"
date: 2011-02-02
forum: Hardware
---

### Post by gr4viton on 2011-02-02
My notebook 
ASUS U30JC
with dualcore i5
and ubuntu 10.10
```

Linux graviton-laptop 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

```
```

$ sudo cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
stepping    : 2
cpu MHz        : 2534.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5053.89
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
stepping    : 2
cpu MHz        : 2534.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 2
apicid        : 4
initial apicid    : 4
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5053.88
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
stepping    : 2
cpu MHz        : 2534.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5053.88
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
stepping    : 2
cpu MHz        : 2534.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 2
apicid        : 5
initial apicid    : 5
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5053.88
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```
I recently installed powertop and it shows that C0 is active almost all the time

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (100,0%)      Turbo Mode     0,0%
polling           0,0ms ( 0,0%)         2,54 Ghz     0,0%
C1 mwait          0,2ms ( 0,0%)         2,40 Ghz     0,0%
C2 mwait          2,2ms ( 0,0%)         2,27 Ghz     0,0%
C3 mwait          2,3ms ( 0,0%)         2,00 Ghz   100,0%

Wakeups-from-idle per second :  0,1     interval: 10,0s
Power usage (ACPI estimate): 41,1W (1,5 hours)

Top causes for wakeups:
  39,0% (1000,5)   [kernel scheduler] Load balancing tick
  34,7% (890,2)   [ath9k] <interrupt>
   6,8% (174,4)   PS/2 keyboard/mouse/touchpad interrupt
   4,2% (109,0)   plugin-containe
   3,8% ( 98,2)   [Rescheduling interrupts] <kernel IPI>
   3,8% ( 96,7)   firefox-bin


```

I installed it because the notebook cant last on the battery more then 1:30 to 2 hours.. but before i updated to 10.10.. it stayed on the battery about 4 hours..
It is very bad, because on the win 7 it stays about 5 or even 6 hours..

So my question is how is it possible? And can I change it without downgrading or reinstalling or building my own kernel?

Also the solutions which powertop offers.. are they permanent ? or should I write script which executes them on startup?

One more question should I use cpufreqd? I had it installed, and I always sets all the cores down to the "powersave" state when  the laptop is on battery (with the gnome-desklet), but everytime after a while it sets itself back to the "ondemand" state. So it ran full speed all the time.

Is there a way to set it permanently to "powersave" when on battery.

I would be thankfull for any solutions!
Have a nice day.

---

### Post by gr4viton on 2011-02-10
my fault,
it was not shown in the task manager although it was due to the Boinc which I installed with so many programs that I nearly forgot I have it..

---

