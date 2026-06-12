---
title: "CPU temperature"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by babooka on 2006-11-04
I've got a GigaByte K8U-939. The edgy stock kernel (2.6.17),
does not support the temp sensors, so I've installed 2.6.18.1.


The story is that, sensor and MB BIOS disagree. In bios CPU temp is 35 C, lm-sensors - 60 C.

Who is right? Now I am being paranoid.

Who do you trust BIOS or lm-sensors/i2c?

---

### Post by testube_babies on 2006-11-05
I would go with the lm-sensors number.  35C is pretty low for a CPU, maybe it's the temp of your hard drive?

---

### Post by shunthemask on 2006-11-05
Sorry to be contrary, but I would imagine that your BIOS is correct.  It was coded specifically for your hardware, lm-sensors, not so much.  I have an Athlon XP 2000 that idles at 50C and a Sempron 2800 that idles at 21C, so keep in mind that your specific CPU makes a big difference.  Oh, yeah, almost forgot to add that Arctic Silver is a beautiful thing!

---

### Post by David Corrales on 2006-11-05
It might be 2 different sensors. Some are from the outside of the cpu, there's others inside (accesible via a pin) and chassis ones too.

---

### Post by Devlin67 on 2006-11-05
I have a Gigabyte board with an Athlon64-3200 and I get 32-35. I'd say your BIOS is more accurate.

---

### Post by rbmorse on 2006-11-05
There is quite a difference between 35 (warm) and 60c (hot!).  What does your finger tell you when you touch the heatsink, preferably as close to the bottom as you can reach?

---

### Post by babooka on 2006-11-05
The CPU in question is Athlon 64 X2 4200+. According to the  specs the max temp for it is 65 C, that is the reason I am worried.


The funny thing is that, BIOS show only 2 temp reading - system and cpu.

The hard-drives temperature, I get it with smartctl

$ sudo smartctl -a /dev/hda | grep 194
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       28
$ sudo smartctl -a /dev/hda | grep 194
194 Temperature_Celsius     0x0032   047   253   000    Old_age   Always       -       34


Which is completely different from the sensors readings. 

$ sensors
smsc47m192-i2c-0-2d
Adapter: SMBus ALi 1563 Adapter @ 1400
in0:       +2.56 V  (min =  +0.00 V, max =  +3.32 V)   
in1:       +1.10 V  (min =  +0.00 V, max =  +2.99 V)   
in2:       +3.28 V  (min =  +0.00 V, max =  +4.38 V)   
in3:       +5.13 V  (min =  +0.00 V, max =  +6.64 V)   
in4:      +12.19 V  (min =  +0.00 V, max = +15.94 V)   
in5:       +3.46 V  (min =  +0.00 V, max =  +4.38 V)   
in6:       +1.66 V  (min =  +0.00 V, max =  +1.99 V)   
in7:       +2.39 V  (min =  +2.39 V, max =  +2.39 V)   ALARM
temp1:     +30.0°C  (low  =  -128°C, high =  +127°C)  
temp2:     +51.0°C  (low  =  -128°C, high =  +127°C)  
temp3:     +27.0°C  (low  =    -1°C, high =    -1°C)  
vid:      +1.500 V  (VRM Version 2.4)

---

