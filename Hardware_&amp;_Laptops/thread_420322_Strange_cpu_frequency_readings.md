---
title: "Strange cpu frequency readings"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by gwi on 2007-04-23
I am running Feisty on an Asus A8N SLI DeLuxe board, with an Opteron 165. Stock speeds with Cool'n'Quiet enabled are 1000MHz and 1800MHz.
The Gnome CPU Frequency applet is showing those speeds.

I overclocked the cpu to 2340MHz, and left Cool'n'Quiet enabled (so my system runs cool and quiet when possible, and fast when needed). All readings are still 1000MHz and 1800MHz, unless I disable Cool'n'Quiet: speed shown is 2,35GHz.

Superpi tests seem to indicate that with Cool'n'Quiet enabled, the system will switch to 2340MHz, not 1800MHz. Time for 'superpi 20' is about 30 seconds, as it is with Cool'n'Quiet disabled.

Why do I get the wrong readings, and how can I fix this?

output of dmesg | grep powernow, QnQ enabled:
```
[   71.356000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[   71.356000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x8
[   71.356000] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
```

output of dmesg | grep powernow, QnQ disabled:
```
[   67.692000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[   67.692000] powernow-k8: MP systems not supported by PSB BIOS structure
[   67.692000] powernow-k8: MP systems not supported by PSB BIOS structure
```

output of a64-vid, QnQ enabled:
```
Maximum freq.   : 0x33 (5900 MHz)
Startup freq.   : 0x28 (4800 MHz)
Current freq.   : 0x3c (6800 MHz)

Voltage range   : 0x1e (800 mV) [No low limit] -> 0x00 (1550 mV) [No high limit]
Startup voltage : 0x00 (1550 mV)
Current voltage : 0x00 (1550 mV)
```

output of a64-vid, QnQ disabled:
```
Maximum freq.   : 0x3d (6900 MHz)
Startup freq.   : 0x38 (6400 MHz)
Current freq.   : 0x3c (6800 MHz)

Voltage range   : 0x1e (800 mV) [No low limit] -> 0x00 (1550 mV) [No high limit]
Startup voltage : 0x00 (1550 mV)
Current voltage : 0x00 (1550 mV)
```

output of cat /proc/cpuinfo, QnQ enabled:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165   
stepping        : 2
cpu MHz         : 1000.000
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2609.80
clflush size    : 64
```

output of cat /proc/cpuinfo, QnQ disabled (only difference with the above shown):
```
cpu MHz         : 2347.403
bogomips        : 4697.65
```

---

