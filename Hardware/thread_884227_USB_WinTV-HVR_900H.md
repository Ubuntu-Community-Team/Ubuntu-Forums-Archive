---
title: "USB WinTV-HVR 900H"
date: 2008-08-08
forum: Hardware
---

### Post by keiffee30 on 2008-08-08
I have had a look and found that on the USA site that the Hauppauge WINTV-HVR 900H will work on linux. 

So i popped out and grabbed myself one. I have installed some apps, but nothing looks like it working. 

Im not sure how to look at the usb to see if the laptop can see it. There is no lights on the usb drive. 

What can one do ????

---

### Post by phidia on 2008-08-08
To "see" your usb open a terminal and enter > lsusb that should show the bus and what's connected. You can also enter > dmesg into a terminal after you plug a device in. I'm not sure exactly what the "Hauppauge WINTV-HVR 900H " is beyond being a TV/video device but there are guides for capture cards and other devices at the [ubuntu video wiki]("https://help.ubuntu.com/community/Video").

---

### Post by kosmo90 on 2009-08-14
Sorry mate, i'm in the same boat as you.
If you look here [http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html) it says  "          Work is under way for the WinTV-HVR-900H."

Not exactly sure when that was posted but i"ve been checking for 2-3 months and theres been no change.
Linux tv lists our device [http://www.linuxtv.org/wiki/index.php/Trident_TM6000#TM6000_based_Devices](http://www.linuxtv.org/wiki/index.php/Trident_TM6000#TM6000_based_Devices) (down the bottom of the page) but nothing yet.

Just keep checking back periodically and i'm sure it will be supported soon.

---

### Post by d0b33 on 2009-11-26
Same here I'd like to get this working with mythtv.

The HD model seems to only have windows support.

---

### Post by oscar.st on 2010-01-26
I've been waiting for the driver for over a year, and the messages of Hauppauge and TV Linux Wiki are there for centuries. I hope one day the driver is available.

:-(

---

### Post by blueturtl on 2010-03-30
I am currently testing this device on the Lucid Lynx beta and it seems possible to have it working *if* the appropriate measures are taken.

It is operated by the em28xx driver which had an experimental branch (em28xx-new). With the em28xx-new driver this card worked, but it had to be manually installed on Ubuntu 8.10. This involved compiling the kernel module.

em28xx-new has been discontinued, but the main branch em28xx seems to be almost ready. It is not working yet, but I found [a reference]("http://forums.gentoo.org/viewtopic-t-815022-start-0.html") on Gentoo forums that suggests this could indeed be working on kernel 2.6.33. See the second post.

We all know Lucid will ship with 2.6.32, but backporting that patch seems feasible at this point and I have offered to help testing should the devs go for it.

Check out my [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318448") on Launchpad if you have this device and want to help test it for Lucid Lynx.

---

### Post by blueturtl on 2010-03-31
Sorry if I got anyone's hope up.

I discovered there are three models of the device in question:

HVR-900
HVR-900 (R2) <-- I have this one
and HVR-900H

---

