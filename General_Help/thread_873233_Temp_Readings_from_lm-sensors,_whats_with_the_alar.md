---
title: "Temp Readings from lm-sensors, whats with the alarm?"
date: 2008-07-28
forum: General Help
---

### Post by Ponomous on 2008-07-28
hey i ran the sensors command and this was my output...


```
lm78-i2c-1-28
Adapter: SMBus nForce2 adapter at f000
VCore 1:     +2.24 V  (min =  +0.00 V, max =  +3.49 V)   
VCore 2:     +2.99 V  (min =  +1.63 V, max =  +3.65 V)   
+3.3V:       +3.26 V  (min =  +0.77 V, max =  +2.69 V)   ALARM
+5V:         +5.48 V  (min =  +0.86 V, max =  +0.05 V)   ALARM
+12V:        +8.27 V  (min =  +1.40 V, max =  +5.65 V)   ALARM
-12V:       -10.96 V  (min =  -7.40 V, max =  -0.33 V)   ALARM
-5V:         -5.51 V  (min =  -1.83 V, max =  -3.71 V)   ALARM
fan1:          0 RPM  (min = 168750 RPM, div = 8)  ALARM
fan2:       1962 RPM  (min = 1757 RPM, div = 8)  ALARM
fan3:       6192 RPM  (min = 9926 RPM, div = 2)  ALARM
temp1:       +18.0°C  (high =  +0.0°C, hyst = +127.0°C)  ALARM  
cpu0_vid:   +3.000 V

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +9.87 V  (min =  +5.39 V, max = +12.04 V)   
AVCC:        +3.26 V  (min =  +0.77 V, max =  +2.69 V)   ALARM
3VCC:        +3.26 V  (min =  +0.51 V, max =  +0.03 V)   ALARM
in4:         +1.09 V  (min =  +0.18 V, max =  +0.74 V)   ALARM
in5:         +1.58 V  (min =  +1.06 V, max =  +0.05 V)   ALARM
in6:         +5.86 V  (min =  +1.95 V, max =  +3.94 V)   ALARM
VSB:         +3.26 V  (min =  +2.77 V, max =  +0.43 V)   ALARM
VBAT:        +3.04 V  (min =  +3.22 V, max =  +0.62 V)   ALARM
Case Fan:      0 RPM  (min = 10546 RPM, div = 128)  ALARM
CPU Fan:    1962 RPM  (min = 1757 RPM, div = 8)
Aux Fan:    6192 RPM  (min = 9926 RPM, div = 2)  ALARM
fan4:          0 RPM  (min = 1318 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +18.0°C  (high =  +0.0°C, hyst = +127.0°C)  sensor = diode
CPU Temp:    +32.5°C  (high = +127.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
AUX Temp:    +32.0°C  (high = +127.0°C, hyst =  +0.0°C)  sensor = thermistor
cpu0_vid:   +1.950 V

```

everything look ok?  i see all of the alarms and the data ranges seem way out of wack but im not really 100% sure of what i am looking at.  Let me know if you need any more data.

---

### Post by ModelM on 2008-07-28
The alarms are always way out of whack until you set them.

Those min & max values are the acceptable value range for each reading. You set them in the config file. You haven't set them yet, so they're goofy. You'll see an alarm at each reading in which the current reading is outside the acceptable value range. Until those acceptable value ranges (or alarm ranges, if you prefer) are set, the alarms mean nothing.

---

### Post by Ponomous on 2008-07-29
ok haha that makes me feel better.  I just need to go back in and set them.  The actual values look ok i think.  32.5 for cpu 18 for system.  not to bad. how accurate are these readings?

---

### Post by ModelM on 2008-07-29
The accuracy of the voltage readings are easily within a few hundred millivolts - for the purpose here they can be considered spot on. Most folks set the min/max values of these to plus or minus 5%. This will alert you to a possibly bad rail before things go too far.

The temp readings are highly dependent on the exact location & type of sensors. The best way to deal with them is simply to watch them over a period of time & get a "feel" for how your machine runs.

---

### Post by Ponomous on 2008-07-29
Thanks  a bunch

---

