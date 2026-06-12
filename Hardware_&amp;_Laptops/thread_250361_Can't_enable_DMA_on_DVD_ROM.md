---
title: "Can't enable DMA on DVD ROM"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by jdunn on 2006-09-04
DMA works fine for my harddrive but I can't enable DMA on my DVD ROM.  DVD play-back on Kaffeine is a little sluggish.  I've tried everything here:

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

and had no luck.  I also checked BIOS settings.  I even tried different versions of firmware for my DVD ROM.  Here's some info on my system.  ABIT IS7 ( uses Intel IH6 chipset), Pioneer DVD-115 (tried firmware 1.22 and 1.33), Kubuntu 6.06 (up-to-date) with 686 kernel.

What can I try next?  What might be the problem?  ](*,)  ](*,)  ](*,)

**Solved**
Something on the DVD drive went bad.  I replaced it.  Now I have dma support and smooth DVD play.

---

### Post by jdunn on 2006-09-04
Bump.  I need to have this solved please.

---

### Post by wargames on 2006-09-17
I use Gnome so I'm not for sure where this option would be in KDE, (I used gconf-editor to change this) but I've had issues with DMA on my DVD burner drive and watching DVD's were jerky. Dapper would not leave DMA on until I turned off autoplay for DVD's. Try to turn off autoplay for DVD's and then reboot, and see if DMA is turned on and if not go ahead an enable it and then try to play a dvd. It's seems like alot of problems with Dapper and DVD drives from what I've read in the forums.

Hope with helps. :D

*My bad...I didn't see that you already solved your problem with a new drive.*

---

