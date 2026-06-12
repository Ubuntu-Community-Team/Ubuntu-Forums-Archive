---
title: "Fan Constantly turning - noisy"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by smartbei on 2006-12-08
I installed Ubuntu on my desktop a month ago, and have noticed since then that the fan has been running constantly - it never slows down or stops. I checked the spu usage, and both cores (Core 2 Duo) register something close to 0.0 nearly always. uptime returns:  

```

$ uptime
12:47:44 up 29 min,  2 users,  load average: 0.04, 0.10, 0.12

```

So CPU usage is pretty minimal. I have tried installing sensors-applet but I am unable to see any information - "No Sensorts found!". The constant fan noise is getting really annoying. Is there any way I can get Ubuntu to recognize the sensors (as I assume that is the problem)?

Hardware:
MoBo: MSI P4M890M
Processor: Core 2 Duo E6300

If more information is needed I will add it.

---

### Post by smartbei on 2006-12-08
I have followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=2780&highlight=i2c+install](http://ubuntuforums.org/showthread.php?t=2780&highlight=i2c+install)
And now running sensors in a terminal returns: 

```
w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min =  703 RPM, div = 128)
CPU Fan:  2518 RPM  (min =  743 RPM, div = 8)
fan3:        0 RPM  (min =  703 RPM, div = 128)
fan4:        0 RPM  (min = 1171 RPM, div = 128)
Sys Temp:    +30°C  (high =    -5°C, hyst =   +63°C)  
CPU Temp:  +28.0°C  (high = -112.0°C, hyst = -112.0°C)  
temp3:     +44.5°C  (high = +80.0°C, hyst = +75.0°C)  
```

I am assuming temp3 is the graphics card...

The problem is, I know for a fact that the case fan IS turning. There also is the power supply fan, though I have no idea whther that is supposed to be included or not. I am still not getting any voltage information, and the fan noise has remained constant regardless.

Thanks in advance for all help on this issue!

---

### Post by tim_c on 2006-12-18
I have the same problem, however Suse 9 and Suse 10 both correctly handle power management correctly, with modulated fan speed. This installed automatically.

ubuntu does not _on the same computer_, suggesting it is to do with the variant of Linux not inherent in Linux. My guess is that a package or something like that is missing from the single CD distribution.

Old SMD system with both CPU showing as active in ubuntu

---

### Post by smartbei on 2007-01-08
Well, I tried SUSE and it appears to have the same problem. The only difference is that in SUSe I am able to see the voltage statistics, which really don't matter to me much... Besides, I finally understand now what people talk about when they mean RPM hell...

From what I understand the problem is that the case fan is not being recognized, as occasionally I can hear the cpu fan speed up if I'm doing something intensive. Any ideas on what to do? Is there a point in trying to install windows to see if it will work fine there?

---

### Post by glabouni on 2007-01-08
are you sure you fan is meant to reduce its rpm in case cpu temperature is low ?

a fan with such a feature should provide a 4 points connector.

if so, have you checked the BIOS? this option could be disabled.

---

### Post by smartbei on 2007-01-08
Actually I have no idea. What should I look for in the bios? According to the CPU temperature sensor my CPU temp is at 33.5C which seems to me pretty low, though I am by no means an expert.

EDIT: Ok, I just restarted and went into the bios. I found a section dealing with the fans, and there was the CPU fan speed and the case fan speed printed. However, the case fan, (as when I type sensors in a terminal) is supposedly at 0RPM (I know for a fact that it is turning). 

I did find one applicable feature - the bios now varies the cpu fan speed according to its temperature - and I set the target at 40. The fan speed is down to 1430RPM, and the noise level is better, and I think the case fan is the problem now. Thanks for the suggestion! Any ideas about what to do about the case fan?

---

### Post by tweedledee on 2007-01-09
> **smartbei said:**
> Actually I have no idea. What should I look for in the bios? According to the CPU temperature sensor my CPU temp is at 33.5C which seems to me pretty low, though I am by no means an expert.

EDIT: Ok, I just restarted and went into the bios. I found a section dealing with the fans, and there was the CPU fan speed and the case fan speed printed. However, the case fan, (as when I type sensors in a terminal) is supposedly at 0RPM (I know for a fact that it is turning). 

I did find one applicable feature - the bios now varies the cpu fan speed according to its temperature - and I set the target at 40. The fan speed is down to 1430RPM, and the noise level is better, and I think the case fan is the problem now. Thanks for the suggestion! Any ideas about what to do about the case fan?

Have you looked here: [http://www.ubuntuforums.org/showthread.php?t=250025](http://www.ubuntuforums.org/showthread.php?t=250025) ?  It provides some suggestsion on how to get correct rpm readings, as well as regulate the speed.  Worked for me.

---

### Post by smartbei on 2007-01-10
Thans for the suggestion, but it returned 
> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed.

I am trying to fiddle with the bios functions I mentioned in the last post - it was at a target temperature of 40 and a tolerance of 3, now I set it at 38 with a tolerance of one, which means that my cpu varies in temperature from 35-42...Is this normal? Will the constant strain on the CPU cause premature failing?

---

### Post by tweedledee on 2007-01-13
> **smartbei said:**
> Thans for the suggestion, but it returned 


I am trying to fiddle with the bios functions I mentioned in the last post - it was at a target temperature of 40 and a tolerance of 3, now I set it at 38 with a tolerance of one, which means that my cpu varies in temperature from 35-42...Is this normal? Will the constant strain on the CPU cause premature failing?

You're not straining your CPU at all, just the fan.  If your fan is constantly changing speeds, it might wear at slightly faster than running a constant speed all the time, but I wouldn't worry about it - I've had fans fail after 2 years of constant high speed use, and still be good after 6 or 7 of the same, so I think the overall manufacturing variability is a much bigger worry.  I find most failures are due to the bearings, and those should wear directly proportional to total use (i.e., changing speeds is better than always max), whereas changing the voltage to regulate the speed is abusing the motor.  But I'm not an expert, perhaps my experience is unusual, so don't bet too much on it.

---

