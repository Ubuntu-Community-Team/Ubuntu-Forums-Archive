---
title: "ATI Mobility 7500 problems"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by andytayloruk on 2007-03-03
Hi,

I've just installed Ubuntu 6.10 Edgy Eft on my laptop and all is good, apart from the general speed of it. Dragging windows around shows up some serious lag, icons take a while to appear, minimizing and maximizing is slow, and certain web pages have incredibly choppy scrolling. Additionally DVDs are very choppy. 

I presume this must be something to do with my graphics card, and I've checked a few things; direct rendering is on, xorg.conf is using the ati driver (weirdly though, it shows a Radeon 9000) um... other than that can't really think of anything. I tried to use envy to update the drivers but it said my card was not supported. I've asked in IRC and people have suggested numerous things, none of which worked. One user said I should just give up because its not worth the bother.

Is there anything I can do to correct this? I'm pretty sure its the graphics card, nothing else could be slowing it down, I've got 1gb of RAM, 1.8 ghz P4 processor... 

Thanks!
Andy

---

### Post by Aparatey on 2007-07-27
Hello andytayloruk!
I have a Compaq Presario 1500US laptop that came with an ATI Mobility 7500 32MB. I have near a 1000fps according with glxgears.
But I'm using a 16 bit DefaultDepth with a 1400x105@60Hz resolution.
I have the followings options in  my xorg.conf  :

[I]Section "Device"
Identifier "ATI RADEON 7500"
Driver "radeon"
BusID "PCI:1:0:0"
VideoRam 32768
Option "AGPMode" "4"
Option "AGPSize" "32"
Option "XAANoOffscreenPixmaps"
Option "DRI" "true"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
EndSection[/I]

What options do you have in your ATI's device section?

Good Luck!

                                 Aparatey

---

