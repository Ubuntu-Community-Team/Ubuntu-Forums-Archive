---
title: "Ubuntu registers processor at only 800mhz"
date: 2011-04-24
forum: Hardware
---

### Post by Nogal on 2011-04-24
Hey there -- I'm running ubuntu 11.04 and it seems to say that my processor is only a 800mhz one, I'm using a Gateway P-7811FX currently, any ideas?

---

### Post by bowens44 on 2011-04-24
probably cpu frequency scaling is active. Does it kick up higher when doing something cpu intensive like running glxgears?

---

### Post by Nogal on 2011-04-24
no, it simply detects two cores at 800mz and never any more/less. It causes issues when loading up programs due to lack of resources -- especially in wine but the problem is not wine exclusive

---

### Post by conradin on 2011-04-24
show us
```

$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

```

check out this article where I stole said code from:
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

where are you getting this info from about your cpu bein 800MHz, and what is it supposed to be? 
also show us

```

$cat /proc/cpuinfo

```

---

### Post by Nogal on 2011-04-24
I have a dual core 2.26ghz processor -- here are the outputs you asked for:
Frequencies:
```
2267000 2266000 1600000 800000 

```cpuinfo:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
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
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 4521.85
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 4521.98
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by jocko on 2011-04-25
> **Nogal said:**
> I have a dual core 2.26ghz processor -- here are the outputs you asked for:

Nothing out of the ordinary there. It clearly says your cpu is 2.26 GHz, but when you checked it was scaled down to 800 MHz.
Check what 'cat /proc/cpuinfo' lists when you run something that causes 100% cpu usage.
If it does not scale up to 2.26 GHz you may have a problem, otherwise it works perfectly normal.

---

### Post by PatrickVogeli on 2011-04-25
you can do the test with a program called cpuburn. Then you can run burnMMX (I believe) in as many terminal windows as cores you have. That will cause 100% cpu load on each core, and then you can check if the processor runs at full speed.

---

