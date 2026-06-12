---
title: "Webcam not detected on Elitebook"
date: 2018-04-29
forum: Hardware
---

### Post by stef-baly on 2018-04-29
I have an HP EliteBook 840 G5 with a fresh 18.04 install. The laptop is new and has never been tested under 16.04. Beside other peripherals the integrated webcam  is missing. Cheese complains the device is missing.
Any ideas how to solve this trouble ?
Thanks,

Stephane

@LY0269:~$ lsmod
Module                  Size  Used by
uvcvideo               86016  0


@LY0269:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 05c8:0808 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 138a:00ab Validity Sensors, Inc. 
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


@LY0269:~$ lsmod | grep uvcvideo
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev

---

### Post by sboulkour on 2018-05-28
Heya !

Any news about your issue with the webcam ?
I'll get the same machine by the end of june and am interested in using it with Ubuntu only.

Despite the webcam issue, did you have to tweak some things or everything works out of the box ?

---

### Post by planet-axis on 2018-06-04
Exactly the same issue here.

HP Elitebook 840 G5 - the webcam is listed in `lsusb`:

```
Bus 001 Device 005: ID 05c8:0808 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
```

But none of video apps can see/use it.

---

### Post by planet-axis on 2018-06-04
For the sake of sharing. I've found this mailing thread on linux uvc development: [https://sourceforge.net/p/linux-uvc/mailman/message/36330850/](https://sourceforge.net/p/linux-uvc/mailman/message/36330850/)

It seems the hardware support is not yet implemented.

---

