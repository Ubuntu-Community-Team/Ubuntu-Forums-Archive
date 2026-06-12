---
title: "seeking &quot;powertop&quot; explanation"
date: 2011-01-10
forum: Hardware
---

### Post by SaintDanBert on 2011-01-10
I get the following when I run **powertop**
```

prompt$ [color=green]sudo powertop --dump[/color]

Your CPU supports the following C-states : C1 C2 C3 C4 
Your BIOS reports the following C-states : C1 C2 C3 
Cn                Avg residency
C0 (cpu running)        (47.1%)
polling           0.0ms ( 0.0%)
C1 mwait          0.0ms ( 0.0%)
C2 mwait          2.1ms (45.3%)
C3 mwait          0.9ms ( 7.6%)

P-states (frequencies)
Turbo Mode    40.5%
  1.60 Ghz     0.6%
  1200 Mhz     3.6%
   800 Mhz    55.4%

Disk accesses:
Wakeups-from-idle per second : 304.3    interval: 15.0s
no ACPI power usage estimate available

Top causes for wakeups:
  65.4% (449.0)   [kernel scheduler] Load balancing tick
  10.5% ( 72.3)   [Rescheduling interrupts] <kernel IPI>
   4.3% ( 29.6)   [i915] <interrupt>
   4.1% ( 27.9)   plugin-containe
...

```

[highlight]Q1: [/highlight]What does this really mean?
[highlight]Q2: [/highlight]What can I do about the **load balancing tick** that is happening so often?

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-01-18
**bump**

Can anyone help me make sense out of powertop report and explain
what I need to do to improve my battery life?

~~~ 0;-Dan

---

