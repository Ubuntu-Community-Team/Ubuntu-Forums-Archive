---
title: "Graphics or video problems"
date: 2009-11-03
forum: Hardware
---

### Post by pokepasa on 2009-11-03
Hi all.

I have and old laptop, Compaq Evo N1020v, with 256 RAM, 40 Gb, and P4 2.4 processor.

So I decided to install Xubuntu 9.10 to run system properly. All works well, except some aplications, with animated graphics involved.

For example, the monitor system does not appear, and GNOMEtris works but background has errors (the block pieces work well). I attach 2 images with what I see.

I dont understand it, I checked the Ubuntu 9.10 live CD and works well, but Xubuntu is faster in this system and I would prefer to have Xubuntu here.

Someone have one idea to this? Why Ubuntu works and Xubuntu dont. Is not the same video driver?

---

### Post by spacecheck on 2009-11-04
> **pokepasa said:**
> Hi all.

I have and old laptop, Compaq Evo N1020v, with 256 RAM, 40 Gb, and P4 2.4 processor.

So I decided to install Xubuntu 9.10 to run system properly. All works well, except some aplications, with animated graphics involved.

For example, the monitor system does not appear, and GNOMEtris works but background has errors (the block pieces work well). I attach 2 images with what I see.

I dont understand it, I checked the Ubuntu 9.10 live CD and works well, but Xubuntu is faster in this system and I would prefer to have Xubuntu here.

Someone have one idea to this? Why Ubuntu works and Xubuntu dont. Is not the same video driver?

Not running Xubuntu, so unsure if xorg.conf is used with it. If so, you could try editing that file & restarting.
See this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13)
Adding the "EXA" entry began to work, but then crashed my Xsession, so I tried using "XAA" instead, and it seems to have worked so far.  Ciao

---

### Post by pokepasa on 2009-11-04
Thanks, but there is no xorg.conf file in my Xubuntu.
 
**Actualized**: Well, finally I've read this [link]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1304635&page=2") and I can have a xorg.conf file and configure it to solve the problem.

---

