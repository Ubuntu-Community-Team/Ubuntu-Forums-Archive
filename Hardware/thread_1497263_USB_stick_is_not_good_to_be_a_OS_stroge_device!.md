---
title: "USB stick is not good to be a OS stroge device!?"
date: 2010-05-30
forum: Hardware
---

### Post by ckkk on 2010-05-30
:confused:one of my "friend"... 
[COLOR=red]He explained, it is not an uncommon thing where the USB root hub will drop connections to a device in a Linux operating system.  The issue is the Linux drivers (for example the touch screen and the TV Tuner) often do not work well together and compete for reources on the USB hub.  So one device or a combination of devices will periodically take 95% of the USB resources and starve all the other devices which will then drop.  Or multiple devices, which drivers do not work well with one another will both absorb all the resources and crash the hub (this is what we see).   This is a function of many of the USB device drivers not working well with one another or not being up to standard.   In other motherboards the hub system will be four 2-port hubs so if USB device crashes a hub it will only take down the one other device on the hub not the entire USB system.  However, in the 945GC chipset,  all of the USB devices are off of one 8 port root hub so if one device crashed the hub it takes down all devices on the hub.  the single 8 port hub can be noted the the technical specs for the board. So the crashes of the root hubs system will continue to take down all the devices... which would include the OS on the thumb drive which would crash the entire system.  We are seeing the crashes regularity now and they will only increase with another USB device on the hub.[/COLOR]
[COLOR=red]So that is the detailed reason, provided by Intel who designed the board and the root hub system, why we can not run the OS on any device connected via USB.[/COLOR] 
 
is it true???:confused:

---

### Post by efflandt on 2010-05-30
I have run Ubuntu 9.10 and 10.04 from USB sticks, USB card readers (SD and even microSD), and USB hard drives, and have not seen the issues that you speak of.

I have one computer that cannot seem to boot from a 500 GB USB hard drive, but it boots fine from a 160 GB USB hd, so that must be some issue with its BIOS.  The same 500 GB USB drive boots fine on 2 newer computers.

I could see where you might have some speed bog trying to run multiple USB devices that use a lot of bandwidth.  But I have never seen a USB hub crash.

---

### Post by sgosnell on 2010-05-30
+1

I regularly run Ubuntu off a USB drive, and I've never had a problem with it.

---

### Post by slooksterpsv on 2010-05-30
I've run Mac OS X off of an external drive with multiple other USB Peripherals connected. I've run Ubuntu off of USB for long periods of time. Maybe on Intel USB items it crashes or drops or that, but I've never had any trouble. Also, ReadyBoost in Vista and 7 wouldn't be possible if that happened. So your friend told you wrong.

---

### Post by ckkk on 2010-06-02
thanks a lot~bro~:P

---

