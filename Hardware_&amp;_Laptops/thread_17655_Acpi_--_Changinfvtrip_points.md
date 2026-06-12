---
title: "Acpi -- Changinfvtrip points"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by Devinci on 2005-03-01
Hi,

How do you change temperature trip points?

```
cat /proc/acpi/thermal_zone/THRM/trip_points

```

```
critical (S5):           100 C
passive:                 92 C: tc1=2 tc2=3 tsp=100 devices=0xdea9d640
active[0]:               68 C: devices=0xdea98980
active[1]:               61 C: devices=0xdea98b00
```

I would like to change active[1] to 51 C.

---

