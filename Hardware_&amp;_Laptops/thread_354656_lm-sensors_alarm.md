---
title: "lm-sensors alarm"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by wiz561 on 2007-02-06
Hi!

   I'm running Ubuntu Feisty (herd 3).  I have an amd athalon 64 dual core processor and a MSI K9N-SLI motherboard.  I just installed lm-sensors yesterday and used the patch located here for my motherboard.

[http://lists.lm-sensors.org/pipermail/lm-sensors/2007-January/018724.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2007-January/018724.html)

  After rebooting and running lm-sensors -f, I get the following...

---
$ sensors -f
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
            +127°F
Core1 Temp:
            +124°F

w83627ehf-isa-0a10
Adapter: ISA adapter
VCore:     +1.36 V  (min =  +0.00 V, max =  +1.30 V) ALARM
+12V:     +12.30 V  (min = +10.82 V, max = +13.20 V) 
AVCC:      +3.33 V  (min =  +3.14 V, max =  +3.47 V) 
+3.3V:     +3.33 V  (min =  +3.14 V, max =  +3.47 V) 
-12V:     -12.28 V  (min = -12.67 V, max = -11.31 V) 
+5V:       +5.05 V  (min =  +4.75 V, max =  +5.25 V) 
VSB:       +3.30 V  (min =  +3.14 V, max =  +3.47 V) 
VBAT:      +2.99 V  (min =  +2.85 V, max =  +3.15 V) 
Case Fan:    0 RPM  (min =    0 RPM, div = 128)
fan2:        0 RPM  (min =    0 RPM, div = 128)
Aux Fan:     0 RPM  (min =    0 RPM, div = 128)
CPU Fan:  3515 RPM  (min =    0 RPM, div = 8)
fan5:        0 RPM  (min =    0 RPM, div = 128)
Sys Temp:    +97°F  (high =  +255°F, hyst =  +235°F)  
CPU Temp: +124.7°F  (high = +176.0°F, hyst = +167.0°F)  
AUX Temp: +122.9°F  (high = +176.0°F, hyst = +167.0°F)  

---

For the VCore, it says 1.36 V and ALARM right next to it.  Everything in the bios is set at the defaults and I haven't messed with overclocking it or changing anything like that at all.  Should I be worried about this?

Thanks for any help!

Oh, also, here is my cpuinfo....


$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2211.369
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4426.28
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2211.369
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4432.20
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by kidders on 2007-02-06
Hi there,

> Should I be worried about this?The short answer is "Maybe... but probably not". :-)

To be sure, I would check to see whether there are any lmsensors-related notes anywhere on the web about my specific motherboard, that mention this issue. Very often (almost always), the actual values lmsensors reads from your hardware are relatively meaningless, and have to be fiddled to correlate sensibly with actual degrees, RPM, etc. (If you look in its configuration file, you'll see this being done.) I'm willing to bet that one or more of the modifiers you're using (or were chosen *for* you) are wrong.

Although it's nice when lmsensors summary tables actually have some basis in reality, you should really think of them as lists of ratios, rather than actual values ... How the numbers change over time is often more interesting/helpful than how big they happen to be.

There are hundreds of sample lmsensors configurations around for a wide range of motherboards, that might offer you some hints. Have you seen any for yours?

---

### Post by Bad_Byte on 2008-02-18
I too get strange readings from lm-sensors, using asus p5k-e/wifi & e6750.

> **wiz561 said:**
> 
w83627ehf-isa-0a10
Adapter: ISA adapter
VCore:     +1.36 V  (min =  +0.00 V, max =  +1.30 V) ALARM
AUX Temp: +122.9°F  (high = +176.0°F, hyst = +167.0°F)  


```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +27°C  (high =   +85°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +27°C  (high =   +85°C)

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.31 V  (min =  +0.00 V, max =  +1.74 V)
in1:      +11.25 V  (min =  +0.05 V, max =  +4.22 V) ALARM
AVCC:      +3.28 V  (min =  +2.90 V, max =  +2.22 V) ALARM
3VCC:      +3.28 V  (min =  +1.17 V, max =  +2.38 V) ALARM
in4:       +1.64 V  (min =  +0.91 V, max =  +1.10 V) ALARM
in5:       +1.69 V  (min =  +1.28 V, max =  +1.16 V) ALARM
in6:       +5.25 V  (min =  +3.02 V, max =  +2.64 V) ALARM
VSB:       +3.28 V  (min =  +0.86 V, max =  +1.15 V) ALARM
VBAT:      +0.70 V  (min =  +0.40 V, max =  +1.33 V)
Case Fan:    0 RPM  (min =  260 RPM, div = 64) ALARM
CPU Fan:  1607 RPM  (min = 2191 RPM, div = 4) ALARM
Aux Fan:     0 RPM  (min =  659 RPM, div = 64) ALARM
fan5:        0 RPM  (min = 7031 RPM, div = 64) ALARM
Sys Temp:    +30°C  (high =    +4°C, hyst =   +10°C)   ALARM
CPU Temp:  +29.0°C  (high = +80.0°C, hyst = +75.0°C)
AUX Temp: +121.5°C  (high = +80.0°C, hyst = +75.0°C)   ALARM

```

---

