---
title: "How to retrieve temperature value and other info?"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by damatta on 2008-02-10
Hiya,

I need to retrieve some info from my hardware, such as MB temperature, CPU temperature, fan RPM. I tried installing the software Xsensors but it did not work.  I also issued in the terminal: acpi -t but it complained about not having any support for device "thermal". I find it odd, since in windows Asus probe does this job pretty well with my ASUS P5K SE

If you have any tips I would gladly read

---

### Post by dicecca112 on 2008-02-10
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by damatta on 2008-02-10
Hello, thank you for the link, however i had already tried that and the motherboard temperature is not being displayed.
heres the output for the command sensors:
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.24 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +11.51 V  (min =  +6.76 V, max =  +0.37 V) ALARM
AVCC:      +3.22 V  (min =  +1.06 V, max =  +1.28 V) ALARM
3VCC:      +3.22 V  (min =  +1.20 V, max =  +2.93 V) ALARM
in4:       +1.71 V  (min =  +1.33 V, max =  +0.20 V) ALARM
in5:       +1.70 V  (min =  +1.64 V, max =  +1.34 V) ALARM
in6:       +5.40 V  (min =  +3.10 V, max =  +4.43 V) ALARM
VSB:       +3.22 V  (min =  +0.29 V, max =  +2.83 V) ALARM
VBAT:      +0.29 V  (min =  +2.56 V, max =  +0.62 V) ALARM
Case Fan:    0 RPM  (min =  878 RPM, div = 32) ALARM
CPU Fan:  2766 RPM  (min = 8035 RPM, div = 4) ALARM
Aux Fan:     0 RPM  (min = 8035 RPM, div = 8) ALARM
fan5:        0 RPM  (min = 337500 RPM, div = 4) ALARM
Sys Temp:    +43°C  (high =  +119°C, hyst =   +91°C)  
CPU Temp:  +40.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:   -1.0°C  (high = +80.0°C, hyst = +75.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50°C  (high =  +100°C)                   

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +46°C  (high =  +100°C)                   

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +46°C  (high =  +100°C)

---

### Post by ~Robert~ on 2008-03-06
There is a configuration file /etc/sensors.conf that specifies the labels of the various signals read from the hardware. If your BIOS displays the sensor values you could note down what value relates to what label, and then edit the configuration file to correct the problem. It might be possible that the value displayed as "Sys Temp" is actually the MB Temp.

---

