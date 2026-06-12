---
title: "[SOLVED] How do I install xserver-xorg-video-via in Ubuntu 8.10?"
date: 2008-11-05
forum: Hardware
---

### Post by 09buntu on 2008-11-05
Hi! My laptop adapter broke today so for now I'm stuck with an old latptop with the ultimate graphics card from hell:

VIA integrated K8M800 UniChrome Pro

The openchrome driver that comes with Ubuntu.. just forget it! freezes X/gdm on boot. Yea some people claim they had that driver working 4 years ago.. good for them. And vesa is well.. vesa.

So.. Is there an easy way to install xserver-xorg-video-via in Ubuntu 8.10? I'm pretty sure that driver works ok with this chipset. If not I'll throw some other distro in this old box.

Thanks

---

### Post by killwin on 2008-11-06
Hello,
   I've got a similar problem with an Amilo li1705 laptop. I was ok with previous Ubuntu versions (well, so, so really because it's necesary to include "Display" subsection with Virtual option manually) but now, first time I got freeze screen on gdm. I've resolved it including the option "AccelMode" equal to "EXA" in xorg.conf but now I cannot use desktop tools to chan apperance or wallpaper because X server crash.

Regards.

---

### Post by ThomasJ02 on 2008-11-06
Same here - Is there some way to use the Hardy VIA package in Intrepid?

---

### Post by 09buntu on 2008-11-07
I solved this by buying a new adapter for the laptop with the nvidia card. :lolflag:
Still, I think it's a stupid decision to remove the working via driver from Ubuntu and replace it with a non working openchrome one.

---

