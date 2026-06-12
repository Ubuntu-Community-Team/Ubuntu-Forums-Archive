---
title: "lm-sensors reports cpu fan =  0 rpm"
date: 2009-04-09
forum: Hardware
---

### Post by AVH on 2009-04-09
Lm- sensors reports that my cpu fan is at 0 rpm which is wrong because I can see it running. I have an Asus P4S800D-X  MB and lm-sensors is set to use the w83627hf driver. Here is the output of 'sensors'. Most of it  seems to be correct and the cpu fan speed is the only error I really care about. Fan1 is the case fan, the cpu fan runs about 1550 rpm

```
alan@alan-u-livingroom:~$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.44 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.04 V  (min = +10.03 V, max =  +7.60 V)
+3.3V:       +3.30 V  (min =  +3.79 V, max =  +1.15 V)
+5V:         +5.01 V  (min =  +3.25 V, max =  +5.73 V)
-12V:        +6.06 V  (min =  -9.81 V, max =  -3.15 V)
V5SB:        +5.05 V  (min =  +3.31 V, max =  +2.50 V)
VBat:        +0.13 V  (min =  +4.05 V, max =  +4.00 V)
fan1:       2360 RPM  (min = 1569 RPM, div = 4)
CPU Fan:       0 RPM  (min = 8035 RPM, div = 2)
fan3:          0 RPM  (min =   93 RPM, div = 128)
M/B Temp:    +30.0°C  (high =  -1.0°C, hyst =  -3.0°C)  sensor = thermistor
CPU Temp:    +41.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +5.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled

```

---

### Post by dabl on 2009-04-09
I don't think it's reading the fans at all.  I have the same problem on my Intel mobo -- it's a disappointment.

---

