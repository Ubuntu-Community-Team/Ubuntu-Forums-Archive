---
title: "CPU Clock speed seems to be half of what is should"
date: 2009-10-18
forum: Hardware
---

### Post by MadnessRed on 2009-10-18
If I run cat /proc/cpuinfo
I get the following...
> madnessred@Anthony-Acer:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon(tm) X2 Dual-Core QL-64
stepping	: 1
cpu MHz		: 1050.000
cache size	: 512 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4200.96
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon(tm) X2 Dual-Core QL-64
stepping	: 1
cpu MHz		: 1050.000
cache size	: 512 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4189.60
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

I have 2 cores running at 1.05GHz, I though a 2.1GHz Dual core meant that both cores ran at 2.1GHz??
Is there a reason why its showing 1.05?

---

### Post by MadnessRed on 2009-10-18
OK I think I found out the reason...

I ran cat /proc/cpuinfo | grep MHz
Then ran a cpu intensive script, the cat urandom one.
Ran cat /proc/cpuinfo | grep MHz again
Then ran another cat urandom script
Ran cat /proc/cpuinfo | grep MHz again

here are results, I think my cpu underclocks when it is not being used

```

madnessred@Anthony-Acer:~$ cat /proc/cpuinfo | grep MHz
cpu MHz		: 1050.000
cpu MHz		: 1050.000
madnessred@Anthony-Acer:~$ cat /proc/cpuinfo | grep MHz
cpu MHz		: 2100.000
cpu MHz		: 1050.000
madnessred@Anthony-Acer:~$ cat /proc/cpuinfo | grep MHz
cpu MHz		: 2100.000
cpu MHz		: 2100.000

```

---

