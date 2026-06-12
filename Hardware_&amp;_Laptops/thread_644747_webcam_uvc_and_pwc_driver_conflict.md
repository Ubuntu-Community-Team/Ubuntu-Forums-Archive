---
title: "webcam: uvc and pwc driver conflict"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by willie_wang on 2007-12-19
i wonder if you guys can help. i may be going about this in the totally wrong way, but please correct me if i'm making a rookie error.

i have a logitech quickcam for notebooks pro - i've done some research and it seems that other linux users have had some success by using the phillips pwc driver instead of the bundled uvc driver. so i downloaded the pwc-source from synaptic and then compiled and installed it.

now. i modprobed the pwc driver, plugged in my webcam, but it seems that my webcam is still trying to run off the uvc driver. caminfo splurge:

```
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:08c3)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 0x0
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

```

i know that some cameras are supported both by pwc and uvc, but is there a way to override the uvc settings so it runs under pwc instead? any help would be much appreciated!

cheers!

Wil

---

