---
title: "fglrx and nforce2 problems"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by fish78 on 2005-04-17
My system:

cpu: XP2000+
board: ASUS A7N8X-E Deluxe (NForce2)
video card: ATI Radeon 9700
os: hoary 5.04

I tried to get the 3D acceleration to work. I decided to follow the [ubuntu wikipage describtion](http://ubuntulinux.org/wiki/BinaryDriverHowto) .

If I use fglrxinfo, I get following information:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

But when I try to get any OpenGL screensaver running there's only a black screen. When I try to get more information about OpenGL and open the KInfoCenter, click on OpenGL, KInfoCenter crashes. Even no other OpenGL programs like Tuxracer work.
Can anyone help me?

---

### Post by fish78 on 2005-04-17
Ok, some more information:

if I type: lsmod |grep nvidia I get:
nvidia_agp              7708  1
agpgart                33704  2 nvidia_agp

I guess here is the problem. I have already set the option UseInternalAGPGART" "no" in the xorg.conf file.

---

### Post by fish78 on 2005-04-17
some steps further ;)

Really strange, tuxracer and tuxkart works great, opengl sreensaver and tvtime don't work.


UPDATE:

It works. Just always thought the opengl screensavers should work. Games and tvtime works.

---

