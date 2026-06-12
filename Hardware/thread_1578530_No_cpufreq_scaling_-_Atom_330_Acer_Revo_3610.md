---
title: "No cpufreq scaling - Atom 330 Acer Revo 3610"
date: 2010-09-20
forum: Hardware
---

### Post by Dwarfie on 2010-09-20
Hi,

I'm having problems getting cpufreq scaling working on my new Acer Revo 3610 with and dual-core Atom 1.6GHz and Ion chipset.

The cpu just doesn't seem to be detected as supporting cpu scaling by the kernel at all. 
/sys/devices/system/cpu/cpufreq is empty, and cpufreq-info gives "no or unknown cpufreq driver is active on this CPU".

I'm using ubuntu 10.04 x86_64 edition, though I tried the 32 bit version first, with no difference.

Any idea how I can get the frequency scaling to work?

modprobe acpi-cpufreq - doesn't help.

cat /proc/cpuinfo gives 

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.950
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3199.90
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

```

x4 for each hyperthreaded core.

Any suggestions?

---

### Post by Dwarfie on 2010-09-22
Would just like to bump this. I guess if I get no reply this time I'll try to take it to IRC.

---

### Post by imrazor on 2011-06-03
> **Dwarfie said:**
> Hi,

I'm having problems getting cpufreq scaling working on my new Acer Revo 3610 with and dual-core Atom 1.6GHz and Ion chipset.

The cpu just doesn't seem to be detected as supporting cpu scaling by the kernel at all. 
/sys/devices/system/cpu/cpufreq is empty, and cpufreq-info gives "no or unknown cpufreq driver is active on this CPU".

I'm using ubuntu 10.04 x86_64 edition, though I tried the 32 bit version first, with no difference.

Any idea how I can get the frequency scaling to work?

modprobe acpi-cpufreq - doesn't help.

cat /proc/cpuinfo gives 


Any suggestions?

I realize this is several months late, but I found a fix for my desktop (MSI G31TM-P21 + Pentium E5500). The trick to getting cpufreq working was to enable a function in BIOS called "Intel EIST". Once that was turned on, I was able to run "cpufreq-selector -g ondemand" without an error and "cat /proc/cpuinfo" started reporting a CPU speed of 1200MHz instead of the base 2800MHz.

---

