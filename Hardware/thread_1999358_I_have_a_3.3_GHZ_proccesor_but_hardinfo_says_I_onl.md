---
title: "I have a 3.3 GHZ proccesor but hardinfo says I only have a 800mhtz?"
date: 2012-06-08
forum: Hardware
---

### Post by trollger on 2012-06-08
Hi every body.

 I don't know if I'm missing something but when I run nano /proc/cpuinfo or run hardinfo I get this

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 10
model name      : AMD Phenom(tm) II X6 1100T Processor
stepping        : 0
microcode       : 0x10000bf
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 6
core id         : 0
cpu cores       : 6
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_l
m cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips        : 6621.64
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb


```Its a six core processor so obviously it prints this five more times. Is my computer actually running at only 800mhtz per core? That would seem ridiculous since I can trans-code a full length movie in handbrake in about 10 mins but seriously whats going on. Is there just an error with /proc? Or some CPU specific problems?  Im running Kubuntu 12.04.

Thank you.

---

### Post by carl4926 on 2012-06-08
Try transcoding a movie and then check your cpu

Ubuntu will clock your cpu down when it's not needed

---

### Post by trollger on 2012-06-08
Cool. I did not know that. Its reading 3300 MHz like it should. 

But how would I find my CPU speed  if I wasn't doing something CPU intensive?

---

### Post by carl4926 on 2012-06-08
> **trollger said:**
> Cool. I did not know that. Its reading 3300 MHz like it should. 

But how would I find my CPU speed  if I wasn't doing something CPU intensive?
I thought you just did, hence the question.
System Monitor also has this info.

Just relax and enjoy

---

### Post by lisati on 2012-06-08
> **trollger said:**
> Cool. I did not know that. Its reading 3300 MHz like it should. 

But how would I find my CPU speed  if I wasn't doing something CPU intensive?

I'm not sure what the equivalent for unity/12.04 is, but "Gnome Classic" under 11.04 has an applet available for the top panel, CPU Frequency Scaling Monitor.

---

### Post by trollger on 2012-06-08
Thanks guys. I get it now.

---

