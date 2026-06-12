---
title: "CPU liquid cooling fan control"
date: 2014-09-21
forum: Hardware
---

### Post by lamb2 on 2014-09-21
Hi,
This computer is running Ubuntu 14.04.1 LTS with KDE on 3.13.0-35-generic (x86_64) with an AMD FX-6300 CPU and a M5A97 R2.0 MOBO. I had an extra CPU cooler, a Antec Kuhler H20 1250 so I installed it on this machine. I have the power plugged into the CPU_FAN on the motherboard. The cooler comes with some .exe software to control fan speeds which works well on Windows 7. When I use Ubuntu the fan speed defaults to low which is 600rpm out of a possible 2500rpm. I don't care if the fan adjusts to temperature. I would just like to increase the fan speed. I tried pwmconfig and it located my CHA_FAN1, CHA_FAN2 and CHA_FAN3 fans but did nothing for my CPU_FAN fan. I then tried plugging in a fan controller to CPU_FAN slot and connecting the power from the cooler to the controller. The knob does adjust the speed of the cooler fans but only from 0rpm-600rpm. Then I tried connecting the fan controller directly to my PSU and connecting the cooler to the controller without the MOBO and still it would only adjust from 0rpm-600rpm. Lastly I tried to use the .exe software through Wine but could not get it to load. Is there anything I can do to increase the rpm on this fan?

---

### Post by john409 on 2015-07-05
Did you ever figure this out? I have a new H100i cooler that i would like to play with

---

### Post by Yellow Pasque on 2015-07-06
> **john409 said:**
> I have a new H100i cooler that i would like to play with

Someone's trying to write a kernel module to control "Corsair Link" devices. [http://forum.corsair.com/v3/showthread.php?t=120092&page=11](http://forum.corsair.com/v3/showthread.php?t=120092&page=11)
I wouldn't buy anything using the proprietary "Corsair Link" protocol if I was running Linux...

---

