---
title: "CPU fan monitoring and control"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by mccarthy on 2006-10-04
There isn't much in-depth information out there about lm-sensors, especially when it comes to troubleshooting...

Anyway, my problem is that 'sensors' reports strange info, which may or may not be correct.  This is typical output:

```
joe@MCCARTHY:/proc/acpi$ sensors
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at c800
V1.5:       +1.48 V  (min =  +1.42 V, max =  +1.58 V)   
VCore:      +1.22 V  (min =  +1.76 V, max =  +1.95 V)   ALARM
V3.3:       +3.35 V  (min =  +3.13 V, max =  +3.47 V)   
V5:        +5.18 V  (min =  +4.74 V, max =  +5.26 V)   
V12:      +12.12 V  (min = +11.38 V, max = +12.62 V)   
CPU_Fan:   2282 RPM  (min = 4000 RPM)                     ALARM
fan2:         0 RPM  (min =    0 RPM)                     
fan3:         0 RPM  (min =    0 RPM)                     
fan4:       594 RPM  (min =    0 RPM)                     
CPU:         +47°C  (low  =   +10°C, high =   +50°C)     ALARM  
Board:       +36°C  (low  =   +10°C, high =   +35°C)     ALARM 
Remote:      +36°C  (low  =   +10°C, high =   +35°C)     ALARM  
CPU_PWM:    77
Fan2_PWM:   77
Fan3_PWM:   77
vid:      +1.850 V  (VRM Version 9.1)
```

I'm worried about a few things.  First of all, there are all those ALARMs.  Also, 47 degrees seems hot for an idle CPU.  Also, I don't know why my CPU fan is running almost half of the minimum value, because I had read somewhere that the fan should be at 100% constantly in linux.  How do I set my fan to 100%?  Maybe I've configured sensors wrong and it's reporting the wrong info?

---

### Post by Polygon on 2006-10-04
i believe that without lm-sensors installed and configured, by default the fans run at 100 % all the time in linux/ubuntu. But with lm-sensors installed i think it starts to configure your fans based on  how hot your motherboard and cpu are getting

i know when i configured it, I got a lot of alarms, but usually they were wierd stuff like V core and my -12 and -5 voltages...

the cpu and motherboard tempertatures really just depend on your motherboard. I know for a fact what average temperatures my stuff runs at so i can tell ifs running a bit hot or not.

And i also know that for me, there were 2 cpus (CPU Intel and CPU AMD) listed when i was trying to configure gnome system applet (which uses lm-sensors) and after a few restarts, a new temperature called "temp" appeared and that was my real cpu, and the others i dunno what they were, because they were running at like 20 degrees celsius

and for me at least, 50 degrees celsius is very cool (at least for my cpu) which usuually runs at 65 degrees celsius with BOINC running (something that uses 100 % of idle cpu power, so its always in use)

---

### Post by tommcd on 2006-10-04
Do you have an AMD CPU with cool & quiet enabled in BIOS? If so, the CPU fan will slow down at idle, although with an idle temp of 47C you would think it would spin faster than that. If you want your CPU fan to spin at 100% you could just disable cool  quiet in the BIOS.

---

### Post by mccarthy on 2006-10-05
Thanks for the help.  Most of my worries are gone now.
I do have one more question: how do I change the relation between temp. and fan speed?  I want to make my fan run faster at lower temps.

No, I don't have an AMD CPU

---

### Post by mozetti on 2006-10-05
Check out this [HowTo for fancontrol](http://www.ubuntuforums.org/showthread.php?t=250025&highlight=fancontrol)

---

