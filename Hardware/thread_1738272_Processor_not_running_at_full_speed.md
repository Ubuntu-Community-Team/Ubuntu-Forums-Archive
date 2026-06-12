---
title: "Processor not running at full speed"
date: 2011-04-24
forum: Hardware
---

### Post by perrti-y02 on 2011-04-24
Hello,

I am having a few problems getting my processor to run at the speed it is supposed to. I have an Intel Core 2 Duo E6750 which I seem unable to run any faster than 1.6GHz. Here is the output of /proc/cpuinfo

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 3203.11
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 3202.88
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

I have disabled ondemand using rcconf and my BIOS claims it is running at 8*333MHz.

Any ideas? This is stopping me from watching some HD videos.

Many Thanks

Tim

---

### Post by TenPlus1 on 2011-04-24
Doesn't your processor have PowerStep technology which increases the 1.6ghz to 2.6ghz when the system load calls for it ?

As for HD movies, try VLC with the hardware acceleration switched on, it'll use your GPU if you use a newed nvidia/ati card to decode the movies, leaving your CPU handy for other things :)

---

### Post by perrti-y02 on 2011-04-24
Even when running at full load the CPU doesn't increase. Playing a Full HD movie causes it to go to 100% demand at certain points and it then causes jitter.

I have just flashed the BIOS to the newest version and it still hasn't worked. I have tried fiddling with things in the BIOS but it doesn't seem to make any difference. I have turned of C1E which I think is another name for PowerStep but this makes no difference.

I do want to sort out my processor but I will try VLC.

---

### Post by perrti-y02 on 2011-04-27
Any more ideas? I was thinking of trying a new motherboard to see if it is to do with how the BIOS talks to the CPU?

---

### Post by KegHead on 2011-04-27
Hi!

What version are you running?

Also have you updated your kernel recently?

KegHead

---

### Post by Yellow Pasque on 2011-04-27
> **TenPlus1 said:**
> As for  here: [https://launchpad.net/~dtl131/+archive/catalysthacksHD](https://launchpad.net/~dtl131/+archive/catalysthacksHD) movies, try VLC with the hardware acceleration switched on, it'll use your GPU if you use a newed nvidia/ati card to decode the movies, leaving your CPU handy for other things :)
VLC hardware decode uses VA-API and will only work with some Intel GPU's by default.
To get it working with nvidia/ati binary drivers, you have to install libva and xvba (or vdpau) backend for libva from Splitted Desktop Systsems and rebuild vlc. It's a pain, but it's already done for you here: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)

---

### Post by tigrezno on 2011-04-27
paste the output of:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq

---

### Post by perrti-y02 on 2011-05-02
Hello,

I am now running 11.04 with the newest kernel and I still have this problem.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
performance
```

is the output there

and 

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq gives

```
1600000
```

I get the feeling there should be more there...

---

### Post by tigrezno on 2011-05-02
> **perrti-y02 said:**
> Hello,

I am now running 11.04 with the newest kernel and I still have this problem.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
performance
```

is the output there

and 

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq gives

```
1600000
```

I get the feeling there should be more there...

ok, take a look at /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

and the same for cpuinfo_min_freq, those are your cpu supported max/min speed.

---

### Post by perrti-y02 on 2011-05-02
CPU max says 1600000 and min is 1200000. This flatly contradicts what the BIOS tells me.

Any ideas what is going wrong?

---

### Post by tigrezno on 2011-05-02
> **perrti-y02 said:**
> CPU max says 1600000 and min is 1200000. This flatly contradicts what the BIOS tells me.

Any ideas what is going wrong?


check your bios options, maybe there is a limitation turned on?
disable any power saving technology and such

I really don't know what's happening to your cpu

---

### Post by perrti-y02 on 2011-05-02
All the power saving options are off in the BIOS. Is it possible that the BIOS simply doesn't see the processor properly? The Motherboard is a Shuttle SG31G2 and the CPU is the E6750.

I saw through google that some people have had problems with this combination so is it possible that this combo simply doesn't work?

---

### Post by tigrezno on 2011-05-02
may be

try sending a support ticket to your board manufacturer

also check for bios updates

---

