---
title: "ekiga works, but vgrabbg gets green picture, on logitech orbit af sphere webcam"
date: 2008-10-29
forum: Hardware
---

### Post by xnoobyxnooby on 2008-10-29
Hello,

I have a Logitech Orbit AF Sphere webcam, and am trying to access it
using the "stopmotion" app. Apparently the stopmotion program calls
vgrabbj to grab an image from the webcam. I am running Ubuntu Desktop
i386 8.10-RC1.

When I run Ekiga, it is able to grab video from the Quickcam perfectly.

When I run the "stopmotion" program, it only imports a green screen.

When I vgrabbg manually, I get a single green picture.

I've read a lot of messages in various forums, but nobody seemed to
have the green picture problem. Since it works in Ekiga, I assume it
should be able to work with stopmotion/vgrabbj.

Any suggestions?

-----

h@hone:~$ lsusb
Bus 008 Device 002: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF

-----

h@hone:~$ vgrabbj -s /dev/video0
vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (UVC Camera (046d:0994))
Capabilities
Type     : 1    Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 960
MaxHeight: 720
MinWidth : 48
MinHeigth: 32

Current Settings:
Brightness: 32896
Hue       : 0
Color     : 8224
Contrast  : 8224
Whiteness : 0
Depth     : 16
Palette   : YUYV (8)
Width     : 800
Height    : 600
Chromakey : 0
h@hone:~$

-----

h@hone:~$ vgrabbj -f test.jpg -d /dev/video0 -i svga  && eog test.jpg
Reading image from /dev/video0
There was no map allocated to be freed...
h@hone:~$
(results in green image)

---

### Post by xnoobyxnooby on 2008-11-01
Bump. Still no luck. Any suggestions?

> **xnoobyxnooby said:**
> Hello,

I have a Logitech Orbit AF Sphere webcam, and am trying to access it
using the "stopmotion" app. Apparently the stopmotion program calls
vgrabbj to grab an image from the webcam. I am running Ubuntu Desktop
i386 8.10-RC1.

When I run Ekiga, it is able to grab video from the Quickcam perfectly.

When I run the "stopmotion" program, it only imports a green screen.

When I vgrabbg manually, I get a single green picture.

I've read a lot of messages in various forums, but nobody seemed to
have the green picture problem. Since it works in Ekiga, I assume it
should be able to work with stopmotion/vgrabbj.

Any suggestions?

-----

h@hone:~$ lsusb
Bus 008 Device 002: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF

-----

h@hone:~$ vgrabbj -s /dev/video0
vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (UVC Camera (046d:0994))
Capabilities
Type     : 1    Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 960
MaxHeight: 720
MinWidth : 48
MinHeigth: 32

Current Settings:
Brightness: 32896
Hue       : 0
Color     : 8224
Contrast  : 8224
Whiteness : 0
Depth     : 16
Palette   : YUYV (8)
Width     : 800
Height    : 600
Chromakey : 0
h@hone:~$

-----

h@hone:~$ vgrabbj -f test.jpg -d /dev/video0 -i svga  && eog test.jpg
Reading image from /dev/video0
There was no map allocated to be freed...
h@hone:~$
(results in green image)

---

### Post by wkimberly on 2009-07-30
Have you tried:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vgrabbj -f test.jpg -d /dev/video0 -i svga
```

Got the recommendation from:
[https://bugs.launchpad.net/ubuntu/+source/vgrabbj/+bug/364744](https://bugs.launchpad.net/ubuntu/+source/vgrabbj/+bug/364744)
[http://n2.nabble.com/Opencv-Samples-in-Linux-environment-td2302179.html](http://n2.nabble.com/Opencv-Samples-in-Linux-environment-td2302179.html)

---

### Post by eswing on 2009-11-08
I am have this same problem with a Logitech C500.  Cheese works find, but stopmotion does not.  I would like to try the workaround, but not sure where this LD_PRELOAD command goes.  Can anyone tell how to do this or if this workaround works?

---

