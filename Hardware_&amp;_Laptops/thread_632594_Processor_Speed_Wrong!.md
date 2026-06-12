---
title: "Processor Speed Wrong!"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by envygeeks on 2007-12-05
I'm sorry if this is a known bug or if there is a fix (please tell me if there is a fix) but is CPU scaling going on my desktop? It shouldn't and I hope that it goes at it's full 2.8ghz.

```

jordon@envygeeks-linux:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 2005.79
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 1000.000
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 2005.79
clflush size    : 64


```

Each core should be a full blown 2.8ghz not 1.0ghz, this also messes with Codega and if it's only going at 1.0 ghz per core that would explain my troubles with Compiz and would prevent me from correctly benching Ruby for clients.  Can somebody please tell me whats going on.

---

### Post by Yellow Pasque on 2007-12-05
Yes, 1.0GHz is what recent AMD CPU's idle at. Not only do they cut the clock speed, but they undervolt to 1.1V as well to save power and keep temps down. This is NOT a bug as the CPU scales back to speed when it gets loaded. If you really don't want it to scale, you should be able to disable "Cool'n'Quiet"/"PowerNow" in your BIOS, or remove powernowd and/or cpufreqd in synaptic. I wouldn't recommend that though.

Sidenote: you can monitor the speed of your CPU by adding the CPU Frequency monitor to your title bar. (right click, Add to Panel)

---

