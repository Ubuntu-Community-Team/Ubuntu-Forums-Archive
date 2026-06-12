---
title: "Temperature showing very high in sensors app"
date: 2018-02-20
forum: Hardware
---

### Post by triplemaya on 2018-02-20
Just want to make sure here. Sensors are listed as 
temp 1
temp 2
temp 1
Physical id 0
Core 0
Core 1
Core 2
Core 3
and the third one is showing 86

Can I assume this is a spurious reading? Everything in the case is apparently very cool. All other sensors are in the 20s

---

### Post by QIII on 2018-02-20
Hello!

By "third one" do you mean the second appearance of "temp1"?

Without knowing the manufacturer and model of the motherboard, it is impossible to track down what component that temperature is associated with and whether it is too high or not -- or whether the sensor app or the onboard sensor is known to produce innacurate readings.

Are you using p-sensor or lm-sensors?

---

### Post by Cavsfan on 2018-02-20
Maybe you could post the output of sensors?
```
cavsfan@cavsfan-le-beast:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +104.0°F  (high = +168.8°F, crit = +212.0°F)
Core 1:      +104.0°F  (high = +168.8°F, crit = +212.0°F)
Core 2:      +100.4°F  (high = +168.8°F, crit = +212.0°F)
Core 3:      +102.2°F  (high = +168.8°F, crit = +212.0°F)


f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.36 V  
in1:          +1.11 V  (max =  +2.04 V)
in2:          +0.92 V  
in3:          +0.76 V  
in4:          +0.98 V  
in5:          +1.10 V  
in6:          +0.91 V  
3VSB:         +3.36 V  
Vbat:         +3.31 V  
fan1:        2222 RPM
fan2:        2835 RPM
fan3:        2712 RPM
fan4:           0 RPM  ALARM
temp1:        +87.8°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +95.0°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +203.0°F, hyst = +195.8°F)  sensor = thermistor
temp3:        +91.4°F  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor



```

Leave off the "-f" if you are not a backwards American and want Celsius. :P

---

