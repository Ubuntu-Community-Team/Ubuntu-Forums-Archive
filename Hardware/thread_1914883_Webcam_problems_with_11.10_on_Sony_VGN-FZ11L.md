---
title: "Webcam problems with 11.10 on Sony VGN-FZ11L"
date: 2012-01-25
forum: Hardware
---

### Post by Chris1492 on 2012-01-25
Most of Ubuntu 11.10 is working on this laptop, but not the webcam.

lsusb shows:

   Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

I've installed the r5u87x package, which reports that it has loaded the firmware successfully.

Cheese works, but only if I change the resolution to 320x240 (from 640x480).  And then the image is upside down (a known feature of these laptops).  I can't find a way to flip the image.

Skype doesn't show video at all -- I've tried setting the resolution manually in the config.xml file, but that didn't help.

I tried 

```
echo 1 >/sys/class/video4linux/video0/vflip
```but that file doesn't exist.

I've installed libv4l from [https://launchpad.net/~libv4l/+archive/ppa]("https://launchpad.net/%7Elibv4l/+archive/ppa") and tried

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so cheese (or skype)
```and that didn't work either.  With skype, I got this message:

```
libv4l2: error dequeuing buf: Device or resource busy
```And now I can't find any other potential fixes to try.

Does anyone have any suggestions, before I give up and reinstall Vista (eek!)

cheers

Chris

---

