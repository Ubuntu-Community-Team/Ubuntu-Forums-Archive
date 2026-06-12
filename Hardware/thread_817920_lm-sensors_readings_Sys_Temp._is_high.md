---
title: "lm-sensors readings Sys Temp. is high"
date: 2008-06-04
forum: Hardware
---

### Post by Seinfeld on 2008-06-04
Hi.

I have installed lm-sensors and ran the sensors-detect successfully. Then, added the Hardware Sensors Monitor monitoring applet to my panel to monitor the temperatures on my desktop.
The CPU and the HDD sound reasonable but the problem is, I see that the Sys Temp. is relatively high, triggering the default alarm setting of 68 Celsius. This is the exact "Ambient Temperature" read in my BIOS. It starts at about 51C Celsius and increases till about 70. Is this possible ?? Or this is just a wrong reading ??

I have a well ventilated case with a fan and I am NOT over-clocking the CPU.

I have a DG31PR G31 Intel Motherboard
Intel Core 2 Duo E6850 3GHz. 1333 FSB
One HDD

Here is my readings at Idle afyer 15 min of turn on... I really appreciate if you can explain the terms e.g. "hyst", AUX Temp..etc..


Adapter: ISA adapter
VCore:     +1.12 V  (min =  +0.00 V, max =  +1.74 V ) 
in1:      +10.56 V  (min =  +7.66 V, max =  +8.82 V ).. ALARM
AVCC:      +3.28 V  (min =  +2.64 V, max =  +3.95 V ) 
3VCC:      +3.28 V  (min =  +2.94 V, max =  +3.62 V ) 
in4:       +1.80 V  (min =  +0.60 V, max =  +1.62 V ).. ALARM
in5:       +1.25 V  (min =  +0.10 V, max =  +1.90 V ) 
in6:       +0.31 V  (min =  +3.02 V, max =  +6.12 V ).. ALARM
VSB:       +3.28 V  (min =  +1.46 V, max =  +2.67 V ).. ALARM
VBAT:      +3.65 V  (min =  +3.04 V, max =  +2.06 V ).. ALARM
Case Fan:    0 RPM  (min = 10546 RPM, div = 128 ).. ALARM
CPU Fan:   902 RPM  (min = 1442 RPM, div = 8 ).. ALARM
Aux Fan:     0 RPM  (min = 10546 RPM, div = 128 ).. ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128 ).. ALARM
fan5:        0 RPM  (min = 10546 RPM, div = 128 ).. ALARM
Sys Temp:    +68°C  (high =    +0°C, hyst =  +117°C)  
CPU Temp:  +36.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp: +127.0°C  (high = +80.0°C, hyst = +75.0°C)..   ALARM

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +23°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +22°C  (high =   +85°C)       

Thanks a lot...

---

### Post by Arup on 2008-11-24
I have the same board and running a quad core, I get normal temps as I do in Windows, no different. On windows I use Hardware Monitor from CPUID and in Ubuntu I use GkrellM. Given same room condition and system load, there is only slight variation from Windows and Ubuntu with the later running cooler.

---

### Post by Seinfeld on 2009-05-22
What's your Motherboard brand ??  I have Intel DG31PR.
Also, Do your fans run normally ??

---

### Post by gtmarks on 2009-07-05
I have essentially the same question.  Here are my "sensors" readings:

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.62 V  (min =  +1.69 V, max =  +0.53 V)   ALARM
AVCC:        +3.26 V  (min =  +0.03 V, max =  +1.36 V)   ALARM
3VCC:        +3.26 V  (min =  +0.64 V, max =  +0.10 V)   ALARM
in4:         +0.07 V  (min =  +1.37 V, max =  +1.62 V)   ALARM
in5:         +1.69 V  (min =  +0.27 V, max =  +0.34 V)   ALARM
in6:         +4.71 V  (min =  +3.28 V, max =  +5.25 V)   
VSB:         +3.26 V  (min =  +0.90 V, max =  +1.12 V)   ALARM
VBAT:        +3.25 V  (min =  +2.18 V, max =  +0.22 V)   ALARM
Case Fan:      0 RPM  (min = 5273 RPM, div = 128)  ALARM
CPU Fan:    1973 RPM  (min = 25961 RPM, div = 4)  ALARM
Aux Fan:       0 RPM  (min = 5273 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min =   76 RPM, div = 128)  ALARM
Sys Temp:    +40.0°C  (high = +10.0°C, hyst =  +8.0°C)  ALARM  sensor = thermistor
CPU Temp:    +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.950 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +41.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +46.0°C  (high = +74.0°C, crit = +100.0°C)

I have a P5E WS Professional motherboard and an Intel Q9650 processor.  I also have two extra case fans, one plugged directly into the power supply, the other into the motherboard.  I would expect "sensors" to detect the latter fan, but apparently it does not.  Both fans do seem to be running.

My guess is that the most important number to monitor is CPU Temp (and it would be nice if there were a Web site that gave reliable guidance on safe CPU temperatures).  After installing additional components in my case recently, one of the power supply cables was interfering with the CPU fan, causing the CPU temperature to rise precipitously!  Fortunately, I caught this in time.  My moral is that one should probably also keep an eye on the CPU Fan reading from "sensors" from time to time.

Apologies to the original poster, but I don't know what Sys Temp refers to, or whether it's cause for concern.  Both he or she and I have a rather high AUX Temp reading; again, I don't know if this is a problem.

---

