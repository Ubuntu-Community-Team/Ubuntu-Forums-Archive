---
title: "Sensors Output"
date: 2010-09-05
forum: Hardware
---

### Post by spandey on 2010-09-05
I have 10.04 installed and working fine. The sensors output Voltages are not correct. It's correct in BIOS.How to rectify it?

spandey@spandey-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +76.0°C, crit = +100.0°C)  

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:       +1.14 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.61 V  (min =  +1.90 V, max =  +1.76 V)   ALARM
AVCC:        +3.36 V  (min =  +2.98 V, max =  +3.63 V)   
VCC:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.82 V  (min =  +0.51 V, max =  +0.06 V)   ALARM
in5:         +1.26 V  (min =  +1.72 V, max =  +1.21 V)   ALARM
in6:         +0.10 V  (min =  +1.92 V, max =  +0.21 V)   ALARM
3VSB:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.18 V  (min =  +2.70 V, max =  +3.30 V)   
fan1:          0 RPM  (min = 1917 RPM, div = 64)  ALARM
fan2:        874 RPM  (min =  760 RPM, div = 
fan3:          0 RPM  (min = 1004 RPM, div = 64)  ALARM
fan4:          0 RPM  (min = 7336 RPM, div =   ALARM
fan5:          0 RPM  (min = 28125 RPM, div =   ALARM
temp1:       +42.0°C  (high = +127.0°C, hyst = +78.0°C)  sensor = diode
temp2:       +29.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:      +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +2.050 V

spandey@spandey-desktop:~$

---

