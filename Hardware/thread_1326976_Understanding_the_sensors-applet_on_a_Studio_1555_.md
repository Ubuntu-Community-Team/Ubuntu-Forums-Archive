---
title: "Understanding the sensors-applet on a Studio 1555 notebook"
date: 2009-11-14
forum: Hardware
---

### Post by nishant.singh28 on 2009-11-14
I have a Dell Studio 1555 notebook running Karmic 64-bit. Config;
Intel Centrino 2 P8600 2.4 GHz 1066 MHz FSB
2x2 GB DDR2 800MHz
512 MB ATI Radeon Mobility HD 4570
320 GB HDD

Screenshot of sensors applet preferences is attached.
Output of sensors command in terminal:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +100.0°C)                  
temp2:       +58.0°C  (crit = +100.0°C)                  
temp3:       +60.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +100.0°C, crit = +100.0°C)

I understand what core0 and core1 stand for. But I have no idea what the TZ0's and the temp's stand for. Can somebody help?

[Edit] TZ01=temp3 , TZ02=temp2, TZ03=temp1

---

### Post by Yellow Pasque on 2009-11-15
The temps could be anything
- Temp of your northbridge
- Temp of your GPU
- Temp of the CPU
- Garbage data

Look in your BIOS and see if you can get a readout there. Try and match up the temps.
TZ = Thermal Zone, often used by ACPI for fan control

---

