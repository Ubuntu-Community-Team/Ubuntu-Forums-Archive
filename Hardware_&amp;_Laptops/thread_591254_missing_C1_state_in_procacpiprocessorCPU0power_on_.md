---
title: "missing C1 state in /proc/acpi/processor/CPU0/power on Asus L3D"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by yannek on 2007-10-25
Prolog:
SInce feisty the laptop run a littler warmer and therefore with more fan activity than before (subjective memories).
With gutsy the problems escalated. The fan showed erratic behaviour e.g. turning to full speed if the temp went below 35°, never turning off fully etc. pp.. That was mitigated by editing the DSDT to lower the trippoint that was seemingly meant as "the sensor gives crap" from 35° to 14° and thus preventig the system from falling into failsafe ventilation.
The current status is again: The (cpu) fan is running all the time at low speed. This is annoying yet bearable.

During this whole journey through how tos, /proc and /sys to get hold of the fan I realized perhaps a deeper problem with power and warmth.

Problem:
What ever I changed in the whole time (including going back to a 2.6.20-generic kernel), nevertheless  /proc/acpi/processor/CPU0/power read:
--snip--
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
--snap--
On a DSL4.0 boot with a  2.4.something kernel, and on a dapper liveCD with a 2.6.17 I get something like:
--snip--
active state:            C1
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency ...
--snap--

AFAIK the c-states are possible idle states that the cpu is capable of.
Therfore two questions arise:
1) Are these states in /proc/acpi/processor/CPU0/power idlestates and therefore important for power consumption (=warmth)?
2) Anyway, why did they vanish, whoose fault is it, and how to correct it if it is a bug?

This is a gutsy update from feisty (x86).

---

### Post by yannek on 2007-10-26
Okay a partial self repliey:
To 1):
On [http://www.acpi.info/](http://www.acpi.info/) I found the official ACPI specs and they define the C states as states that the cpu can go into while idling, to reduce energie consumption.
Further:
--snip--
8.1.2 Processor Power State C1
All processors must support this power state. 
--snap--

So there is something wrong. Yet what?

---

