---
title: "acpi reports wrong temperature?"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by aethralis on 2008-01-29
Sometimes when I start my laptop (Lenovo 3000 n100) I notice the fan constantly working and acpi -V reports high temperature
```
     Battery 1: charged, 100%
     Thermal 1: ok, 76.0 degrees C
     AC Adapter 1: on-line

```

But the sensors command gives 
```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +40°C  (high =  +100°C)                   

```

And the air from the vent is not warm. After system restart the acpi -V reports normal temperatures. cat * in /proc/acpi/thermal_zone/TZ00 gives now

```

0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             48 C
critical (S5):           102 C
passive:                 87 C: tc1=0 tc2=4 tsp=4 devices=CPU0 CPU1 

```.

What can be the problem?

---

### Post by aethralis on 2008-01-31
Bump. Again the vent is constantly working and temperature sensors (hwmon) gives temp 36, acpi 70. Just switched the laptop on... Strange.

---

