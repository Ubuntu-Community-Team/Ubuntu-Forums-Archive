---
title: "Jaunty + ati: anyone?"
date: 2009-04-29
forum: Hardware
---

### Post by fipoo on 2009-04-29
Ubuntu Jaunty has been released, ATI also released the new 9.4 Catalyst driver... 
But, I still cant make fglrx driver work!

I have a laptop with an ATI HD2400 M video card.
Yesterday night I downloaded the most fresh image from Kubuntu Jaunty, 
Installed it and then installed the Catalyst 9.4 drivers.
Then ran
```
aticonfig --initial
```
Rebooted and PUF!
Again and again... just before the graphic boot, the only thing I got is a total black screen!

I'm just wondering if someone could help me solving this, it has been many weeks (since march, if I remember) I'm trying to have HW aceleration to run Compiz, games and any stuff that needs them!

---

### Post by madias on 2009-04-29
there are big problems with 9.04 and the ati-drivers. I also tried the manually install of the catalyst 9.4 with same results (laptop ati hd2600, desktop ati 4850): black screen after reboot, sometimes it works for 2-3 times - next reboot: black screen. with the "old" drivers, that are recommended for installation: on hd2600 slow resize of windows (compiz), no working dual screen configuration (4850), and so on...
i just work with the open source driver without compiz (and without ANY problems ;) ), until a new (working) driver release come out. safe your time and do this either.

---

### Post by dulbirakan on 2009-04-29
I have a Radeon 4850. when I install the proprietary drivers provided by Hardware Drivers tool boot time and suspend functions are seriously affected.

The boot time is prolonged by 20-30 seconds and the suspend function fails to resume.

There are also problems with video playback...

I hope a solution will come soon.

---

### Post by emarkay on 2009-04-29
Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

