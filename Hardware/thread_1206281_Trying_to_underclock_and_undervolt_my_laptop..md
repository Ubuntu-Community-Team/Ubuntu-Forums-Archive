---
title: "Trying to underclock and undervolt my laptop."
date: 2009-07-07
forum: Hardware
---

### Post by Shikaku2 on 2009-07-07
I've been messing with the cpudyn package in Jaunty, and it works kind of.  It only clocks in 2 intervals (.8 GHZ and 1.6 GHZ) when I know it can go with lower with more intervals and I have no idea how to make it undervolt either.

Here is what I get when I run cat /proc/cpuinfo:

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping	: 2
cpu MHz		: 1600.000
cache size	: 256 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 3192.37
clflush size	: 64
power management: ts fid vid ttp tm stc

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping	: 2
cpu MHz		: 1600.000
cache size	: 256 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 3192.37
clflush size	: 64
power management: ts fid vid ttp tm stc
```

In short, I want more power management options that I can work with for maximum Battery Life and minimum heat.

---

### Post by shatterblast on 2009-07-07
If you haven't already, you might check out the Ubuntu Remix version.  To my understanding, it has options enabled to help reach an optimal state for your computer's power-saving capabilities.  It may have a few compatibility issues depending on the hardware platform.

---

