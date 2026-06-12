---
title: "Xorg failures on 11.04"
date: 2011-05-03
forum: Hardware
---

### Post by egandt on 2011-05-03
I have a new System on which I want to install Linux.  I have the following issue however I have have 3 screens:

23": 1920x1080
23": 1920x1080
20": 1600x1200

I also have an ATI HD5570 Video card (which supports 3 monitors), however X crashes any time I try to configure all 3 displays at the same time (nice that).  So I purchased a second adapter (1x PCI-E as that is all I had to work with): a ATI HD4500 series card.  Now from the command line I can run:

aticonfig --lsa
* 0. 01:00.0 ATI Radeon HD 5570
  1. 03:00.0 ATI Radeon HD 4300/4500 Series       

* - Default adapter

Which shows both adapters, but in X when running amdccle I only see the 2 screens attached to adapter 1 (the 5570) and the second adapter is displayed as unknown (see snapshot).  To make matters worse I use 3 separate desktops in X so that I can have a total of 18 virtual desktops open at any 1 time, but the mouse pointer on Desktop 2 (when not extended) is a mess of pixels that can not be be described.  Interestingly it is not messed up in the screen shots (see below) however you will notice there is not boarder on the window and I can not type in the windows (you have to take my word for this).

The first thing I need it to figure out how to get the display driver from ATI to display the monitors attached to each video card, which exist or else how to use the open source driver, as I do not need 3d support, but if I remove the firegl driver, then Xorg -configure fails saying no driver matches the hardware present, even though the 5570 is listed under supported devices.

Basically I now have a great system, which works fine as long as you do not want or need X or at least more than a single monitor configured, which is just unacceptable!, in Windows yes that nasty OS all 3 monitors worked right away and without issues, so I know its all drivers and configuration related, but that does not make anything easier!

Partial FIX: The second monitor goes away if I disable compiz, so it now that works,  Now I just need to work out the problems with the monitors themselves.

ERIC

---

