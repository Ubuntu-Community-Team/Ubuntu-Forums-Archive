---
title: "acpi and lm-sensors question"
date: 2008-11-11
forum: General Help
---

### Post by brandon88tube on 2008-11-11
I wanted to know if this output was strange because the temperature NEVER changes from 0.0 degrees C.
```
$ acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 0.0 degrees C
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 10

```

Also I find this output to be the same as it never changes from 0.0 degrees C
```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +94.0°C)
```

Can anyone tell me why they refuse to read the temperature?

---

### Post by brandon88tube on 2008-11-11
Anyone?

---

### Post by brandon88tube on 2008-11-12
Seriously, come on, can anyone help me out here?

---

### Post by brandon88tube on 2008-11-13
If I don't get a reply after this bump I will try and ask elsewhere.

---

