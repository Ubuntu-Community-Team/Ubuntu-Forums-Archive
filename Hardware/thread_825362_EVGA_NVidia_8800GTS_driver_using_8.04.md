---
title: "EVGA NVidia 8800GTS driver using 8.04"
date: 2008-06-10
forum: Hardware
---

### Post by Tanilu on 2008-06-10
Had a ATI Radeon X900 card that worked wonderfully in 7.10.  Had beryl set up very nicely too, but needed to stop usage for school, anyway...
After having this EVGA nvidia 8800 gts card for about 6 months i switched to ubuntu 8.04.
Ubuntu automatically detected the card and prompted for the restricted graphics drivers.  I installed the driver, and the resolution was very very small, was about 640X720.  Without the drivers I can get my desired 1280X1024.  With the restricted drivers I hope to play EVE, but the resolution needs to be higher.
After attempting to change the screen resolution (System -> Preferences -> Screen Resolution), it diplays an error:
> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
If any more information is needed, feel free to ask.  I did some searching for this problem, and found some that sounded similar, but was unable to find any that are close to this problem.
> **jrharvey said:**
> 8500, 8600 and 8800 gt work automatically. Im not sure how GOOD the ubuntu drivers are but it works. I am not sure about 8800 GTS, GTX, Ultra or GTS (G92). from [http://ubuntuforums.org/showthread.php?t=822445&highlight=8800+gts]("http://ubuntuforums.org/showthread.php?t=822445&highlight=8800+gts")
others that I looked at:
[Screen Resolution - x server does not support the xrandr]("http://ubuntuforums.org/showthread.php?t=756000")
[xrandr wont let me change resolution]("http://ubuntuforums.org/showthread.php?t=760780")

---

### Post by dinub1 on 2008-06-10
> **Tanilu said:**
> After having this EVGA nvidia 8800 gts card for about 6 months i switched to ubuntu 8.04, had a ATI Radeon X900 card that worked wonderfully in 7.10.  Had beryl set up very nicely too, but needed to stop usage for school, anyway...
Ubuntu automatically detected the card and prompted for the restricted graphics drivers.  I installed the driver, and the resolution was very very small, was about 640X720.  Without the drivers I can get my desired 1280X1024.  With the restricted drivers I hope to play EVE, but the resolution needs to be higher.
After attempting to change the screen resolution (System -> Preferences -> Screen Resolution), it diplays an error:

If any more information is needed, feel free to ask.  I did some searching for this problem, and found some that sounded similar, but was unable to find any that are close to this problem.
 from [http://ubuntuforums.org/showthread.php?t=822445&highlight=8800+gts]("http://ubuntuforums.org/showthread.php?t=822445&highlight=8800+gts")
others that I looked at:
[Screen Resolution - x server does not support the xrandr]("http://ubuntuforums.org/showthread.php?t=756000")
[xrandr wont let me change resolution]("http://ubuntuforums.org/showthread.php?t=760780")

Why not go back to nVidia 8800 GTS card? It works wonderfully on mine... and at 1900 x 1650 (?) on my screen. It is a better card...

---

### Post by tenmoi on 2008-06-10
Have you tried using the driver provided by Nvidia?
Search this forum for threads on a PROPER installation.

---

### Post by Tanilu on 2008-06-10
> **dinub1 said:**
> Why not go back to nVidia 8800 GTS card? It works wonderfully on mine... and at 1900 x 1650 (?) on my screen. It is a better card...
That is what I am currently using, changed the wording around to make more sense.
Will try searching for the proper installation method tomorrow after work.

---

### Post by Victormd on 2008-06-10
Try installing the driver using Envy-ng (in the repos as envyng). That's how I got my to work...

If using Ubuntu, install the envyng-gtk. If using Kubuntu, use the envyng-qt. I will show up under Applications>System tools

---

### Post by Tanilu on 2008-06-11
Thank you for the recommendation of [envy-ng]("http://www.albertomilone.com/envyngfaq.html#A"), using this, the drivers are installed, but the problem still persists...

---

### Post by nbayiha on 2008-06-21
Are u still having that problem ?? 
If it's the case try to follow these instruction and u should have it fixed .

[http://ubuntuforums.org/showthread.php?t=765985&page=3](http://ubuntuforums.org/showthread.php?t=765985&page=3)

---

