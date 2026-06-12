---
title: "Which is the correct CPU sensor??"
date: 2008-11-06
forum: Hardware
---

### Post by beumont2 on 2008-11-06
Ok, so I installed lm-sensors and I wanna now how hot is my Core2 Intel E6600

I type $sensors and get the following output:

```
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.42 V
Vcore:       +1.40 V  (max =  +2.04 V)
Vdimm:       +2.14 V
Vchip:       +1.97 V
+5V:         +5.71 V
12V:        +11.60 V
5VSB:        +3.95 V
3VSB:        +3.44 V
Battery:     +3.33 V
CPU:        3759 RPM
System:     2912 RPM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +47.0&#65533;&#65533;C  (high = +85.0&#65533;&#65533;C, hyst = +81.0&#65533;&#65533;C)
                      (crit = +50.0&#65533;&#65533;C, hyst = +46.0&#65533;&#65533;C)  sensor = transistor
System:      +30.0&#65533;&#65533;C  (high = +85.0&#65533;&#65533;C, hyst = +81.0&#65533;&#65533;C)
                      (crit = +100.0&#65533;&#65533;C, hyst = +96.0&#65533;&#65533;C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +72.0&#65533;&#65533;C  (high = +78.0&#65533;&#65533;C, crit = +100.0&#65533;&#65533;C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +70.0&#65533;&#65533;C  (high = +78.0&#65533;&#65533;C, crit = +100.0&#65533;&#65533;C)

```

So CPU is 47C? Why the core are so different 72C and 70C? In Bios a habe only one value. Please explain :)

---

### Post by BUGabundo on 2008-11-06
> **beumont2 said:**
> So CPU is 47C? Why the core are so different 72C and 70C? In Bios a habe only one value. Please explain :)

those are not the CPU... its disk drives!

and they seem quite hot. u better buy some disk fans to lower their tempature

---

### Post by Kevbert on 2008-11-06
+1. if it's possible you need to move the disk drives apart in the case so there is room for the air to flow. If they are stacked one above the other then you need to try to move them apart (if possible).

---

### Post by beumont2 on 2008-11-06
But with HDDTEMP i get 
/dev/sda: ST3500320AS: 31°C
/dev/sdb: HDS728080PLA380: 35°C
/dev/sdc: ST3500320AS: 29°C

Ther are cooled with 1x 120mm FAN.

Core - this points to the CPU. Hdd dont have a CORE :)

---

### Post by beumont2 on 2008-11-06
But with HDDTEMP i get 
/dev/sda: ST3500320AS: 31°C
/dev/sdb: HDS728080PLA380: 35°C
/dev/sdc: ST3500320AS: 29°C

Ther are cooled with 1x 120mm FAN.

Core - this points to the CPU. Hdd dont have a CORE :)

---

