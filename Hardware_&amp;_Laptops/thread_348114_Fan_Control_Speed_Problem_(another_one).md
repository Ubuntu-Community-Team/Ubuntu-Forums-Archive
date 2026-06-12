---
title: "Fan Control Speed Problem (another one)"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by salamaza on 2007-01-28
hi
I followed the steps described at

[http://ubuntuguide.org/wiki/Ubuntu_d...8lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_d...8lm-sensors.29)


i`ve detected my speed, temps, and v`s, so far so good. i created the "fancontrol" file, but when i run it i get this(with sudo)


"Some mandatory settings missing, please check your config file!"

i red all the comment, guids here in the forum and in ubuntu guide..but no luck, I have Asus A8n32x sli deluxe (nforce4)

as i sayed everything is detected when i type the word sensors in the terminal, i get 

> root@omio-desktop:/etc/init.d# sensors
it8712-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.39 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VCore 2:   +0.00 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+3.3V:     +3.31 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+5V:       +5.05 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
+12V:     +12.10 V  (min = +16.32 V, max = +16.32 V)   ALARM
-12V:      -3.92 V  (min =  +3.93 V, max =  +3.93 V)   ALARM
-5V:      -13.64 V  (min =  +4.03 V, max =  +4.03 V)   ALARM
Stdby:     +5.05 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
VBat:      +3.09 V
fan1:     1599 RPM  (min =    0 RPM, div = 4)          
fan2:        0 RPM  (min =    0 RPM, div = 128)          
fan3:        0 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +36°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor   
CPU Temp:    +42°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor   
Temp3:      +128°C  (low  =    -1°C, high =    -1°C)   sensor = disabled   





thanks

---

### Post by salamaza on 2007-01-30
*bump*


any ideas ?

---

