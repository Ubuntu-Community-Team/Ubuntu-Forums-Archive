---
title: "CPU Temperature"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by RobbanG on 2007-05-28
Hello all
Im trying to lower my CPU Idle temperature and fan speed but i dont know where to start. The thing is running windows xp idle the CPU is about 42C and the fan 1700rpm but running Kubuntu Festy Idle the CPU is 49C and the fan 3000rpm. Im trying to figure out how to make my CPU use the other C-states when Idle but i dont know how to do it. 

cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:

This tells me it never changes states, anybody have any idea?
Thanx

---

### Post by r0ydster on 2007-05-28
Is this a Laptop? or a standalone? Dual core cpu?  

Which kernel are you running? 

My results on my Dual Core laptop:
acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 40.0 degrees C
  AC Adapter 1: on-line


------------------------------------------------------------
                CPU 0
------------------------------------------------------------
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00628408] duration[00000000003560182191]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[04796615] duration[00000000034388555266]
------------------------------------------------------------
                CPU 1
------------------------------------------------------------
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00476980] duration[00000000001840506391]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[06841693] duration[00000000036123613471]

I have 3 possible states - C3 is idle, C0 is max load.

I haven't upgraded to Feisty 7.04 yet, here is my kernel:

Linux mike-laptop 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686 GNU/Linux


Run this command and post the output:

```
cat /proc/acpi/processor/CPU0/info
```


MIke

---

### Post by RobbanG on 2007-05-29
Its a old desktop Athlon xp2100.

cat /proc/acpi/processor/CPU0/info

processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

Does this mean it cannot change the C-state or maybe i have to install or configure something? I mean it has to be possible to make my CPU run cooler when Idle. In windows xp i had to enable the hlt-instuction manually using a tool WPCREDIT to change some PCI Configuration Registers. Is it possible to make something similar?

The kernel is:
Linux ubuntu 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

---

