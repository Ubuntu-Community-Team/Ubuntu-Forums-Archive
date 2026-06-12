---
title: "my laptop wont stay powered on"
date: 2011-11-01
forum: Hardware
---

### Post by kooley on 2011-11-01
hello, im having a bit of a problem with my laptop, its is an MGD Aptonbook and a little while ago it started just shutting itself off at first i thought it was the battery just died faster than the indicator specified so i just kept it plugged in all the time but that didn't help at all, so i got a new power cord for it and that still didn't help. it powers on no problem then it runs for a couple of mins then all the lights start flashing and it shuts off. does anyone know what is causing this problem, and how to solve it?

thanks

---

### Post by tartalo on 2011-11-01
Overheating maybe?

[http://www.n00bsonubuntu.net/content/monitor-your-cpu-temperatures-with-lm-sensors-and-sensors-applet/](http://www.n00bsonubuntu.net/content/monitor-your-cpu-temperatures-with-lm-sensors-and-sensors-applet/)
EDIT: these instructions are old. Looking for something current.

EDIT2: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by kooley on 2011-11-01
it doesn't stay on long enough to load the OS some of the time other times it loads up but not for long enough to do anything

---

### Post by dFlyer on 2011-11-01
My best guess is overheating, what does the following command return.

sensors -f

---

### Post by kooley on 2011-11-01
its not staying powered on long enough to load properly anymore it gets about to the splash then shuts off rarely it will make it into the desktop then it only last about 30 sec then shuts off

---

### Post by |{urse on 2011-11-01
It surely does sound like overheating. +1

could also be...

If you have 2 SODIMM's try removing one and see if it improves, if not swap them and try booting again. If it works then you might have some bad ram. The other thing you might try is removing the hard drive entirely and boot to livecd, if it makes it past where it shuts down on your system then power off and replace the hard drive, reboot to livecd again open a terminal and run 

sudo e2fsck -c /dev/sda    

Replace sda with your device alias.

If that doesnt help then you may have a bad hard drive on your hands, definitely try a reinstall before chucking it though.

---

### Post by kooley on 2011-11-01
thanks for the feedback i will try these out and post back my findings

---

### Post by kooley on 2011-11-05
well i managed to get it fixed thank you for all your feedback, to solve this problem i had to remove the battery and run it without a battery, i guess the bater was sucking power and not charging or something, and i also had to replace the hard drive because when i got the computer to stay powered on i discovered the hard drive had died :/

---

### Post by costre on 2011-11-08
Thanks for the tip. My laptop is shutting down rabdomly, and ubuntu is showing the battery to be broken. I will try to run it without the battery for a while.

---

### Post by |{urse on 2011-11-09
Glad you got it sorted, I was thinking either overheating or bad hard disk. But yeah, from now on if you ever need to diagnose a hardware problem on a laptop just repeat those steps, if none of that helps then it could be other things but I find 90% of the time its either ram, hard drive, power jack, screen, or display power inverter.
The other 10% of the time its a total motherboard replacement that rivals the cost of an entire new laptop. You got off cheap with it just being a hard drive! :P

---

