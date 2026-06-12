---
title: "CPU state is in C0 100% of the time"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by motin on 2007-12-17
Having tried to reduce the power consumption using powertop's diagnostic information and suggestions, I find there is one figure that I cannot do anything about.

When idle, the CPU state "should" be in C4 most of the time, according to various sources including this powertop FAQ: [http://www.lesswatts.org/projects/powertop/faq.php](http://www.lesswatts.org/projects/powertop/faq.php)

Powertop however constantly reports:

C0 (cpu running) (100%)
C1 0,0ms (0%)
C2 0,0ms (0%)
C3 0,0ms (0%)
C4 0,0ms (0%)

This is regardless of number of reported wake-ups per second, even if the computer is started in recovery mode (which results in around 6-9 wakeups per second).

Also, it doesn't matter if I set CPU scaling to conservative, powersave, ondemand or performance.

I have reported this as a bug against powertop here: [https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/176553](https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/176553)

But I suspect it's not powertop's fault, but an ACPI issue. Here is some acpi cpu output:
```
motin@laptop:~$ cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[001] usage[00000000] duration[00000000000000000000]
    C2:                  type[C2] promotion[--] demotion[--] latency[001] usage[00000000] duration[00000000000000000000]
    C3:                  type[C3] promotion[--] demotion[--] latency[085] usage[00000000] duration[00000000000000000000]
    C4:                  type[C3] promotion[--] demotion[--] latency[185] usage[00000000] duration[00000000000000000000]
motin@laptop:~$ acpi -t
     Battery 1: charged, 100%
     Thermal 1: ok, 77.0 degrees C
     Thermal 2: ok, 50.0 degrees C
motin@laptop:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

```

Running latest Gutsy kernel... How can I solve this?

Thanks!

---

### Post by linedpaper on 2007-12-18
I'm having the same issue.  Thus far I have not been able to find a solution.

---

### Post by motin on 2007-12-26
> **linedpaper said:**
> I'm having the same issue.  Thus far I have not been able to find a solution.

Great - maybe you can update the bug report with your experiences?

What CPU do you have? And do you think this is an ACPI issue or merely a presentational bug with powertop?

Cheers!

---

