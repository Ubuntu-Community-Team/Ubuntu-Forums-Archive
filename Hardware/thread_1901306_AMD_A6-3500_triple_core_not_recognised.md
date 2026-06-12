---
title: "AMD A6-3500 triple core not recognised"
date: 2011-12-28
forum: Hardware
---

### Post by nfarley88 on 2011-12-28
Hi,
I recently bought an AMD A6-3500 (triple core), one of AMD's new APU range but just discovered that ubuntu cannot see the third core, and system utilities like top and screenlets showing CPU usage show odd percentages like '124%' and '3%' when playing flash videos.

Output of ```
uname -a
``` is:
```
Linux bach 3.0.0-14-server #23-Ubuntu SMP Mon Nov 21 20:49:05 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Output of ```
cat /proc/cpuinfo
``` is:
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 18
model		: 1
model name	: AMD A6-3500 APU with Radeon(tm) HD Graphics
stepping	: 0
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 3
core id		: 0
cpu cores	: 3
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 4944.18
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 18
model		: 1
model name	: AMD A6-3500 APU with Radeon(tm) HD Graphics
stepping	: 0
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 3
core id		: 1
cpu cores	: 3
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 4943.98
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 18
model		: 1
model name	: AMD A6-3500 APU with Radeon(tm) HD Graphics
stepping	: 0
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 3
core id		: 2
cpu cores	: 3
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 4944.26
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

```

Any ideas?

---

### Post by jackluu on 2012-01-07
Hi there, I intend to buy this one too. How is it in your machine? Can you use the integrated graphic?

---

### Post by MoreOrLess on 2012-01-07
I'm not sure what the OP is talking about. cpuinfo shows core number 0, 1, and 2. That's 3 cores..

---

### Post by nfarley88 on 2012-05-11
I got confused; another one of my machines with only two cores displays three. I figured... something different. Anyway problem is fixed now! The only thing about my integrated graphics is that catalyst isn't supported yet (at least not with my setup). The open source drivers do pretty good for most things though! (Read, can't play 1080p youtube video, but never struggles with 720p anything).

---

### Post by MonkeyPaw on 2012-05-12
If you go over to AMD.com and download the catalyst drivers and follow the install instructions, you should see better results.

---

