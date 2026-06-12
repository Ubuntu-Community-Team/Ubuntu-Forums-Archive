---
title: "Sony C series 13&quot; Fan constantly spinning"
date: 2011-09-04
forum: Hardware
---

### Post by david35k on 2011-09-04
Dear,

The Sony VPCCA1C5E fans are constantly spinning on Ubuntu 11.04. 

First, the laptop shut down randomly when plugged when external temperature is approaching 30°C, while laptop on battery is stable. 

There is no direct access to fancontrol, but sensors gives internal temperature to 48°C, this is not so high.

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +96.0°C)                  
temp2:       +48.0°C  (crit = +96.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +86.0°C, crit = +100.0°C) 

I tried to check the temperature of the GPU :

$ aticonfig  --od-gettemperature

Default Adapter - AMD Radeon 6600M and 6700M Series
                  Sensor 0: Temperature - 46.00 C

I tried to fix the CPU and GPU to minimal frequency scaling. The issue remains. Any ideas ?

---

