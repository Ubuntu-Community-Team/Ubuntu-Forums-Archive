---
title: "Temperature and fan speed monitoring for 6600GT"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by rautamiekka on 2007-05-03
Ubuntuguide says that with GKrellM you can monitor temp/fan speed of 6600GT out-of-box but I can't. I've tried to first install lmsensors and configure it, then try again with GKrellM (it was shutted down of course). This is what **sudo sensors** gives

```
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.54 V  (min =  +0.26 V, max =  +0.29 V)       ALARM
+12V:      +5.84 V  (min = +10.82 V, max = +13.19 V)       ALARM
+3.3V:     +1.63 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +4.99 V  (min =  +4.75 V, max =  +5.25 V)
-12V:      -0.60 V  (min = -13.18 V, max = -10.80 V)       ALARM
V5SB:      +5.08 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +2.99 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 42187 RPM, div = 8 )              ALARM
CPU Fan:     0 RPM  (min =   -1 RPM, div = 8 )              ALARM
fan3:     2250 RPM  (min =   -1 RPM, div = 8 )              ALARM
M/B Temp:    +28°C  (high =   +96°C, hyst =    +0°C)   sensor = thermistor     
CPU Temp:  +38.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor     
temp3:     +33.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor     
vid:      +0.275 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled
```

---

