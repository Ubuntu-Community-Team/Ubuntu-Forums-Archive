---
title: "lenovo thinkpad x120e sluggish"
date: 2011-05-13
forum: Hardware
---

### Post by kenneth.koontz on 2011-05-13
I'm running 11.04 64-bit desktop and this computer seems pretty sluggish. I ran cpu info and got this.


kenneth@achilles:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 20
model		: 1
model name	: AMD E-240 Processor
stepping	: 0
cpu MHz		: 750.000
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc up rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt npt lbrv svm_lock nrip_save pausefilter
bogomips	: 2993.37
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

Notice that the cpu clock speed is at 750 Mhz is this correct? Am I missing something here? Please advise.

---

### Post by kenneth.koontz on 2011-05-13
Nevermind, got it running at 1500 MHz. 

```
cpufreq-selector -f 1500000
```

---

### Post by nemilar on 2011-05-26
Hi,

I have the same laptop.  When idle, /proc/cpuinfo says 750, but when under load, it automatically steps itself up to 1500.

---

