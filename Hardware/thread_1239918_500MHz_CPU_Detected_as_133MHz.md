---
title: "500MHz CPU Detected as 133MHz"
date: 2009-08-14
forum: Hardware
---

### Post by buggy1 on 2009-08-14
On my ThinkPad 600X, the CPU is detected to be running at 133MHz only, despite it being a 500MHz part.

Ubuntu 9.04 used, all updates installed.

/proc/cpuinfo
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 8
model name    : Pentium III (Coppermine)
stepping    : 1
cpu MHz        : 133.421
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat p
se36 mmx fxsr sse up
bogomips    : 266.84
clflush size    : 32
power management:

```dmesg | grep proc
```
[    0.000000] Detected 133.421 MHz processor.
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    1.470411] Total of 1 processors activated (266.84 BogoMIPS).
```dmesg | grep cpu
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.006700] Initializing cgroup subsys cpuacct
[    9.852181] cpufreq: No nForce2 chipset.
[   10.696015] cpuidle: using governor ladder
[   10.696015] cpuidle: using governor menu
```Any idea...?

---

### Post by kerry_s on 2009-08-14
go into the bios and turn off the cpu throttling.

---

### Post by buggy1 on 2009-08-14
Thanks for quick reply, but the only CPU-related option available is "CPU S/N", which is disabled.

Any other idea...?

---

### Post by kerry_s on 2009-08-14
you look under the power saving in the bios?
could your cpu be going bad?

---

### Post by buggy1 on 2009-08-14
The BIOS of the ThinkPad 600 series is pretty rudimentary, it has very few configurable options, and Power Management doesn't seem to be one.

Before I nuked the Windows XP install and got Jaunty Jackalope on it, IIRC, the CPU was working fine, which was last than a week ago.

I'm hoping it's a software issue, or even better, only a reporting issue (i.e. the CPU is indeed running at 500MHz). I've also looked at tpctl ([http://tpctl.sourceforge.net/tpctl-tool.html](http://tpctl.sourceforge.net/tpctl-tool.html)), but it takes quite some work and time to setup.

Thanks.

---

### Post by buggy1 on 2009-08-14
Wow this is weird... I just check /proc/cpuinfo and now it shows 498MHz

The problem is that, I don't know what have I done, if any, that fixed the problem.

Glad to have this solved before the weekend.

---

### Post by lisati on 2009-08-14
I noticed this thread earlier and decided to check my own machine: Ubuntu reported that it was running at 1GHz, slower than I was expecting. Later I had cause to boot up Vista, tinkered with a power mode setting there, and now Ubuntu reports full speed! No obvious settings in the BIOS settings. Hmmmmm..... curious, perhaps there's a setting within Ubuntu as well that we're missing here.

---

### Post by Yellow Pasque on 2009-08-14
> Ubuntu reported that it was running at 1GHz, slower than I was expecting. Later I had cause to boot up Vista, tinkered with a power mode setting there, and now Ubuntu reports full speed!

Nothing you do in Vista should affect Ubuntu, unless you're tinkering with BIOS settings. Chances are that the first time you checked your CPU, it was idle, and the next time it was under load at that moment.

If your CPU is faster than 1GHz, it probably should run at 1GHz at idle, especially if it's AMD (Intel will underclock too, but the idle clock speed varies a lot more between models). After all, you want to conserve power at idle.

---

### Post by Copernicus1234 on 2009-08-14
Works fine for me. I have a overclocked 3 Ghz CPU to 3600 Mhz (its not a laptop however)

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 3600.094
cache size	: 6144 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 7200.18
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 3600.094
cache size	: 6144 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 7199.67
clflush size	: 64
power management:

---

