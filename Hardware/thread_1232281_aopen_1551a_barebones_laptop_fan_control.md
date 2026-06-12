---
title: "aopen 1551a barebones laptop fan control"
date: 2009-08-05
forum: Hardware
---

### Post by mtucker2 on 2009-08-05
Hello, 

 I have a Hi-Grade Notrino C2200 laptop which is a re branded Aopen 1551a Barebones laptop. The problem I'm having is after installing ubuntu (9.04) due to the intel graphics drivers crashing windows, the cpu fan seems to be constantly set to minimum speed. This is causing the laptop to run extremely hot - it got to 90 degrees C last night.

 All I can establish from the Aopen website is it has 855gme and ICH4 chips from Intel, I know the graphics part of the 855gme chip seems to be dodgy as after installing the intel graphics driver on windows xp (after a disk format, worked fine before the format) it'll work for a few minutes and then the screen will freeze into a checker board style pattern - but I'm not sure if this would cause the fan speed not to work either. I have also noticed the fan speed sometimes goes high just before it switches off, so I'm assuming the OS gives control back to the BIOS? 

 I have tried installing lm-sensors and running sensors-detect but that came back with nothing found. I also tried i8k which loaded fine under the force flag but I have since discovered this is just for Dell laptops (and after getting a log file of output from it, it isn't reading temperature or fan speed, most are negative 1s). I then installed qgkrellm and it seems it has no fan speed sensors either, but it does have cpu temp sensors which is how I found out it got to 90 degrees last night. 
 
 Has anyone got any suggestions please, I don't really want to cook my cpu... 

Marlon

---

