---
title: "VIA/S3G Unichrome video card on an Averatec 3200..."
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by rla128 on 2005-06-20
I'm having some problems with the video, most notably when playing dvds.  Everything seems to work fine, but when I play a dvd with xine, it drops frames like crazy.  What can I do to fix this?

---

### Post by rla128 on 2005-06-24
Yeah, I've tried everyting I can, and video playback is still horrible.

---

### Post by recmar on 2005-06-24
Hi!
I have the same video card on my Acer and it performs exactly the same way. I think the problem is with 2D/3D hardware acceleration disabled even when using VIA driver. I found some information on [www.linux-on-laptops.com](www.linux-on-laptops.com) but still have no idea how to enable acceleration. :? 
Wish you luck.

---

### Post by mail2sona938 on 2005-06-24
Hi, I purchased a new Compaq Presario M2000 notebook and am having plans of installing ubuntu....will it detect all my hardware? plz help.

---

### Post by aaarg on 2005-06-25
i have the averatec 5400 with the same card and i experienced the same thing. i tried everything i could think of and still no good.......only one resolution with a whopping refresh rate of 0. made any videos/dvds look like .........

---

### Post by Rinnan on 2005-06-26
[QUOTE=aaarg]i have the averatec 5400 with the same card and i experienced the same thing. i tried everything i could think of and still no good.......only one resolution with a whopping refresh rate of 0. made any videos/dvds look like .........[/QUOTE]
 The S3/Unichrome is not fully supported by Ubuntu yet.  For example, 3D is not supported yet.  The video is slow in this chipset, it is possible to have fully smooth DVD playback, and I've done it (on other distros) on a Nehemiah M10000, but I had to do it through directfb.

---

### Post by rla128 on 2005-06-27
Recmar, have you found anything that's worked yet?

---

### Post by rla128 on 2005-06-28
Anything, anyone?

---

### Post by recmar on 2005-06-29
I'm sorry rla128 but I really have no idea how to fix this problem. Although I found that info on [www.linux-on-laptops.com](www.linux-on-laptops.com) about my Acer aspire:

[B]Graphic adapter

The VIA KM/KN400 is supported by the vesa driver of XFree86 4.x. In XFree86 4.4 the via driver fully support this chip. To use 3D hardware acceleration you need the file via_dri.so from the binary via driver. Put this file into /usr/X11R6/lib/modules/dri. Then you have to patch your 2.6 Kernel with via-v4l-1.4a-drm.patch.gz.[/B]

Notice that VIA KM/KN400 and Via/S3 Unichrome is the same video card.

---

