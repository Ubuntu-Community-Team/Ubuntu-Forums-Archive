---
title: "EM2860 video capture device"
date: 2015-09-11
forum: Hardware
---

### Post by patrick-duim on 2015-09-11
Some years ago i bought a usb 2.0 video capture device.
I plugged it into my computer running ubuntu 14.04 and strarted up VLC player.
It recognised the device as EM2860/TVP 5150 reference design.
But when i started my attached VCR it didn't show any video on my screen.
There was a website [http://www.linuxtv.org/wiki/index.php/SilverCrest_USB_2.0_Video_Grabber_VG_2000](http://www.linuxtv.org/wiki/index.php/SilverCrest_USB_2.0_Video_Grabber_VG_2000) 
where i read that this device would be working on linux.

There is a driver loaded:

```
11.197979] em2860 #0: v4l2 driver version 0.2.0
[   13.122953] em2860 #0: V4L2 video device registered as video0
[   13.122958] em2860 #0: V4L2 VBI device registered as vbi0
[   13.122962] em2860 #0: analog set to isoc mode.
[   13.123010] usbcore: registered new interface driver em28xx
[   13.129561] em28xx-audio.c: probing for em28xx Audio Vendor Class
[   13.129563] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   13.129564] em28xx-audio.c: Copyright (C) 2007-2011 Mauro Carvalho Chehab
[   13.129787] Em28xx: Initialized (Em28xx Audio Extension) extension
```

But the device cannot be opened:

```
patrick@patrick-MS-7616:~$ lsusb -v  -d eb1a:2863

Bus 001 Device 003: ID eb1a:2863 eMPIA Technology, Inc. Video Grabber
Couldn't open device, some information will be missing
```

Does anyone have more experience with this?
I am not certain what steps to make next.

Regards: Patrick

---

