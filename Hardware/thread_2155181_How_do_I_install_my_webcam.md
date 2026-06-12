---
title: "How do I install my webcam?"
date: 2013-06-17
forum: Hardware
---

### Post by iscariotes on 2013-06-17
Hi, I'm using an up-to-date Ubuntu 14.04 and I have a M-Tek webcam. I think the model is Mtek SC301K, here are some technical information about it:

(from dmesg)
```
[ 4058.641654] usb 1-2: >New USB device strings: Mfr=16, Product=96, SerialNumber=0
[ 4058.641660] usb 1-2: >Product: SC301 UPcam
[ 4058.641664] usb 1-2: >Manufacturer: PixArt Imaging Inc.
[ 4058.648347] uvcvideo: Found UVC 1.00 device SC301 UPcam (093a:2700)
[ 4058.656590] input: SC301 UPcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8

```

(from lsusb)
```
Bus 001 Device 004: ID 093a:2700 Pixart Imaging, Inc.
```

When I try to open cheese, it fails with the following error:

```
$ cheese
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.

(cheese:3643): Clutter-CRITICAL **: Unable to initialize Clutter: Unable to find suitable fbconfig for the GLX context: Failed to find any compatible fbconfigs

```

Could somebody help me, please? Is there a missing kernel module or something?

---

### Post by coldraven on 2013-06-17
Try installing "guvcview" from the Software Centre or
```
sudo apt-get install guvcview
```
and see if that helps.
Edit: I mean run guvcview and see if it works.

---

