---
title: "Video graphics card compatibility database"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by AchimRS on 2008-02-23
Hi,
is there a kind of video/graphic card compatibility database available somewhere, like for scanners in the sane project?

I search for an older / cheaper card, which:
- Is fully supported from the Gutsy installation and display configuration diaglog (prevent editiing xorg.conf)
- which supports hibernate (not like my ATI card, which prevents s2disk)
- which supports games (like Die Siedler II DirectX 9c and Vertex shaders)
- supports 3D effects
- allow plugging in my DVI monitor and an addition VGA
- can  be plugged into AGP

Probably it is a NVidia 6000er series...

---

### Post by toa on 2008-02-23
In the old days, you had Trident, S3, Nowadays, the main graphic hardware providers nVidia, Intel, ATI and other matrix and stuff.

---

### Post by AchimRS on 2008-02-23
OK, I search for more detailed information. I.e. Are the following cards/chips supported well:
- NVIDIA GeForce 6200
- NVIDIA GeForce FX5600

Thanks
  Achim

---

### Post by JontomXire on 2008-02-23
Possibly not.

If you search for problems relating to Xorg/desktop freezes (where everything freezes except the mouse which moves but doesn't change cursor) you find the problem always seems related to having an NVidia graphics card.

Some people say they manage to solve the problems they are having, so you might be ok, but if you want to avoid having any problems at all you may be better off going for a non NVidia graphics card. ATI cards also seem implicated with this problem.

Personally I think it is an Xorg/X server problem, but hey, what do I know?

---

### Post by Yellow Pasque on 2008-02-23
I think your best bet would be to try and find a used nVidia 6600GT AGP

ATI Catalyst has major issues with AGP, so that eliminates ATI

---

