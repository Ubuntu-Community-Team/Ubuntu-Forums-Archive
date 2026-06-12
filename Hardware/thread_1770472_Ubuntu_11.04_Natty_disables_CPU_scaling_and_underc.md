---
title: "Ubuntu 11.04 Natty disables CPU scaling and underclocks on Thinkpad T40p"
date: 2011-05-29
forum: Hardware
---

### Post by kimchi on 2011-05-29
I have an IBM Thinkpad T40p with a Pentium M 755 2.0 GHz CPU. After upgrading to Ubuntu 11.04 from 10.10 the CPU is incorrectly underclocked to 598 MHz and cannot be adjusted, manually or automatically. When I boot off the old 10.10 live CD, CPU scaling and all the governors work again perfectly.

I've tried loading every possible scaling module I could think of (acpi-cpufreq, speedstep-centrino, p4-clockmod, cpufreq_ondemand) and tried multiple scaling daemons and programs with no luck at all. I'm stuck at what to try next.

The Gnome Panel CPU Scaling monitor says "CPU frequency scaling unsupported" and here is the output of various commands:

```
$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
  
  
$ sudo /etc/init.d/cpufrequtils start
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...
 * disabled, governor not available... 


$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.00GHz
stepping    : 8
cpu MHz        : 597.949
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips    : 1195.89
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:


$ ls -h /sys/devices/system/cpu
cpu0  cpufreq  cpuidle  kernel_max  offline  online  possible  present  probe  release


$ ls -h /sys/devices/system/cpu/cpu0
cpuidle  crash_notes  topology


$ ls -lh /sys/devices/system/cpu/cpufreq
total 0


$ ls -h /sys/devices/system/cpu/cpuidle
current_driver  current_governor_ro


$ cat /sys/devices/system/cpu/cpuidle/*
acpi_idle
menu


$ dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] PAT not supported by CPU.
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u4194304
[    0.000000] pcpu-alloc: s28800 r0 d24448 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] CPU 0 irqstacks, hard=f5406000 soft=f5408000
[    0.008754] Initializing cgroup subsys cpuacct
[    0.008939] mce: CPU supports 5 MCE banks
[    0.060134] weird, boot CPU (#0) not listed by the BIOS.
[    0.064798] Brought up 1 CPUs
[    0.216353] Switched to NOHz mode on CPU #0
[    0.220886] cpufreq-nforce2: No nForce2 chipset.
[    0.326754] ACPI: acpi_idle registered with cpuidle
[    0.605330] cpuidle: using governor ladder
[    0.605536] cpuidle: using governor menu


$ uname -a
Linux dep 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux


$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```

---

### Post by kimchi on 2011-06-02
Bump. Anyone have any pointers at all?

---

### Post by kimchi on 2011-06-03
Update: Booting with an older kernel, 2.6.35-29-generic, works perfectly. How can I dig deeper to solve this problem?

```
$ uname -a
Linux dep 2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:13:54 UTC 2011 i686 i686 i386 GNU/Linux


$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: centrino
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 798 MHz - 2.00 GHz
  available frequency steps: 798 MHz, 1.06 GHz, 1.33 GHz, 1.60 GHz, 2.00 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 798 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 798 MHz.
  cpufreq stats: 798 MHz:57.47%, 1.06 GHz:0.69%, 1.33 GHz:0.35%, 1.60 GHz:0.53%, 2.00 GHz:40.96%  (744)
```
And now there are more /sys entries:

```
$ ls -h /sys/devices/system/cpu
cpu0  cpufreq  cpuidle  kernel_max  offline  online  perf_events  possible  present  probe  release


$ ls -h /sys/devices/system/cpu/cpu0
cpufreq  cpuidle  crash_notes  topology


$  ls -lh /sys/devices/system/cpu/cpufreq
total 0
drwxr-xr-x 2 root root 0 2011-06-03 10:00 ondemand
```

---

### Post by Chilly_Willy on 2011-06-08
I had the same problem.

This is the fix: [http://ubuntuforums.org/showthread.php?t=1745001](http://ubuntuforums.org/showthread.php?t=1745001)

Edit /etc/init.d/cpufrequtils and sett he values for MAX_SPEED and MIN_SPEED.

To find the frequencies: cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by kimchi on 2011-06-14
I tried this already and it doesn't work. I believe it's a kernel related problem preventing CPU scaling from  loading, so I can't even access those system files and paths because they don't exist.

My current work around is booting to a previous kernel version saved from my upgrade from 10.10, which is kernel 2.6.35-29-generic.

I wish I knew where to direct this problem so I could get more visibility by those who can help me work towards solving it.

---

### Post by TBABill on 2011-06-14
For 11.04 aren't there a few kernels available? I believe mine is 2.6.38-9? I'm not positive and can't verify...not currently on a Linux machine. But, if you can get a previous kernel and try it you may find it working correctly. I know it's a kernel function so could something have corrupted or could it be a bug in your current kernel? Mine sets to ondemand by default, which I believe is standard since 2.6.32-xx. Worth a shot if you can try an older kernel via synaptic.

---

### Post by deadite66 on 2011-06-20
Having this problem too since my upgrade to natty.

Stuck at 1.5Ghz unless i use powersave then it stuck at 187Mhz and too slow to do much.
[IMG]https://dl.dropbox.com/u/7618572/cpufreq-end-1m.png[/IMG]

Big jump in heat for a fanless mediapc.
[IMG]https://dl.dropbox.com/u/7618572/temperatures-end-1m.png[/IMG]

---

### Post by kedmond on 2011-08-22
I upgraded my Dell Latitude E6400 laptop to 11.04.  It's a totally fresh install.  Ever since then, when the CPU gets warm the fans go on like they should, but at full speed.  It's all or nothing.  Then, after the CPU has cooled, the fans just stay on indefinitely.  If the CPU is at 100% for a long time, with the fans on too, Ubuntu eventually decides to temporarily lock the laptop at the slowest speed (800 MHz) until it's cooled down to 40 degrees, which is the idle temp. It SUCKS.

How the hell do I fix this?  10.10 was so much better.

---

### Post by deadite66 on 2011-08-22
no other option but to go back to maverick.

---

### Post by Chilly_Willy on 2011-08-23
You could also try the new 3.0 kernel from oneiric. I used this ppa: [https://launchpad.net/~guido-iodice/+archive/kernel-and-drivers](https://launchpad.net/~guido-iodice/+archive/kernel-and-drivers) but you could also try the newest from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.3-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.3-oneiric/)

---

### Post by deadite66 on 2011-09-06
i've tried the 3.0.4 oneiric kernel but its no help.

from exhaustive googling it seems the kernel devs have decided the Pentium cpu's shouldn't have been using acpi-cpufreq in the first place so aren't going to fix this in the mainline kernel despite years of it working nicely for years.

guess we should resigned to the fact we can't use acpi-cpufreq, ondemand and have undervolting anymore.

---

