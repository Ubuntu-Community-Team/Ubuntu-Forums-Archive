---
title: "CPU Scaling stuck in &quot;Performance&quot; mode on Lucid Lynx 10.04 using P4 2.0GHz CPU"
date: 2010-06-22
forum: Hardware
---

### Post by FactTech on 2010-06-22
Hello, all,

I've been doing lots of research on this issue but haven't come up with a solution yet. I'm hoping to get a reply from someone familiar with this type of problem who can offer help in diagnosing and/or correcting the problem.

I recently installed a completely fresh instance of Lucid Lynx 10.04 32-bit on a Sony Vaio PCG-GRZ610 laptop. I previously had CPU frequency scaling working on this machine under Hardy Heron 8.04.

When I first tried to install the GNOME CPU scaling applet, it would not allow me to, saying that frequency scaling was unsupported. I installed the cpufreqd and cpufrequtils packages and added the p4_clockmod module to /etc/modules. On reboot, I was able to install the GNOME applet without trouble.

However, I'm finding that, although the applet is active and shows the current speed, it does not actually let me control the CPU speed. I can select what I wish from the drop-down menu, but the applet remains stuck on "Performance" no matter what I do, with the result that the CPU runs as fast as it can at all times (automatically slowing temporarily only for heat-related reasons).

I've tried to directly change the governor setting to "ondemand" using the command line, but it does not respond either using the cpufreq-set command or directly injecting 'ondemand' into /sys/devices/system/cpu/cpu0/cpufreq/scaling-governor.

Strangely, I can get a minor improvement with the following steps:

1) comment out p4_clockmod in /etc/modules
2) reboot and login (CPU scaling applet reports scaling not supported)
3) use terminal to load p4_clockmod ('sudo modprobe p4_clockmod')
4) logout and login (without rebooting)

At this point, the scaling applet allows me to manually set a specific speed (e.g. 750 MHz), but still reverts to the "Performance" governor if I choose any governor setting.

If anyone can offer any insight into this issue, it would be much appreciated.

---

### Post by FactTech on 2010-06-22
for additional information, the output from cpufreq-info and cpuid:


```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 250 MHz - 2.00 GHz
  available frequency steps: 250 MHz, 500 MHz, 750 MHz, 1000 MHz, 1.25 GHz, 1.50 GHz, 1.75 GHz, 2.00 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 250 MHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
  cpufreq stats: 250 MHz:0.00%, 500 MHz:44.61%, 750 MHz:3.07%, 1000 MHz:0.64%, 1.25 GHz:0.19%, 1.50 GHz:0.96%, 1.75 GHz:0.00%, 2.00 GHz:50.53%  (13)
```


```
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 00000f27 00010809 00000400 bfebf9ff
00000002 665b5101 00000000 00000000 007b7040
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 20202020 6e492020
80000003 286c6574 50202952 69746e65 52286d75
80000004 20342029 20555043 30302e32 007a4847

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000f27:
Type 0 - Original OEM
Family 15 - Pentium 4
Extended family 0
Model 2 - 
Stepping 7
Reserved 0

Brand index: 9 [not in table]
Extended brand string: "              Intel(R) Pentium(R) 4 CPU 2.00GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 1

Feature flags bfebf9ff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
51: Instruction TLB: 4KB and 2MB or 4MB pages, 128 entries
5b: Data TLB: 4KB and 4MB pages, 64 entries
66: 1st-level data cache: 8KB, 4-way set assoc, 64 byte line size
40: No 2nd-level cache, or if 2nd-level cache exists, no 3rd-level cache
70: Trace cache: 12K-micro-op, 4-way set assoc
7b: 2nd-level cache: 512KB, 8-way set assoc, sectored, 64 byte line size
```

Note that this is the output from within a session in which I manually loaded the p4_clockmod module; normally the "current policy" line in the cpufreq-info output shows the range as 2.0GHz to 2.0GHz.

---

### Post by GeorgeOfTheBush on 2010-06-22
me too having the same problem.

I have Lucid Lynx 64bit installed.

I had run the update manager yesterday and Everything was working fine.

I shut down the system a few hrs back and later switched ON only to find that **the frequency scaling monitor is [COLOR=Red]stuck at 2 GHz (Performance mode)[/COLOR]**. and I [COLOR=Red]**cannot**[/COLOR] change it.

Another point to mention is that, I am [COLOR=Red]**unable to SHUTDOWN**[/COLOR]. Though I click on SHUTDOWN, I am brought back to the login screen.

Any help is appreciated.

---

### Post by FactTech on 2010-06-22
Found a bug report on Launchpad that seems to match the symptoms perfectly:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706)

I guess the fix is "easy" for a more advanced user than I am. I'll post again if I get more information on how to implement the proposed solution, but if anyone else has any input, I'm definitely open to it.

---

### Post by kabloink on 2010-06-22
It may have something to do with the ondemand script bug.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022")

---

### Post by FactTech on 2010-06-22
> **kabloink said:**
> It may have something to do with the ondemand script bug.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022")

I'm not 100% certain that's an actual bug. The man page for start-stop-daemon ([http://manpages.ubuntu.com/manpages/lucid/man8/start-stop-daemon.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/start-stop-daemon.8.html)) seems to indicate that the "--" in the command is legal, if optional. Regardless, removing it did not change the behavior on my system.

---

