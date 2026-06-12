---
title: "Sony Eyetoy."
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by Rackerz on 2006-07-30
[http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page](http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page)

I need to install this driver to get it working, but I don't know how. I'm new to Linux and I don't understand those instructions. Could someone help out?

---

### Post by J0s3ph on 2006-08-23
[http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html](http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html)

With all due respect I found this link after five seconds of visiting the link you gave.

---

### Post by TMR on 2006-08-27
I think I've installed the ov519 drivers for the Sony Eyetoy.  But I'm getting the following

```
root@SandyCheeks:/etc/modprobe.d# [COLOR="Blue"]lsmod | grep ov[/COLOR]
root@SandyCheeks:/etc/modprobe.d# [COLOR="Blue"]modprobe ov51x[/COLOR]
root@SandyCheeks:/etc/modprobe.d# [COLOR="Blue"]lsmod | grep ov[/COLOR]
ov51x                  99264  0
videodev                9856  1 ov51x
usbcore               129668  7 ov51x,snd_usb_audio,snd_usb_lib,usb_storage,ehci_hcd,uhci_hcd
root@SandyCheeks:/etc/modprobe.d# [COLOR="Blue"]dmesg | tail[/COLOR]
[...]
[4376369.473000] /tmp/ov51x-jpeg-0.5.3/ov51x.c: USB OV519 video device found
[4376369.475000] /tmp/ov51x-jpeg-0.5.3/ov51x.c: reg write: error -71: Bit-stuff error (bad cable?)
[4376369.475000] /tmp/ov51x-jpeg-0.5.3/ov51x.c: OV519 Config failed
[4376369.476000] /tmp/ov51x-jpeg-0.5.3/ov51x.c: Camera initialization failed
[4376369.476000] ov51x: probe of 2-1:1.0 failed with error -5
[4376369.476000] usbcore: registered new driver ov51x
[4376369.477000] /tmp/ov51x-jpeg-0.5.3/ov51x.c: v1.65-1.11-mark : ov51x USB Camera Driver
```

The camera (an ov519 chipset Sony Eyetoy) works under Win XP, and I'm trying to make it work with aMSN under Ubuntu 6.0.6 Dapper Drake.  It's probably the last thing I need to get working before I delete my XP partition. Any help will be much appreciated.

TMR

---

