---
title: "Accelerometer HP Drive Guard support in 9.10?"
date: 2009-10-12
forum: Hardware
---

### Post by mikerbot on 2009-10-12
I have a HP mini 5101 running the beta of 9.10. This machine has a few accelerometers in it to turn off the hard drive and retract the heads in the event of sudden movement. I know nothing about them, and I was wondering if they're doing their job in Karmic. And can I use the output of them to do something interesting, like Smackbook for macs?

---

### Post by ninja togo on 2009-11-09
I know it was technically possible in 9.04 out of the box, as you could play tux racer with it as a joystick:D but it is used for safety in 9.10.:mad:

---

### Post by laser_b on 2009-11-27
Well I have a HP 8510p Notebook. I can use the accelerometer as a joystick out of box with 9.10. But the calibration is terrible. I tried it first with Neverball, because you see very quickly if it works, even if it's only very less. To calibrate and test the joystick I used  [jstest-gtk]("http://www.getdeb.net/updates/jstest-gtk") from getdeb. Just change min and max to a lower number i.e. -500 and 500 and it works fine for me :D. So now I'm playing with my 3kg notebook some hours a day and I will no longer need any additional strength training :D.

---

### Post by faskunji on 2010-01-04
Sorry for asking this here but I have strange problem:
I have HP ProBook 4510s which came with Suse Linux. I removed it and installed XP and Ubuntu 9.10
XP works fine. Ubuntu sometimes loads normally but about 70% of boots ends with blank text mode screen with cursor blinking on top-left corner. If I load with recovery mode it shows some device init logs and stops at different lines each time.
Sometimes it loads and works fine.

I know that this model also has accelerometers, one of the papers that came with notebook says:
> HP 3D DriveGuard is a feature on this computer and is only compatible with Microsoft Windows operating systems. 3D DriveGuard protects the hard drive by parking the drive and halting I/O requests when you either drop the computer, or move the computer withe the display closed while computer is running on battery power.
My question is if buggy or incompatible driver for the sensor can be reason of such stops at boot time?
Maybe it's value ranges do not much and sensor looks too noisy for driver? 
I am thinking about such strange reason cos it stops randomly at boot time.

---

### Post by mikerbot on 2010-02-23
Maybe it'll be quick and dirty to poke around the bios and see if you can turn off the drive guard? @Laser_b Thanks for the heads jstest, I'll see if I can do something interesting!

---

### Post by mikerbot on 2010-02-23
jstest doesn't see it. xinput doesn't see it either. This is the driver that (i think) is in the 2.6.3X kernel: [http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d](http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d) 

interesting convo here: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-10/msg10705.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-10/msg10705.html)

I looked in /sys/devices/platform/lis3lv02d but didn't find anything useful, I shook my laptop around and then checked the user and system logs, still nothing. BIOS has no settings. Any suggestions?

---

