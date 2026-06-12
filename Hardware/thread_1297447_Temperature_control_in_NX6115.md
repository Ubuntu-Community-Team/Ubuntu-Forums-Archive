---
title: "Temperature control in NX6115"
date: 2009-10-21
forum: Hardware
---

### Post by ffg1977 on 2009-10-21
Hi folks.
I have an issue concerning temperature control in a HP NX6115 laptop.
It is a Turion 64 ML-32.
The fan is controlled using a sensor that is not the core temperature sensor. The core sensor communicates with the OS using driver max1617-i2c-0-4c, wich was detected using lm-sensors.
If I run sensors I got:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +37.0°C  (crit = +94.8°C)                  
temp2:       +42.0°C  (crit = +100.0°C)                  
temp3:       +30.7°C  (crit = +100.0°C)                  
temp4:       +50.0°C  (crit = +110.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +31.0°C                                    

max1617-i2c-0-4c
Adapter: SMBus PIIX4 adapter at 8200
Board Temp:  +42.0°C  (low  = -128.0°C, high = +90.0°C)  
CPU Temp:    +49.0°C  (low  = -128.0°C, high = +70.0°C) 
```Running cat /proc/acpi/thermal_zone/*/trip_points
```
critical (S5):           95 C
passive:                 88 C: tc1=1 tc2=2 tsp=100 devices=C000 
active[0]:               80 C: devices=C256 
active[1]:               75 C: devices=C257 
active[2]:               65 C: devices=C258 
active[3]:               58 C: devices=C259 
critical (S5):           100 C
passive:                 90 C: tc1=1 tc2=2 tsp=300 devices=C000 
critical (S5):           100 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=C000 
critical (S5):           110 C
passive:                 110 C: tc1=1 tc2=2 tsp=300 devices=C000
```Running acpi -tc
```
     Battery 0: Full, 99%
     Thermal 0: ok, 50.0 degrees C
     Thermal 1: ok, 30.1 degrees C
     Thermal 2: ok, 41.0 degrees C
     Thermal 3: ok, 36.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Fan 0 of 1
     Cooling 2: Fan 0 of 1
     Cooling 3: Fan 0 of 1
     Cooling 4: Fan 0 of 1
```There is only 1 cooler in the system and it is controlled using 4 steps (Cooling 1-4).
For temp1 > 58°C, cooling 1 turns on. For temp1 > 65, cooling 2 turns on and so them go. But when temp1 ~ 65°C, CPU Temp ~ 77°C and I got only the second fan stage turned on.
I would like to know if is there a way to set acpi to use the right sensor to control fan speed, so my system runs cooler. I don't care about noise or power consumption (this is the next step).
I'm new to Linux and maybe this question is stupid, but I could not find anything like this in the forum.
Thanks in advance.

It looks like temp1 is always 12°C below CPU Temp. Is there a way to change that?
When CPU Temp goes above 80°C, the system freezes.

---

