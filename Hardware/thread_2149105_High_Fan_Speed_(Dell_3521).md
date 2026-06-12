---
title: "High Fan Speed (Dell 3521)"
date: 2013-05-27
forum: Hardware
---

### Post by geocool on 2013-05-27
I've just purchased a Dell 3521 notebook with pre-installed windows 8. 
This notebook has switchable graphics with HD 4000 and Ati HD 7670m.
On windows 8 i couldn't even hear the fan when I was doing simple things like programming and browsing the net. 
I could only hear at when I was playing games while I was using the Ati Graphics Card.

On **Ubuntu 13.04** I hear the fan all the time.  Also the CPU temperature is around 60 °C. (checked it with lm-sensors)

One of my guesses was that my cpu is in higher frequency than the frequency that used to be in windows 8 ( usually around 0.8 Ghz ++)
I checked it with /proc/cpuinfo and the frequency was around 700Mhz.

Another guess is that Ubuntu OS uses the ati graphics card,as a result the high temperature and the high fan speed.

So what do you think the problem is ?
Also is there a way to disable the Ati Graphics Card ?
 I tried installing catalyst with the thought that it may have an option but after installing ubuntu started in low graphics mode.

In The Details App: 
```
CPU: Intel® Core™ i5-3337U CPU @ 1.80GHz × 4
Graphics: Intel® Ivybridge Mobile
```

---

### Post by geocool on 2013-05-27
ok I managed to disable VGA by following instructions of this post: [http://ubuntuforums.org/showthread.php?t=2043730](http://ubuntuforums.org/showthread.php?t=2043730)
CPU Temperature decreased by 10°C (Current Temperature Is Around 45°C)

Unfortunately Fan Speed is still High :(

**edid - I Found A Post About Latest Bios Update Of Dell 3521**
> [COLOR=#333333][FONT=Arial]In standard conditions, just windows explorer opened the fan is turn off (0 RPM) and the CPU temperature is betwen a min of 45°C and max of 52°C (46°C mean)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]In a higt stress (1 video, 3/4 streaming windows opened ecc) the fan turn on (2600 RPM) at 55°C and reduced the temperature of CPU about 51-52°C, we didn't find other speeds.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]The fan turn off when the temperature is 46°C.[/FONT][/COLOR]

This means that ubuntu has different method of changing the fun speed than the bios... So, how can we change that ?

**edid-2 - Found A Way To Change Fan Speed**
This site has info of how to load required module to change fan speed. 
[http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/](http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/)
I created a script for my Dell Model. I may share it when its final and tested.

**edid-3 Beta Ruby Script For Fan Speed Moderate**
Download: [https://www.dropbox.com/sh/7ucmkug9lrrimr2/QP8FUqimSU](https://www.dropbox.com/sh/7ucmkug9lrrimr2/QP8FUqimSU)
Instructions And Info: [http://thedreamdev.blogspot.gr/2013/05/cpu-fan-control-for-dell-3521.html]("http://thedreamdev.blogspot.gr/2013/05/cpu-fan-control-for-dell-3521.html#more")

---

### Post by Pedroriel on 2013-08-06
G'day geocool

I have the inspiron 15 3521, and the best I have found is a guy on the dell forums who found a program called vgaswitcheroo, which allowed him to use only one graphics card. That cooled his computer, but fan still goes off to much for him. Does this controller of yours fix the problem? I may try it antway. Don't worry about reply if it works. Thanks 
Pedroriel

---

### Post by Pedroriel on 2013-08-06
I have tried to do this method, but am denied permission right at the start, here [COLOR=#333333][FONT=Arial]chmod -R 705 /sys/kernel/debug. Any ideas?

[/FONT][/COLOR]

---

