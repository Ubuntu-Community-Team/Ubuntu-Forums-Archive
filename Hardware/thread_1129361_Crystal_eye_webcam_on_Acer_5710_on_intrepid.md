---
title: "Crystal eye webcam on Acer 5710 on intrepid"
date: 2009-04-18
forum: Hardware
---

### Post by numanx86 on 2009-04-18
Hi all, this is my first post on forum, I'm italian (sorry for my english).
Well,
I've got an Acer 5710 with crystal eye webcam, to getting it works I did a lot of things:
1) I download and make the newest uvc-video driver [http://linuxtv.org/hg/](http://linuxtv.org/hg/), after this the webcam light turns on but skype or cheese doesn't works.
2) On the net I found several how-to that says to mount uvcvideo or usbvision kernel module after the installation of uvc-video driver... in my system (kernel 2.6.27-14) those modules are already present.

Two questions:
1- Is there a reliable howto to solve this problem?
2- After launching ```
modprobe -l
``` I see a lot of modules that seems to control webcam: usbvideo, usbvision, uvcvideo etc... is it possible that its causes conflicts each other?

---

