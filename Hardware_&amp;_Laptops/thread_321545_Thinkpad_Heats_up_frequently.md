---
title: "Thinkpad Heats up frequently"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by puneit on 2006-12-19
Hello,
I have been using Ubuntu for the past 3 months now  on my IBM Thinkpad R52 series notebook and I have observed quite a large number of times that it actually heats up. 
So, last few weeks I have been trying to figure out if I can somehow increase the fan speed.
The fan's average rpm is 3850 most of the times. Also, I am sure that CPU is close to 800 Mhz as against its full capacity of 1.7Ghz. 
I looked around thinkpad wiki and ended up in disabling all the hotkeys. 
So, can someone suggest me how to increase the fan speed and or at least the CPU frequency should be variable. 
One more thing, when the notebook is switched on, the fan starts at full speed(i can hear the fan sound) and as Ubuntu boots up, the fan speed slows down. 
Moreover, when the notebook is kept in idle mode for a few hours the temperatures reach up to 85C. Usually temperatures hover aroung 60-65C.
The configuration of my machine is
IBM Thinkpad R52 
Model 1847
CPU - 1.7 Ghz
RAM- 512 MB

Ubuntu -Edgy (was using dapper till yesterday, changed to Dapper hoping the problem will go away)
Gnome Desktop

Thanks for reading my post, kindly suggest something
Puneit

---

### Post by xyz on 2006-12-19
Hi,
Mine's OK so...
```
th@luser:~$ sudo hddtemp /dev/hda
/dev/hda: HTS541080G9AT00: 30°C

```
I found this; it's quite a long thread with lots of command lines to determine whether "you have this on or off"...so to speak. You may want to look at it: quite informative, too.
[Laptops overheat]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/22336")

---

