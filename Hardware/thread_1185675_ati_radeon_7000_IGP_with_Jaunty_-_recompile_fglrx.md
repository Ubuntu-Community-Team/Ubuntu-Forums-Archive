---
title: "ati radeon 7000 IGP with Jaunty - recompile fglrx?"
date: 2009-06-12
forum: Hardware
---

### Post by barna on 2009-06-12
Hi,
I have recently upgraded to jaunty, and have problems with my video output. My notebook has a ATI Mobility Radeon 7000 IGP video card, and as I have learned from the forums and google, 
1) the proprietary driver fglrx from ati does not support this card anymore, only 9500 and above
2) Ubuntu uses the open-source xserver-xorg-driver-radeon for the ati cards.

This works more or less for me, but GoogleEarth has an empty display, and a CAD application (VariCAD) has absolutely screwed up display in 2D (3D works, surprisingly).
So I concluded that xserver-xorg-driver-radeon is good though, but not perfect - far not perfect. However, I can not use the fglrx (my notebook freezes, if I install this driver and try to start X)

Since I had a perfectly working video (3D/2D) with Gutsy, 7.10, I am wondering if the video driver source code from that distro (I guess it was then fglrx as well, but I will check) could be recompiled on 9.04, and be used. Anybody has an idea?
Could somebody give me a few-lines example, how to do this? 

Thanks

---

