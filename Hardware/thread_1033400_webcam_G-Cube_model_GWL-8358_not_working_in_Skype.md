---
title: "webcam G-Cube model GWL-8358 not working in Skype"
date: 2009-01-07
forum: Hardware
---

### Post by Berduchwal on 2009-01-07
Hi
After fresh installation of 8.10 I can not use my web cam in Skype.
It is called G-Cube model GWL-835B.

dmesg

```

[24255.500046] usb 4-1: new full speed USB device using uhci_hcd and address 2
[24255.760426] usb 4-1: configuration #1 chosen from 1 choice
[24255.889438] Linux video capture interface: v2.00
[24255.897598] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
[24255.898816] usb 4-1: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x303B)
[24255.975104] usb 4-1: No supported image sensor detected
[24255.975951] usbcore: registered new interface driver zc0301

```

so it appears to be registered correctly but skype does not show it at all.

lsusb
```

Bus 004 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

```

I have libv4l-0 and:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
does not help.

It was working fine under 8.04.

Can you please suggest other diagnostics I can run to discover why?

---

### Post by Berduchwal on 2009-01-14
Some additional information about the topic:
[http://www.kubuntuforums.net/forums/index.php?topic=3094576]("http://www.kubuntuforums.net/forums/index.php?topic=3094576")

This might be related:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/144745]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/144745")

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/292086/comments/16]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/292086/comments/16")

It appears that it is related to usage of the zc0301 driver as per last line of the dmesg.

---

### Post by reyfer on 2009-02-06
The line you use, where did you find it? > LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skypeI use this
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
and skype works perfectly

---

### Post by Berduchwal on 2009-02-06
If you are 8.04 users as your profile suggests then you will not have this problem.

This only occurs in 8.10 as described in the bug description under lunchpad.

I have tried you version of the command and it changes nothing webcam is still not showing under skype.

---

### Post by reyfer on 2009-02-25
> **Berduchwal said:**
> If you are 8.04 users as your profile suggests then you will not have this problem.

This only occurs in 8.10 as described in the bug description under lunchpad.

I have tried you version of the command and it changes nothing webcam is still not showing under skype.

Sorry, when I posted I still had not changed my profile, I was using 8.10 and still am, and that line works for me

---

### Post by Berduchwal on 2009-02-25
Ok, that is great news!

It would be great if you could mention your answer in the lunchpad so developers can ask you question about other staff and get to the bottom of the issue.



For this and other webcams see:
[http://moinejf.free.fr/webcam.html]("http://moinejf.free.fr/webcam.html")

Camera above is on the list there and package can be downloaded from:
[http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/~jfrancois/gspca/")

---

