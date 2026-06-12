---
title: "Display Driver (OpenChrome) 'sort-of working' - garbled screen after login"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by slyfox on 2007-09-25
(First post; morning all!)

I'm currently working my way through the usual hardware issues that have presented themselves since installing Ubuntu 7.04 on my Gateway MX3220b laptop.

I've got wireless working following the ndiswrapper how-to's which is a great relief, however, I'm still having problems with getting Gnome working *properly* with the VIA OpenChrome driver...

After following the various how-to's etc without problems, I restarted my machine to be presented with the perfectly pixelated version of the login-screen, complete with 24-bit colour depth and 1280x768 resolution. I eagerly logged in only to have my excitement of getting it working crushed: as soon as I login the screen becomes garbled almost beyond recognition (banding present, can just about make out the cursor at four places on the screen etc)... 

I've tried altering colour-depth, turning DPI and various other options off via xorg-reconfigure; nothing works (well, the changes take place, but again, as soon as I login the display becomes garbled). The only thing that does work is setting the resolution to 1024x768 or below, then after login everything carries on as normal..

Anybody have any ideas as to why the display would work fine at 24-bit colour depth and the correct resolution (1280x768 ) for the login screen, but die as soon as the login takes place?

All help/advice would be greatly appreciated, no matter how obscure! :) I've spent hours looking on Google but have yet to find a cure :(

---

### Post by slyfox on 2007-09-26
Anybody? :(

I've spent a couple more hours Googl'ing to no avail :(

---

### Post by stefe on 2007-10-06
smae thing here, have a via k9 series.

Banding occurs to me also, have abondoned using the via drivers and gone back to vesa. not perfect, buit workable.

VIA chipsets have poor support, and heavily considering buying a cheap NVIDA or ATI graphics card.

Stephen


> **slyfox said:**
> (First post; morning all!)

I'm currently working my way through the usual hardware issues that have presented themselves since installing Ubuntu 7.04 on my Gateway MX3220b laptop.

I've got wireless working following the ndiswrapper how-to's which is a great relief, however, I'm still having problems with getting Gnome working *properly* with the VIA OpenChrome driver...

After following the various how-to's etc without problems, I restarted my machine to be presented with the perfectly pixelated version of the login-screen, complete with 24-bit colour depth and 1280x768 resolution. I eagerly logged in only to have my excitement of getting it working crushed: as soon as I login the screen becomes garbled almost beyond recognition (banding present, can just about make out the cursor at four places on the screen etc)... 

I've tried altering colour-depth, turning DPI and various other options off via xorg-reconfigure; nothing works (well, the changes take place, but again, as soon as I login the display becomes garbled). The only thing that does work is setting the resolution to 1024x768 or below, then after login everything carries on as normal..

Anybody have any ideas as to why the display would work fine at 24-bit colour depth and the correct resolution (1280x768 ) for the login screen, but die as soon as the login takes place?

All help/advice would be greatly appreciated, no matter how obscure! :) I've spent hours looking on Google but have yet to find a cure :(

---

