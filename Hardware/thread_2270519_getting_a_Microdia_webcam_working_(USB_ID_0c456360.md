---
title: "getting a Microdia webcam working (USB ID 0c45:6360)"
date: 2015-03-23
forum: Hardware
---

### Post by akos.maroy on 2015-03-23
Hi,

I'm trying to get a microdia webcam working on my ubuntu 14.10, with kernel 3.16.0-31-generic

if I just plugin in the webcam, I get the following in dmesg:

```
[13530.217554] usb 1-2.3.1: new high-speed USB device number 21 using ehci-pci
[13530.357191] usb 1-2.3.1: New USB device found, idVendor=0c45, idProduct=6360
[13530.357194] usb 1-2.3.1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[13530.357196] usb 1-2.3.1: Product: USB 2.0 Camera
[13530.357198] usb 1-2.3.1: Manufacturer: Sonix Technology Co., Ltd.
[13530.378055] usb 1-2.3.1: 4:1: cannot get freq at ep 0x84
[13530.478100] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6360)
[13530.500193] uvcvideo: No streaming interface found for terminal 6.
[13530.500272] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3.1/1-2.3.1:1.0/input/input25
[13530.500401] usbcore: registered new interface driver uvcvideo
[13530.500403] USB Video Class driver (1.1.1)
[13530.522573] usb 1-2.3.1: 4:1: cannot get freq at ep 0x84
[13530.821198] uvcvideo: Failed to query (GET_MAX) UVC control 2 on unit 2: -110 (exp. 2).
[13531.120900] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[13531.420662] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[13531.720558] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).

```

and no /dev/videoX device

if I try to compile a driver manually as described here: [http://wiki.ubuntu-it.org/Hardware/Webcam/Microdia](http://wiki.ubuntu-it.org/Hardware/Webcam/Microdia) , I get the following compilation error:

```
$ make
make -C /lib/modules/3.16.0-31-generic/build SUBDIRS=/home/akos/src/aviation/glass.aero/src/microdia modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.o
/home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.c: In function ‘v4l_sn9c20x_register_video_device’:
/home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.c:1463:11: error: ‘struct video_device’ has no member named ‘parent’
  dev->vdev->parent = &dev->interface->dev;
           ^
/home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.c:1465:11: error: ‘struct video_device’ has no member named ‘current_norm’
  dev->vdev->current_norm = 0;
           ^
scripts/Makefile.build:257: recipe for target '/home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.o' failed
make[2]: *** [/home/akos/src/aviation/glass.aero/src/microdia/sn9c20x-v4l2.o] Error 1
Makefile:1345: recipe for target '_module_/home/akos/src/aviation/glass.aero/src/microdia' failed
make[1]: *** [_module_/home/akos/src/aviation/glass.aero/src/microdia] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-31-generic'
Makefile:33: recipe for target 'driver' failed
make: *** [driver] Error 2

```

the webcam works fine on other systems, e.g. on Windows, and on Android phones with a USB OTG cable

I wonder how I can make it work on my Linux box as well...

---

### Post by tgalati4 on 2015-03-23
I had a similar Microdia camera and had to manually compile the module for it to get it to work with Skype, but that was a long time ago, perhaps 8.04.   So, if you have the time, you might consider setting up a vm or another machine with 14.04 and try to compile and see if you get the same errors.  It looks like a V4L2 framework error, perhaps a reshuffling of what cameras are supported and what modules to load.

It's also possible that it is supported under the universal video camera module (uvcvideo), but requires a few switches to be turned on.

> tgalati4@Mint17 ~/Desktop $ modinfo uvcvideo | grep quirks
parm:           quirks:Forced device quirks (uint)


You just need to find the magic quirk number.

---

### Post by akos.maroy on 2015-03-23
> **tgalati4 said:**
> I had a similar Microdia camera and had to manually compile the module for it to get it to work with Skype, but that was a long time ago, perhaps 8.04.   So, if you have the time, you might consider setting up a vm or another machine with 14.04 and try to compile and see if you get the same errors.  It looks like a V4L2 framework error, perhaps a reshuffling of what cameras are supported and what modules to load.

It's also possible that it is supported under the universal video camera module (uvcvideo), but requires a few switches to be turned on.



You just need to find the magic quirk number.

thanks for the tip. I tried all the quirks listed here: [http://www.ideasonboard.org/uvc/faq/#faq6](http://www.ideasonboard.org/uvc/faq/#faq6)  - but none of them helped :(

---

### Post by tgalati4 on 2015-03-24
I'm busy this week, but I will dig out that camera and see if I can get it to work under 14.04:

> tgalati4@Mint17 ~/Desktop $ uname -a
Linux Mint17 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by akos.maroy on 2015-03-24
> **tgalati4 said:**
> I'm busy this week, but I will dig out that camera and see if I can get it to work under 14.04:

thanks. I'm running the following:

```
$ uname -a
Linux rakku 3.16.0-31-generic #43-Ubuntu SMP Tue Mar 10 17:37:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

