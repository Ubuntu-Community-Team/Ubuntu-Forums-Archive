---
title: "CPU Specs"
date: 2009-10-20
forum: Hardware
---

### Post by mastermindg on 2009-10-20
I'm trying to determine the model and frequency of the processor I currently have installed (i.e, Brisbane 2.3GHz..). Here is the output of cpuinfo, any ideas?:
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2004.34
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2004.34
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```

---

### Post by bowens44 on 2009-10-20
> **mastermindg said:**
> I'm trying to determine the model and frequency of the processor I currently have installed (i.e, Brisbane 2.3GHz..). Here is the output of cpuinfo, any ideas?:


model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
cpu MHz		: 1000.000



It probably shows 1gig instead of 2.3 gig because of frequency scaling.

---

### Post by mastermindg on 2009-10-20
So, with frequency scaling that would mean that I've got a 2.0GHz Dual-Core?

---

### Post by mastermindg on 2009-10-20
OK, so I figured out that my cpu frequency is 2100000 (2.1GHz) from /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq. The problem that I'm having now is that my processors seem to be locked on 1GHz even though I'm active on my system. How can I adjust these settings?

---

### Post by mastermindg on 2009-10-20
I figured it out: Installed cpufred and cpufreq-utils, uncommented ondemand profiles and restarted the cpufred service. Now my cpu's are running at capcacity.

---

