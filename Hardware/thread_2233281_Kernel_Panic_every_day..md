---
title: "Kernel Panic every day."
date: 2014-07-07
forum: Hardware
---

### Post by lrouxc4 on 2014-07-07
Hi all, 

I have been getting a kernel panic on average once a day for a month or so. The machine just switches to a black screen and automatically reboots after 30 seconds (screenshot attached)


My laptop is a Samsung Series 9 NP900X3C.

> ZZZ@zzz-ultrabook:~$ uname -a
Linux zzz-ultrabook 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

My mcelog shows:

> mcelog: failed to prefill DIMM database from DMI data
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 4
TIME 1404757006 Mon Jul  7 20:16:46 2014
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: Internal unclassified error: 402
STATUS b200000000100402 MCGSTATUS 0
MCGCAP c07 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 58

The problem is intermittent. It is not a memory issue, I have run a proper memtest and it did not find anything.
I did not find a solution using Google.

Could anyone help me to debug this issue further, please. 

I am not convinced this is a hardware error as the laptop was stable for long before (running ubuntu 13.10)

---

### Post by tgalati4 on 2014-07-07
It is possible that you have a memory error in the cache.  A 4-core machine will have a 4-way associated (shared) cache and it seems that all 4 cores are choking.  In fact, the same memory address is called out by all for CPU's.  Sometimes this cache is called L3, where L1 and L2 caches reside with each processor core--it depends on the specific chipset.

[https://software.intel.com/en-us/articles/intel-performance-counter-monitor-a-better-way-to-measure-cpu-utilization#cpu_utilization](https://software.intel.com/en-us/articles/intel-performance-counter-monitor-a-better-way-to-measure-cpu-utilization#cpu_utilization)

If you think it is a kernel issue, then grab an older distro and boot off of a USB drive and see how stable the machine is.  I don't think memtest tests on-die cache.  It simply reports the amount of cache.  Memtest does a comprehensive test of RAM, which is off of the CPU die.  If you have an error in L3 cache, then you may see the errors that you have posted.  I have never seen those types of hardware errors, so I am just guessing.  If it was just a single core memory issue, then only a single core would report the problem.

There may be some Intel-specific diagnostics that you can run to troubleshoot further.  But try the older distro first.  If you have an issue with 13.10, then you know you have developed an unfortunate hardware fault.

If you experience the problem with an older kernel, then it is time to declock the computer and run it at a slower speed--if your BIOS allows it.

---

### Post by lrouxc4 on 2014-07-15
It seems my month long issues have been sorted out (fingers crossed) by uninstalling the software centre version of virtualbox and installing the newest version from oracle (4.3.12).

---

### Post by swata on 2014-12-01
Hi,

I also had the same issue with my HP server and got the solution for my issue [here]("http://expertisenpuru.com/reboot-after-panic-server-rebooted-automatically-in-hp-ux/")

---

