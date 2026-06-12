---
title: "Alert and high temperature shutdown but CPU is too cold"
date: 2009-12-08
forum: Hardware
---

### Post by HiB on 2009-12-08
Hi, 

my computer shuts down at around 55°C (131°F). 
If my computers CPU temperature reaches this threshold, i hear a fire alarm sound from the speaker of my mainboard and the computer shuts down immediately. If Iturn the computer on and enter bios right after that, cpu temperature is around 45-50 degrees C. Way too cold for an alert. 

CPU is a Athlon XP-M 2600+ with a max. allowed temperature of 90° C
Mainboard: NF7-S 2.0. 

I suppose that somewhere on my computer a high temperature threshold is set too low, so my computer shuts down at around 55 degrees. But i don't know where else to search. 

I have already looked at my mainboards bios. Threshold there is set at 75 degrees Celsius. 

Maybe there is such a threshold switch set on Ubuntu too? Does anyone have another suggestions? 

I'm using Kubuntu 8.04 (Hardy).

---

### Post by Fnx on 2010-03-07
I have the same processor and Mainboard
I using Kubuntu 8.04 (Hardy) too

$ uname -a 
  Linux orion 2.6.24-27-generic

I have recently experienced automatic thermal shutdown, but it seemed to be for real especially when browsing Flash animation with Firefox. Temperature ramps up quite constantely up to the shutdown temperature

Idle CPU temperature is about 45°C.
Bios warning is at 75°C, automatic shutdown seems to occur at 70°C (disabling the Bios protection did not change much the behavior).


$ cat /proc/acpi/thermal_zone/*/*
returns: 

0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             44 C
critical (S5):           70 C
passive:                 67 C: tc1=4 tc2=3 tsp=60 devices=CPU0
active[0]:               67 C: devices= FAN


I don't know where you can set critical (S5).
Where did you get the max temperature of 90°c for the CPU ?

---

