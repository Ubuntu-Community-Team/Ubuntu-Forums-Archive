---
title: "Conky"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by elmnas on 2009-08-28
Hi Guys I have installed im-sensors also conky but what need I to write go get the information of my fans in the conky?
I tried. Please help me out.

Fan1: $alignr${execi 300 /usr/bin/sensors | grep fan1 | cut -c11-18}
Fan2: $alignr${execi 300 /usr/bin/sensors | grep fan2 | cut -c11-18}
HD Temp: $alignr${execi 60 hddtemp /dev/hda | cut -c28-29}C
CPU Temp: $alignr${execi 60 /usr/bin/sensors | grep 'CPU Temp' | cut -c15-16}
MB Temp: $alignr${execi 60 /usr/bin/sensors | grep 'M/B Temp' | cut -c15-16}C


if I wrote sensors in terminal I get.




root@Dapeamel:~# sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.11 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.30 V  (min =  +0.53 V, max =  +3.38 V)   ALARM
AVCC:        +3.30 V  (min =  +1.57 V, max =  +2.30 V)   ALARM
3VCC:        +3.30 V  (min =  +0.14 V, max =  +0.77 V)   ALARM
in4:         +1.42 V  (min =  +0.00 V, max =  +0.26 V)   ALARM
in5:         +1.70 V  (min =  +1.42 V, max =  +0.58 V)   ALARM
in6:         +4.61 V  (min =  +3.69 V, max =  +1.74 V)   ALARM
VSB:         +3.30 V  (min =  +2.30 V, max =  +0.03 V)   ALARM
VBAT:        +3.30 V  (min =  +2.34 V, max =  +3.36 V)   
Case Fan:   1776 RPM  (min = 2636 RPM, div = 8)  ALARM
CPU Fan:    1016 RPM  (min =  649 RPM, div = 16)
Aux Fan:    1061 RPM  (min = 5113 RPM, div = 8)  ALARM
fan5:       1016 RPM  (min =    0 RPM, div = 8)  ALARM
Sys Temp:    +41.0°C  (high =  +1.0°C, hyst = +78.0°C)  sensor = thermistor
CPU Temp:    +41.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.163 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +51.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +49.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +49.0°C  (high = +82.0°C, crit = +100.0°C)  



please help me.

---

### Post by tgeer43 on 2009-08-28
One way to do it would be to direct the output of the 'sensors' command to a file:
```
${execi 300 /usr/bin/sensors > /tmp/sensors.data}
```Then use an awk script or some other method to parse out the values you want, format them, and print them. The output of your script will go right back to conky to be displayed.

tgeer

---

