---
title: "Processor is Severely Underclocked"
date: 2009-05-04
forum: Hardware
---

### Post by gerowen on 2009-05-04
I kept wondering why my CPU rarely heats up and the fan rarely comes on, so I thought maybe there was an issue with the fan sensors.  I googled cause' I forgot how to check CPU's status, and did a cat /proc/cpuinfo and got this:
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-72
stepping	: 1
cpu MHz		: 500.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4198.13
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-72
stepping	: 1
cpu MHz		: 500.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4189.63
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

My processor, as it was displayed when I had Windows on this machine and as it is listed is the following.

AMD Turion X2 64 @ 2.1 Ghz

Any idea as to why it's only 500 Mhz per core?

---

### Post by HavocXphere on 2009-05-04
Various linux OSs underclock the CPU on the fly as part of powersaving...but 500mhz does seem a bit low.

What happens if you max out the CPU?

---

### Post by gerowen on 2009-05-04
Ah, that did it.  I wrote a small python script that just loops an exponential math equation and after about 10 seconds and 15 degrees temp increase it jumped up to normal, I=noob, lol.

---

### Post by gerowen on 2009-05-04
Is there a way to change the power saving settings so that it doesn't underclock my processor so much?  I can't seem to find a menu option for controlling the CPU speed reduction.

---

### Post by Brian_the_King on 2009-05-04
Right click on a panel, 'Add to Panel', and install 'CPU Frequency Scaling Monitor'

---

