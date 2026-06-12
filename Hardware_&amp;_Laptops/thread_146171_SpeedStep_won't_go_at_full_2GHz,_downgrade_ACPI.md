---
title: "SpeedStep won't go at full 2GHz, downgrade ACPI?"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by siennalizard on 2006-03-17
I've got a Clevo M121W laptop, which had power management problems leading to incorrect temperature readings that caused it to shutdown during boot. I managed to keep most of the ACPI features be recompiling my kernel and leaving out CPU temperature control. That worked fine: SpeedStep was working, and when the power was unplugged, the system would go into a low power consumption mode. The only thing I lost was of course, temperature readings, but there seemed not to be a problem.

I have allowed Ubuntu's updates to continue, thinking I had reached the holy grail of complete Linux compatibility with this hardware. I remember ACPI being upgraded at one point.

After that, I seem to be stuck at a maximum processor speed of 1.20GHz, regardless of the condition of the power supply, and suspend to disk has stopped working, too.

In response I fetched the latest vanilla kernel sources and recompiled with the same options, but that didn't help.

Do you think I should downgrade my ACPI packages, and, if so, how do I go about that? Are old versions kept in the repositary, too?

Cheers,
J.

---

### Post by siennalizard on 2006-03-17
Seems that downgrading the acpi-support package through synaptic's "force version" function solved the standby problem. Still no luck at getting the thing to go faster than 1.2GHz, even burning the CPU with an intensive task.

Ideas much appreciated.
J.

---

