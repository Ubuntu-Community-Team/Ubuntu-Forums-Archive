---
title: "How to find the source of interrupt"
date: 2020-10-26
forum: Hardware
---

### Post by hustjifa on 2020-10-26
I fond one line in /proc/interrupts
```
9:          82341288         0          0          0          0          0          0          0   IO-APIC    9-fasteoi   acpi
```
and in  /sys/firmware/acpi/interrupts/gpe24
```
82341398 enabled
```


What the mean  of 9 and gpe24?
And how to find the source of the interrupt

Thank you very much.

---

