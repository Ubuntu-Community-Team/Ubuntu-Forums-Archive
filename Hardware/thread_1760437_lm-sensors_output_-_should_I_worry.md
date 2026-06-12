---
title: "lm-sensors output - should I worry?"
date: 2011-05-16
forum: Hardware
---

### Post by ikester8 on 2011-05-16
I've been trying to diagnose the cause of my Dual core Intel Pentium D system shutting down in the middle of processor-heavy applications. It also refuses to reboot immediately; takes a few minutes to restart, so I'm pretty sure I have a heat issue. lm-sensors came up with this:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +30.0°C  (crit = +110.0°C)                  

w83627dhg-isa-0a10
Adapter: ISA adapter
Vcore:       +1.29 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.90 V  (min =  +1.44 V, max =  +1.02 V)   ALARM
AVCC:        +3.39 V  (min =  +2.98 V, max =  +3.63 V)   
+3.3V:       +3.38 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.62 V  (min =  +0.58 V, max =  +1.83 V)   
in5:         +1.69 V  (min =  +0.02 V, max =  +0.94 V)   ALARM
in6:         +1.62 V  (min =  +1.51 V, max =  +1.70 V)   
3VSB:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.06 V  (min =  +2.70 V, max =  +3.30 V)   
fan1:          0 RPM  (min =  150 RPM, div = 128)  ALARM
fan2:       1308 RPM  (min =  803 RPM, div = 8)
fan3:          0 RPM  (min =   99 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +39.0°C  (high = +15.0°C, hyst = -59.0°C)  ALARM  sensor = thermistor
temp2:        +7.5°C  (high =  -0.5°C, hyst =  -1.0°C)  ALARM  sensor = diode
temp3:        -1.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
```

Some of these look scary, but I'm not sure what exactly they are measuring. Does it look like the mobo needs replacing?

---

### Post by jerrrys on 2011-05-17
you have 4 fans it looks like only one is running. as for the overvolts...

---

### Post by mcduck on 2011-05-17
actually that just looks like you haven't actually configured lm-sensors at all. Which is why all the sensor data might not be mapped to right outputs,all the min/max limits are rather insane, and it also seems some of the sensor data isn't even calculated properly.

Lm-sensors isn't something one can just install and start using, it doesn't know what is the correct way to interpret the raw sensor data your motherboard's sensor chip sends. You have to configure that yourself by editing the /etc/sensors.conf file to tell it which sensor should be used for what value, what the preferred limits are and if the raw sensor data should have some multiplier/divider (or other formula) to convert it to real value.

Anyway, I obviously don't have much information about your system, or any data to compare the lm-sensors output with, but 'd say the voltages look fine, missing fan speeds can be ignored (you either don't have such fans or they don't provide RPM info) and the only working temperature sensor is temp1, the other values (temp2 & temp3) are clearly incorrect or don't work at all. Either way, everything seems to be just fine. The voltages are within standard limits and 39C isn't a bad CPU temperature at all.

Still, if you are suspecting temperature issues, you should check that with some other program, or preferably your computer's BIOS. You'll need the info some other tool anyway as reference to configure lm-sensors properly.

---

### Post by ikester8 on 2011-05-17
Thank you, McDuck. I will work with the config file to try to make sense of this. Indeed, there seems to be only one fan on the CPU. I'll keep working on it.

---

