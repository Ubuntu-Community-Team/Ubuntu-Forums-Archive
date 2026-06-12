---
title: "Dell Latitude E6400 high cpu usage when using webcam"
date: 2010-04-11
forum: Hardware
---

### Post by meonkeys on 2010-04-11
I love Ubuntu 9.10 on the Dell Latitude E6400! Everything works well out of the box. Wifi, compiz, webcam/mic/speakers, multimedia buttons, sleep/hibernate/resume, wow!

The only thing I'm running into lately is that the CPU usage seems higher than it should be whenever I use the webcam. I suppose I have no idea what the CPU usage *should* be, but 50% seems high.

```
$ lsusb | grep Microdia
Bus 001 Device 004: ID 0c45:63f1 Microdia
$ dmesg | grep uvc
[   12.610840] uvcvideo: Found UVC 1.00 device Integrated_Webcam_2M (0c45:63f1)
[   12.620725] usbcore: registered new interface driver uvcvideo
```

Anyone got any ideas?

Hrmm, it might actually be video *playback* that's causing the problem... watching a video also bumps up the CPU usage.

---

