---
title: "[SOLVED] What is &amp;quot;hyst&amp;quot;"
date: 2008-10-27
forum: General Help
---

### Post by Bruce M. on 2008-10-27
Hi Folks,

When I run "sensors" I get an output that includes a term "hyst".
```
bruloo@bruloo:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +56.0°C                                    

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.39 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.59 V  (min =  +9.18 V, max =  +0.24 V)
+3.3V:       +3.14 V  (min =  +1.47 V, max =  +3.98 V)
+5V:         +4.91 V  (min =  +5.97 V, max =  +4.59 V)
-12V:       -11.87 V  (min = -13.10 V, max = -13.59 V)
V5SB:        +5.03 V  (min =  +1.10 V, max =  +1.96 V)
VBat:        +3.01 V  (min =  +1.01 V, max =  +3.09 V)
fan1:          0 RPM  (min = 168750 RPM, div = 2)
CPU Fan:    168750 RPM  (min =   -1 RPM, div = 8)
fan3:       4963 RPM  (min = 9926 RPM, div = 2)
M/B Temp:    +37.0°C  (high = +28.0°C, **hyst** =  +8.0°C)  sensor = thermistor
CPU Temp:    +49.0°C  (high = +80.0°C, **hyst** = +75.0°C)  sensor = thermistor
temp3:       +19.0°C  (high = +80.0°C, **hyst** = +75.0°C)  sensor = diode
cpu0_vid:   +0.000 V
beep_enable:enabled
```
Anyone have any idea what that means?

Chimo!
Bruce

---

### Post by jespdj on 2008-10-27
It most likely means [hysteresis](http://www.lassp.cornell.edu/sethna/hysteresis/WhatIsHysteresis.html).  But what it actually indicates in this context, I don't know.

---

### Post by tCarls on 2008-10-27
It's short for hysteresis. An alarm goes on when the temperature reaches the "high" value and doesn't go off until it falls below the "hyst" value.

---

### Post by Bruce M. on 2008-10-27
> **tCarls said:**
> It's short for hysteresis. An alarm goes on when the temperature reaches the "high" value and doesn't go off until it falls below the "hyst" value.

That's what I need to know.  Thank you!

Chimo!
Bruce

---

