---
title: "lm sensors not displaying all hardware parameters"
date: 2009-01-12
forum: Hardware
---

### Post by cirrusminora on 2009-01-12
I installed lm-sensors on my Lenovo Y series laptop (i use gutsy 7.10) and after installation when i run the "sensors" command i get only the following output..

kumar@kumar-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +53°C  (high =   +85°C) 

now that leaves a lot of other parameters that the package offers like fan speed,RAM consumption and voltages. I've gone through some basic threads on the forum and have tried all i could including answering yes to all sensors-detect questions.Thanks in advance for bailing me out of this.

---

### Post by SnakeHips on 2009-01-12
This guide works for me everytime...

[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm+sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm+sensors)

---

### Post by cirrusminora on 2009-01-12
Thanks for the thread.I followed the howto and it goes fine till I try to load the modules manually using modprobe. I get the following output on giving this command...

kumar@kumar-laptop:~/Desktop$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
kumar@kumar-laptop:~/Desktop$ sudo modprobe i2c-viapro
kumar@kumar-laptop:~/Desktop$ sudo modprobe i2c-isa
kumar@kumar-laptop:~/Desktop$ sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device
kumar@kumar-laptop:~/Desktop$ sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device

And indeed,on the "sensor" command,I'm back at the same point,just two temperatures of my dual core and nothing else.Is it some hardware incompatibility with the Lenovo (Y) laptop I use ? Please advise.

---

### Post by cirrusminora on 2009-01-15
I've moved on to gnome applet which displays temperature.But I'm still looking forward to suggestions for getting the lm sensors working,for the sake of other hardware parameters.Thanks.

---

### Post by zika on 2009-01-15
today I've installed lm-sensors and sensors-applet and enabled Hardware_monitor_(lm-sensors) in my System->Admin->Services. I've added Hardware_sensors_monitor (sensors-applet 2.2.1) to my panel. If I want to change preferences I get the following error:"Error saving sensor configuration". what should I do to correct that?

also, the output of *sensors *in terminal gives:```
~$ sensors
f71882fg-isa-0e80
Adapter: ISA adapter
3.3V:        +3.41 V
Vcore:       +1.26 V  (max =  +2.04 V)   
Vdimm:       +1.87 V
Vchip:       +1.57 V
+5V:         +5.04 V
12V:        +13.96 V
5VSB:        +8.74 V
3VSB:        +3.39 V
Battery:     +3.10 V
CPU:        2712 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +42.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +34.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = thermistor
```how do I enable these "ALARM" values to be shown? fans are working ... ;)

---

