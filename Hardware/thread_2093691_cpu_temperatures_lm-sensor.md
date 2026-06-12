---
title: "cpu temperatures/ lm-sensor"
date: 2012-12-11
forum: Hardware
---

### Post by nalsanj on 2012-12-11
i have a desktop intel i3 processor with ubuntu P. i installed lm-sensors and did 'sensor detect' and after that did 'sensor'. the report is below. some sensors are detecting temperatures out of healthy range and fan speed = 0. But i dont understand the implications. i think i have one fan connected to the board - the CPU. the rear fan is connected directly to the smps and not the board.


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +34.0°C  (high = +89.0°C, crit = +105.0°C)
Core 2:       +34.0°C  (high = +89.0°C, crit = +105.0°C)

w83627dhg-isa-0a10
Adapter: ISA adapter
Vcore:        +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +0.75 V  (min =  +1.99 V, max =  +1.99 V)  ALARM
AVCC:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.36 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.30 V  (min =  +0.90 V, max =  +1.77 V)
in5:          +0.76 V  (min =  +1.15 V, max =  +0.90 V)  ALARM
in6:          +1.06 V  (min =  +0.94 V, max =  +2.03 V)
3VSB:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.36 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan2:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan3:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan5:           0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:        +38.0°C  (high = -121.0°C, hyst =  +9.0°C)  ALARM  sensor = diode
temp2:        +42.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:    +2.050 V
intrusion0:  OK

radeon-pci-0100
Adapter: PCI adapter
temp1:        +70.0°C 

Can someone help out?

---

