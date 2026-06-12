---
title: "Help Cpu two cores running slow"
date: 2012-03-29
forum: Hardware
---

### Post by johnbo96 on 2012-03-29
When I enter:
```
sudo cat /proc/cpuinfo
```

This is what i get: 
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 5
model name      : AMD Athlon(tm) II X3 425 Processor
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 3
core id         : 0
cpu cores       : 3
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 5429.33
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 5
model name      : AMD Athlon(tm) II X3 425 Processor
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 3
core id         : 1
cpu cores       : 3
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 5430.26
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 5
model name      : AMD Athlon(tm) II X3 425 Processor
stepping        : 2
cpu MHz         : 2700.000
cache size      : 512 KB
physical id     : 0
siblings        : 3
core id         : 2
cpu cores       : 3
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 5430.27
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

It would appear that only one of my cores is running at full speed. If this is fix able, how do i fix this. If it means anything to anyone I'm using Kubuntu

Thank you kindly,
                Me

---

### Post by Pand5461 on 2012-03-29
I think it's just power saving. I have Intel Core i5, and its clock speed is 1600 MHz while idle but it rises automatically to 3600 MHz when loaded.

---

### Post by QIII on 2012-03-29
Does your motherboard support AMD Cool 'n Quiet and do you have it enabled?

That will throttle the CPU cores when not under load.

Run the check a few times quickly.  Does the CPU speed change between the cores?

(800Mhz, by the way, is the typical throttled no-load speed in late model AMD CPU cores using Cool 'n Quiet")

---

### Post by Yellow Pasque on 2012-03-29
> I think it's just power saving.
If that was the case, all 3 cores would be 800MHz

Does this happen every time? If not, it could be that the CPU is throttled by the time the third core is checked.

---

### Post by QIII on 2012-03-29
I have an 1100T Black Edition mildly overclocked.  At any given time I may find any combination of speeds ranging from 800MHz to 3.4GHz in any of the six cores.  Different cores are running faster than others every time I check.  There is even a "turbo" mode during which I may find the single allowed core running at 3.7GHz.

My Phenom II x4 processors behave exactly the same way.

What the OP is seeing is not unusual -- as long as the load is bouncing around and none of the cores is running full bore all the time.

Cool 'n Quiet isn't powersaving per se.  It throttles unused cores based on load.

A power saving mode generally throttles core activity at some predetermined maximim below the CPU's design max.

---

### Post by Yellow Pasque on 2012-03-29
Hmm. I've never seen my Phenom II's 3 cores at different speeds, but I guess the hardware does support it.

---

### Post by QIII on 2012-03-29
Making matters worse, of course, is AMDs terrible, terrible accuracy problems with temp and activity reporting.  As a matter of course, I use a script to add 10 to the temp my Phenoms IIs report and display that in my conkys. 

It's a bit hard to accept a temperature reading 2 degrees below ambient!  :D

Edit:  actually, it looks like the 1100T can switch three cores at a time to turbo mode when it needs to run fewer threads faster.  Hmmm.  Thought it was just one.  I guess I've just never seen that in progress.

---

### Post by matt_symes on 2012-03-29
Hi

You can always change the scaling_governor.

The available governors.

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors
```

The current governor

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

You can pipe the governor you want into scaling_governor.

You can also use Jupiter.

Kind regards

---

### Post by johnbo96 on 2012-03-29
I ran it a few more times and the result didn't change much, except that core 2 went down to 800 and a once core 0 went up to 2700. I also tried to run a 1080p video. at which point a few things happened:
core 0 went to 800 mhz
core 1 went to 1500 mhz
core 2 went to 2100 mhz

Thanks for the help,
                   Me

---

### Post by QIII on 2012-03-29
I think you are OK.  It's just a snapshot.  If it changes, it's fine.  Different cores are taking part of the load in turn.  If you have several things running, all of them might be higher than 800MHz.

Happy hunting!

---

