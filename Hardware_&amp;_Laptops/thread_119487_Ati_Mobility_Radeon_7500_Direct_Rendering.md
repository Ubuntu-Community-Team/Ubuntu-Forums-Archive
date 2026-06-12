---
title: "Ati Mobility Radeon 7500: Direct Rendering"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by dresnu on 2006-01-19
Ok, I'm so desperate with this issue. I have searched in tons of sites, forums, threads. Everyone suggesting millions of different solutions. From the most easy to the most "exotic". I have tried every single one of them. I have changed my xorg.conf thousands of times. And the result is nothing! 

"Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect"

I'm really asking for help from those(lucky) people who have succeeded in using direct rendering with their radeon. I would appreciate alot if someone who made it, could possibly show me step-by-step how I can reproduce the same result on my machine. 

Ps: To those people with other ati cards, even the most "similar" to the 7500, don't post here. Just ATI MOBILITY RADEON 7500, thank you.

I'm running kubuntu 5.10 on an evo n610c laptop

---

### Post by dresnu on 2006-01-21
*just bumping this one*

(sorry for not posting it in the video and sound subforum, my mistake)

---

### Post by dresnu on 2006-01-24
Ok, I found the solution. It turns out that you need xorg 6.9 to have the radeon(DRI) driver properly working. For anyone interested what I did was go here [http://dri.freedesktop.org/wiki/Download](http://dri.freedesktop.org/wiki/Download) follow the instructions for installing xorg, then go here [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) and download the latest common and radeon archives. Then just install these two and you should have direct rendering working ;)

---

### Post by dengzhiqiang on 2007-01-03
I also have an ATI Radeon Mobility 7500. I can't seem to get direct rendering to work either. 

I'm running Edgy Eft, and using the "radeon" driver. Seeing as this thread is almost a year old, I was wondering if there are any newer ways to get it up and running.

---

### Post by Jaxilian on 2007-05-02
I have a Evo N610C with ATi radeon 7500 and Direct rendering worked out-of-the-box with ubuntu 7.04. I can even run Beryl without any problems.

guide: [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by kaede on 2007-05-02
i think the first step u need to do remove the  fgrlx module

---

