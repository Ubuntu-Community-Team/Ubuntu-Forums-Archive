---
title: "GPSD working but apps not finding GPS information"
date: 2010-07-10
forum: Hardware
---

### Post by Thystra on 2010-07-10
I recently got a BU-353 GPS Puck.  I spent some time playing around with it and searching, and I came across a couple older posts and webpages about how to get it working.  I'm on 64 bit 10.04 Lucid.  I finally did manage to get xgps to work and pick up satellites.

I can't get Tango GPS or GPS Drive to seem to work.  Tango GPS shows "no GPS..No GPSD" and GPSdrive doesn't seem to pick it up (the window goes off the bottom of the laptop screen and it won't allow itself to be shrunk.  

Any suggestions on how to get the mapping programs to see the GPS info would be much appreciated.

[IMG]http://www.blackrosesyndicate.com/post/xgpsworking.png[/IMG]

---

### Post by tgalati4 on 2010-07-10
Sometimes you need to change the USB device in preferences.  What is the output of:

ls -la /dev/ttyU*

and 

ls -la /dev/U*

I have the same puck.  It has a SiRFstar III chipset and it works pretty well.

---

### Post by Thystra on 2010-07-11
Here's the outputs.  Glad to know it can work!

alan@gryffon:~$ ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2010-07-11 11:06 /dev/ttyUSB0

alan@gryffon:~$ ls -la /dev/U*
ls: cannot access /dev/U*: No such file or directory

alan@gryffon:~$ /dev/
block/      char/       .initramfs/ net/        serial/     .udev/
bsg/        disk/       input/      pktcdvd/    shm/        usb/
bus/        fd/         mapper/     pts/        snd/        v4l/

---

### Post by Thystra on 2010-07-11
Well, for whatever reason it seems to be working now!

---

### Post by tgalati4 on 2010-07-11
Well, good.  /dev/ttyUSB0 is the typical device that most programs use, but sometimes the device is not set properly in preferences.  I my experience, many programs can share the USB gps puck simultaneously.  That is why gpsd is a server daemon, it serves up gps data to whatever program uses it.  Try google earth and see if it picks it up.

---

