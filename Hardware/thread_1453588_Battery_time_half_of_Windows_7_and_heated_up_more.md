---
title: "Battery time half of Windows 7 and heated up more"
date: 2010-04-13
forum: Hardware
---

### Post by kdev10 on 2010-04-13
[FONT=Georgia][SIZE=4]Hi everyone, 

I have a Think pad T400 and the battery time is less than half of what i am getting in Windows 7 .  Also the Laptop gets heated up soon,  while running ubuntu 9.1 but that's not the case in windows 7 . 

Is there is some special package i need to download or any tweak or solution for it. 

Please suggest 

Thanks [/SIZE][/FONT]

---

### Post by khelben1979 on 2010-04-13
First off it's good to know about [lm_sensors]("http://en.wikipedia.org/wiki/Lm_sensors").

lm sensors is part of the Linux kernel and it can gather information about your fans in your laptop. Using a package such as ksensors you can see all the rpm speeds of detected fans in your laptop.

To install ksensors:```
sudo apt-get install ksensors
```

[How to control fan speed]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed") allows you to adjust the speed of the fans.

---

### Post by Mark Phelps on 2010-04-13
My guess would be that, under Win7, your CPU is throttling back during idle times.  This will both lower the battery usage and the CPU/system temps.

Looks like Ubuntu 9.10 is NOT doing that, thus, if your CPU is running flat-out all the time, this will create greater battery drain and seriously heat up your CPU/system.

Good luck with lm-sensors and ksensors ... I have an old tablet PC that hasn't worked with an Ubuntu version since 8.04, but on that version, lm-sensors works fine -- and CPU scaling works fine as well.

---

### Post by ada-m on 2010-05-10
I too have a t400 and am very disappointed with the battery life of my 6cell.  I'm lucky to get three hours with a full charge.  A friend of mine suggested powertop, sudo apt-get install powertop.  To run it type in sudo powertop.  I haven't had time to test it yet but that will allow you to view what is causing all of the CPU wake ups.

Hope this helps,
Adam

---

