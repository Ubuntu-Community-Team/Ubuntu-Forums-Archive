---
title: "Intel e6550 frequency issue"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by zeno on 2007-10-30
Hi 2 all,
i installed ubuntu gutsy 64 bit on my Intel Core 2 Duo E6550 processor but i have a big problem:
the frequencies accepted for my processor are only 2... 600 Mhz and 700 Mhz and seems that i can't modify these settings.
I installed cpufreq utils and even if i make a sudo 
```
cpufreq-set  -d 600000 -u 2330000
```
i can't get processors running @ 2.33Mhz.

Here is my cpuinfo:
> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping        : 11
cpu MHz         : 600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4670.48
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping        : 11
cpu MHz         : 600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4666.71
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

And here is my cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
> 
700000 600000


Is there a way to have my processors running @ 2.33 Mhz?

Thanks a lot

---

### Post by zeno on 2007-11-02
up

---

### Post by wazzup on 2008-01-04
any succes yet ?

---

### Post by zeno on 2008-01-04
I'm sorry, but i answer: no.
I haven't any progress. The only thing i made was to upgrade the bios of my motherboard (Asus P5N-E SLI) to the latest one but without success... i'm very disappointed about this issue because phoronix reported my motherboard as 100% compatible with Linux :(
The next step is to try to compile a vanilla kernel, but i will not have time to do this for a while.

---

### Post by blueworm on 2008-01-07
I'm having exact same problem, same HW. It seems that it is acpi reporting incorrectly to kernel. The proper fix is for asus to fix BIOS.
My findings so far. When it reports 700mhz it is actually 2,33Ghz. This can be deduced by benchmarking. What I'm not sure about is the "actual" clockspeed when it reports 600mhz.

---

### Post by jespdj on 2008-01-07
It was slightly different for me, but maybe this will be useful.

I have a Core 2 Duo E6600 (2.4 GHz) in my desktop PC, on an Asus P5B Deluxe/WiFi-AP motherboard. At first, frequency scaling didn't work at all (the CPU was running at 2.4 GHz all the time and cpufreq-info reported that frequency scaling wasn't supported). I flashed to the newest BIOS version, and then frequency scaling was supported, but now the CPU was stuck on 1.6 GHz (the E6600 has two speeds: 1.6 GHz and 2.4 GHz).

To fix this, I edited /etc/init.d/cpufrequtils and changed the line

MAX_SPEED=""

to

MAX_SPEED="2400MHz"

Now it works without problems.

---

### Post by zeno on 2008-01-07
> **jespdj said:**
> 

To fix this, I edited /etc/init.d/cpufrequtils and changed the line

MAX_SPEED=""

to

MAX_SPEED="2400MHz"

Now it works without problems.

I tried your "fix" but without good results.

---

### Post by wazzup on 2008-01-07
I'm stuck between 2.0 and 2.3 Ghz... 

so I'm capable of running at max speed, but I'm dissapointed it won't throttle down further. What's the use if all you can throttle down to is 2.0 Ghz (15% or so).

---

### Post by blueworm on 2008-01-07
I've been testing a little more. 
Even though cpufreq-info is reporting 600/700 cpu scaling does actually work.
Like I said 700 = 2333 mhz 1.35v, and 600 = *whatever* at 1.2v.
The fact that voltage is being throttled properly confirms this. Also monitoring cpu temperature also reflects this since cpu is cooler at the lower 600 mhz setting.

---

### Post by blueworm on 2008-01-07
> **wazzup said:**
> I'm stuck between 2.0 and 2.3 Ghz... 

so I'm capable of running at max speed, but I'm dissapointed it won't throttle down further. What's the use if all you can throttle down to is 2.0 Ghz (15% or so).
What mainboard and BIOS version?

---

### Post by zeno on 2008-01-07
> **virtuoso said:**
> are you asking about overclocking your processor?
i think overclocking should not be done as.. it has more disadvantages than the advantages..!

We are talking about cpufreq-acpid frequency issues on new hardware... where you read about overclocking in this 3ad?!?!

---

### Post by wazzup on 2008-01-14
> **blueworm said:**
> What mainboard and BIOS version?

It's a HP board with BIOS

HP Compaq dc7800 Small Form Factor
 smbios.bios.version = '786F1 v01.04'

---

### Post by zeno on 2008-02-27
With the latest 0901 bios from Asus the frequency is ok. Now i can read the real frequency of the CPU!

Update your bios!

---

### Post by wazzup on 2008-02-28
> **zeno said:**
> With the latest 0901 bios from Asus the frequency is ok. Now i can read the real frequency of the CPU!

Update your bios!

I don't think that would work on my non-ASUS mainboard. I'll probably have to wait until HP coughs up a new BIOS.

---

### Post by zeno on 2008-02-28
> **wazzup said:**
>  I'll probably have to wait until HP coughs up a new BIOS.

Yes. The problem is the bios and not the kernel.

---

