---
title: "/proc/cpuinfo wrong?"
date: 2008-05-14
forum: Hardware
---

### Post by prox2far on 2008-05-14
OK Iv'e tried searching for this without any results related to my experience.

I have a Gigabyte GA-P35C-DS3R and an Intel E2160 1.8 GHz. Recently Iv'e been overclocking the cpu to see what i can gain from it.

After I started lowering the CPU multiplier I get some impressive results from /proc/cpuinfo.

Example running 6 x 400 Mhz = 2.4 GHz

```

cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
stepping        : 13
cpu MHz         : 3600.155
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 7205.03
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
stepping        : 13
cpu MHz         : 3600.155
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 7199.99
clflush size    : 64

```

3600 MHz is way above what I have set in the BIOS.

Before posting this i did a little test with a home baked prime calculation program testing the calculation time with stock, 250 x 9 and 400 x 6 settings. 

stock: 60 seconds
250x9: 47 seconds
400x6: 45 seconds

From the results the CPU seems to be running at 2.4 GHz making me wonder why cpuinfo reports 3.6 GHz. Does anybody have an educated guess or knowledge to why i get such a high reading?

---

