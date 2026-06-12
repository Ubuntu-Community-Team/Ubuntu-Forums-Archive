---
title: "Sensor issue on satellite A100"
date: 2010-07-06
forum: Hardware
---

### Post by lehibou on 2010-07-06
Hello

I'm the proud owner of a toshiba satellite A100-483 (with a phoenix bios) running on Lucid (10.04). I just wanted to be able to read my cpu fan actual speed and to tune it. ```
$Sensors-detect
``` only find one sensor : "coretemp" 
cf results :

```

#----cut here----
# Chip drivers
coretemp
#----cut here----
```and the ```
$ sensors
``` only gives few temperatures : no voltage no fan speed as I see in some other thread :
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +106.0°C)                  
temp2:       +49.0°C  (crit = +96.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +44.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +49.0°C  (crit = +85.0°C)     
```I installed omnibook which gives an info on the fan speed but it doesn't change with change of fan activity :
```
$ cat /proc/omnibook/fan
```gives :
```
Fan is on (level 9)
```even if the fan speed is low or high.


Does anyone know if it is caused by a misconfiguration or just a lack in my laptop capacities.


I would be realy pleased if someone help me to fix this.

Thank you in advance for the time you take to read me.

Lehibou
PS please excuse my poor english (I'm french)

---

