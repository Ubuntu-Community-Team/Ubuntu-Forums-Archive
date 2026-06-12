---
title: "Strange old webcam."
date: 2009-03-14
forum: Hardware
---

### Post by ykcirt on 2009-03-14
I'm trying to get an old 3Com webcam to work on my Ubuntu rig. A big problem is determining what it is, as there are almost no signs of model numbers. There is a very tiny sticker on the back, almost unreadable and all I can make out from it is that the serial number might be 0776. It could also be 8776. That's not much to work with. I've also lost the old installation cd-rom over the years. On the top of the webcam is a big, red warning sticker: 

*"WAIT! Do not install this camera until after you run the Video Connections(tm) Installation CD-ROM. Trust us, we know what we are doing."*

So.. that might be a bit detrimental, if for Windows. :popcorn:

Below the sticker it reads "3Com HomeConnect" but some searches revealed nothing there.

I plugged that sucker in, but nothing happened. Any clues on how to proceed?

The only other device that I plug in sometimes is an MP3 player, although it basically functions in Ubuntu as an external harddrive rather than a piece of hardware that might require a very specific driver. That MP3 player is working, so I'm guessing something is working right.

---

### Post by cariboo on 2009-03-14
If your webcam is connected via usb, open a terminal and type:

```
lsusb
```

You should see something similar to this:

```
lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 003: ID 0665:5161  
Bus 001 Device 002: ID 045e:074f Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Note above that my Logitech QuickCam is detected.

Jim

---

### Post by ykcirt on 2009-03-14
```
Bus 002 Device 004: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]
Bus 002 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 002 Device 002: ID 05d5:6782 Super Gate Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0582:0099 Roland Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So at least it's being recognized.

---

### Post by ykcirt on 2009-03-18
How do I go from here?

---

