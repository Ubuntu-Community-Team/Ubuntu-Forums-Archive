---
title: "How to get AMD64 CPU frequency above rating with Dynamic Overclocking"
date: 2014-05-09
forum: Hardware
---

### Post by m-dw on 2014-05-09
My main desktop has an AMD64 3200+ CPU which is rated at 2000MHz.  The motherboard is made by MSI and supports Cool'n'Quiet and Dynamic Overclocking technologies.

Cool'n'Quiet lowers the CPU speed to 1000MHz under low loads, dropping the CPU temperature to about 30degC on a cool day, and under CPU intensive activities the CPU goes up to 2000MHz, and hovers around the 50degC mark.  I have enabled dynamic overclocking on the motherboard, which should allow the CPU to go 10% over the rated speed under load. but it doesn't go above 2000MHz.

lshw provides the following...

```

*-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3200+
          slot: Socket-A
          size: 1800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow rep_good nopl cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified

```

Is there any way to set a higher maximum CPU speed?

---

### Post by m-dw on 2014-05-12
I guess not then.  Bouncing this to maybe get a new readership....

---

### Post by tgalati4 on 2014-05-12
Do you have a cpu frequency monitor on your dash?  Watch the cpu frequency and run a few instances of *cpuburn* to see if it kicks into overdrive.  Does this machine dual-boot?  Does it work in Windows?

---

### Post by m-dw on 2014-05-12
I'm using gkrellm with the  cpufreq plugin.  I was monitoring while transcoding a DVD with transcode..  Just installed cpuburn and ran 5 instances.  While performance is pretty sluggish, the CPU still hasn't exceeded 2GHz.  /proc/cpuinf also shows 2000MHz at maximum and 1000 MHz at minimum utilisation.  Sensors reported that it was running a couple of degrees hotter at 52degC, but nothing to worry about.

This machine has never run Windows, but dynamic overclocking definitely did work in SUSE 10.2 I had it set for 5% overclock and it ran (and reported) at 2100MHz).  I'm pretty sure Ubuntu (which I've been running since 12.04) has never shown a speed higher than 2GHz.  It's not a big deal (how much is 10% going to benefit me).

Could it be a reporting issue?  Is there anyway to measure CPU speed externally?

---

### Post by tgalati4 on 2014-05-13
I don't have any AMD machines, but for Intel, there are utilities that allow you to select a specific speed or a policy (performance, balanced, powersave, etc).  Some of the utilities allow you to tweak the settings:

tgalati4@Mint14-Extensa ~ $ apt-cache search cpufreq
mate-applets - Various applets for the MATE panel
mate-applets-common - Various applets for the MATE panel (common files)
collectd-core - statistics collection and monitoring daemon (core system)
[B]cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
cpufrequtils - utilities to deal with the cpufreq Linux kernel feature[/B]
gnome-applets - Various applets for the GNOME panel - binary files
indicator-cpufreq - CPU frequency scaling indicator
libcpufreq-dev - development files to deal with the cpufreq Linux kernel feature
libcpufreq0 - shared library to deal with the cpufreq Linux kernel feature
xfce4-cpufreq-plugin - cpufreq information plugin for the Xfce4 panel
xfce4-goodies - enhancements for the Xfce4 Desktop Environment

If it worked in SUSE, then you need to find the module and utilities used to control your dynamic clock then find the equivalents in Ubuntu.  They may not exist.

---

### Post by m-dw on 2014-05-13
I have cpufrequtils,  [COLOR=#000000]gnome-applets and [/COLOR]indicator-cpufreq and their dependencies installed, and I can set the CPU frequency  or governor from the command-line with cpufreq-set.  There's a bunch of interesting files in /sys/devices/system/cpu/cpu0/cpufreq, but none of those files can be written to directly.

```

$ cat bios_limit 
2000000
$ cat cpuinfo_max_freq 
2000000
$ cat scaling_max_freq 
2000000

```

Output of cpufreq-info:
```

david@deskbuntu:~$ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 106 us.
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
  cpufreq stats: 2.00 GHz:32.42%, 1.80 GHz:3.05%, 1000 MHz:64.53%  (1865)

```

It's currently running at 2GHz because I'm transcoding a DVD rip.  It will drop back to 1GHz when it has finished.  What I'd like to be able to do is increase the upper available frequency step to 2100, 2140 or 2200 MHz.  The motherboard is currently set to allow 5% overclocking which should give me a clock speed of 2100MHz but I don't know how to make Linux understand that.

Maybe the kernel is getting the data from the CPU and isn't able to see what the motherboard is capable of?

---

