---
title: "Slower fglrx performace with Ubuntu 11.10?"
date: 2011-11-29
forum: Hardware
---

### Post by angryfirelord on 2011-11-29
Hello all,

I'm just trying to get some input about the performance of the fglrx drivers in Ubuntu. I noticed this when I was testing two distributions on it.

In 11.10, I downloaded and ran a game called AssaultCube. Now, this game isn't very demanding (it can run on Pentium-III style hardware), so anything modern will be playable with ease. On my onboard Radeon 4250, I was getting around 90-110 FPS using the drivers in the repository. I was also using Unity 2D desktop.

However, under a copy of Scientific Linux 6.1 using the ElRepo fglrx drivers, I was hitting the FPS cap easily, which was 200 FPS. The setup was exactly the same, no changes were made to the resolution and graphical detail.

So, I'm wondering if anyone else has noticed this drop. Granted, this was only one test, which isn't enough to draw a trend, but having your FPS cut in half is a significant difference. I'd like to know if the issue is with Ubuntu's default configuration, with the fglrx driver and unity, or perhaps with the newer Linux kernel.

Thanks!

---

### Post by ajgreeny on 2011-11-29
You will find many complaints in these forums and across the web related to the major problem of 11.10 and the ATI/AMD fglrx driver.  I gather that ATI are working on it, but it is a big problem at the moment.

---

### Post by typhoon_tip on 2011-11-30
Try the usual stuff related to compiz and vsync:
[http://askubuntu.com/questions/38028/performance-being-really-choppy-with-ati-drivers](http://askubuntu.com/questions/38028/performance-being-really-choppy-with-ati-drivers)

I add one more note, after disabling detect refresh rate, set the rate to double your video frequency (e.g. I got 60 Hz, I set it to 120 fps). It will be then as smooth as silk.

---

