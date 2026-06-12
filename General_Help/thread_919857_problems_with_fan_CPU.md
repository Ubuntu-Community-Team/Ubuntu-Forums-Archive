---
title: "problems with fan CPU"
date: 2008-09-14
forum: General Help
---

### Post by Sidus on 2008-09-14
hi all
i'm italian and i from Rome.
i'm young user of linux -> kubuntu
unfortunately i have problems with fancontrol CPU and i have follow these tutorials
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
and
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

	
but I can not say that after the 50° must start the fan at maximum RPMs

this is my sensors
```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.18 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +12.14 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:        +3.31 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VCC:        +3.31 V  (min =  +1.02 V, max =  +2.59 V)   ALARM
in4:         +1.22 V  (min =  +0.06 V, max =  +0.00 V)   ALARM
in5:         +1.61 V  (min =  +0.03 V, max =  +0.02 V)   ALARM
in6:         +3.84 V  (min =  +0.82 V, max =  +0.00 V)   ALARM
VSB:         +3.31 V  (min =  +0.02 V, max =  +0.00 V)   ALARM
VBAT:        +3.23 V  (min =  +0.53 V, max =  +1.02 V)   ALARM
Case Fan:      0 RPM  (min = 10546 RPM, div = 128)  ALARM
CPU Fan:    1022 RPM  (min = 168750 RPM, div = 8)  ALARM
Aux Fan:       0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +35.0°C  (high =  +1.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU Temp:    +40.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.338 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (crit = +85.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (crit = +85.0°C)
```

and this is my /etc/fancontrol

```
INTERVAL=10
FCTEMPS=hwmon0/device/pwm2=hwmon0/device/temp1_input
FCFANS= hwmon0/device/pwm2=hwmon0/device/fan2_input
MINTEMP=hwmon0/device/pwm2=35
MAXTEMP=hwmon0/device/pwm2=50
MINSTART=hwmon0/device/pwm2=150
MINSTOP=hwmon0/device/pwm2=125
MINPWM=hwmon0/device/pwm2=100
MAXPWM=hwmon0/device/pwm2=150

```

	
I'm crazy and that the whole afternoon trying to make it work

sorry for my english, is very ****
please help me, i'm despair

---

