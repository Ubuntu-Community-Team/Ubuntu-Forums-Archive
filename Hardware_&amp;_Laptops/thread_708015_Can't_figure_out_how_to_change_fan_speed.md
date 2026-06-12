---
title: "Can't figure out how to change fan speed"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by messybricks on 2008-02-25
Hey all.  

I have installed lm-sensors on my desktop (7.04) and my laptop (7.10), and all the measurements I get are over 120F.  I would like to increase the fan speeds to lower this temperature, and I could do it in Windows with SpeedFan.  Can I use lm-sensors to increase fan speeds?  Or is there an easier way?

My BIOS doesn't do it, and I have tried running "sensors" in the terminal, but it says it doesn't find any, and I go through the default options under "sensors-detect", and it seems to find some, but then I run "sensors" again and it can't find it.  I am confused at this.

---

### Post by messybricks on 2008-02-25
update:  I just got the "sensors" command to do something by typing "sudo modprobe w83627hf", because that's my chipset.

here's what I get from "sensors":

> w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.65 V  (min =  +0.32 V, max =  +2.13 V)              
+3.3V:     +3.31 V  (min =  +2.32 V, max =  +0.19 V)       ALARM  
+5V:       +4.92 V  (min =  +0.99 V, max =  +2.31 V)       ALARM  
+12V:     +10.94 V  (min =  +0.06 V, max =  +0.24 V)       ALARM  
-12V:      +0.14 V  (min = -13.59 V, max = -11.95 V)       ALARM  
-5V:       +5.10 V  (min =  -5.95 V, max =  -6.91 V)       ALARM  
V5SB:      +5.46 V  (min =  +4.35 V, max =  +0.11 V)       ALARM  
VBat:      +3.25 V  (min =  +0.00 V, max =  +1.06 V)       ALARM  
fan1:        0 RPM  (min = 9926 RPM, div = 2)              ALARM  
fan2:        0 RPM  (min = 3443 RPM, div = 2)              ALARM  
temp1:       +35°C  (high =   +58°C, hyst =   +13°C)   sensor = thermistor           
temp2:     +46.5°C  (high =   +70°C, hyst =   +50°C)   sensor = diode           
alarms:   
beep_enable:
          Sound alarm disabled



I still can't figure out how to change the fan speed though...

---

