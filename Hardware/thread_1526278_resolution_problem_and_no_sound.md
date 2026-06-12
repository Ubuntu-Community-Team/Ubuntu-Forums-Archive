---
title: "resolution problem and no sound"
date: 2010-07-07
forum: Hardware
---

### Post by raoulz on 2010-07-07
Hello, I recently install Ubuntu 10.04, is pretty much my first experience on Linux, I've tried to install Ubuntu and a couple of other distro before but always end up with same both problems so I gave up and went back to windows :-(. So basically the problems are when I start ubuntu I get a 1600x1200 resolution that is not my screen resolution and cut me half of the desktop, so I try to change it going in system-preferences-monitor and put another one, but every other one i try the display goes all scramble and you can't see anything, that's the main problem, the 2nd one is I got no sound at all, I suppose my sound card is not recognized, I' ve tried to find solutions for both problems reading forums around, but everything I tried never work. I got a gateway laptop mx3228 here is a link to the specs : [http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml) 
thank you for any help

---

### Post by lidex on 2010-07-08
For audio. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
Video:
```
lspci -nn | grep VGA
```

---

### Post by raoulz on 2010-07-08
Ok I finally found a solution evry thing seems working now

here is the key for display

[http://ubuntuforums.org/showthread.php?t=1127987](http://ubuntuforums.org/showthread.php?t=1127987)

and for the sound

[http://ubuntuforums.org/showthread.php?t=1519718](http://ubuntuforums.org/showthread.php?t=1519718)

---

