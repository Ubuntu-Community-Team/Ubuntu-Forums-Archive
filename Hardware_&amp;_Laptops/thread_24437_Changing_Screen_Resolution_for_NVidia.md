---
title: "Changing Screen Resolution for NVidia"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by Ducatisti on 2005-04-06
Well, I am an Ubuntu newbie and I can't figure out how to change my screen resolution past the three default sizes and one available (60) Hz setting.

I have installed the NVidia drivers with the Synaptic Package Manager but new resolutions and Hz settings have not appeared as viable optional settings.

Currently, I use my monitor with three computers and I prefer 1280 x 1024 at 75 Hz for the other two machines.  With the Ubuntu machine at 1024 x 768 at 60 Hz, some of desktop is skewed off the right side of the screen and I would have to adjust the default settings on the CRT display to correct it but that would throw off the display for the other two computers.

How do I increase the optional settings for the Ubuntu display with this NVidia card?  Any help would be appreciated.

Thanks,
Ducatisti

---

### Post by soul_rebel on 2005-04-07
go on your monitor manufacturer's website and find its specifications in terms of refresh (horiz and vert)

Then edit /etc/X11/xorg.conf and correct those values. Probably this is the only thing you need.

---

