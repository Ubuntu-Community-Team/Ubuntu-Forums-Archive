---
title: "Ubuntu 19 with nvidia p400 quadro"
date: 2019-05-17
forum: Hardware
---

### Post by blupace on 2019-05-17
Hey all, 

So i've really been struggling to get my NVIDIA P400 Quadro card working under ubuntu.
I have tried the proprietary drivers and the opensource ones, but each version just hangs my system.
I have to manually remove the card and revert back to the intel drivers for the motherboard.

I use my system for photo editing, CAD, and video editing. If the P400 is just a no go, then i will just sell it and get something a little more compatible.
Any help and recommendations welcome..

Kind regards

---

### Post by Autodave on 2019-05-17
That card should run just fine.  What version of Ubuntu are you using?  Are you using Wayland?

How about some specs for the rest of your system?

---

### Post by blupace on 2019-05-28
Hey autodave apologies for the late reply.

I'm running ubunto Disco Django, Ive managed to get the propriety nvidia drivers installed, but only under runlevel3.
When I switch to runlevel5 my system freezes, so it seems to be an issue when booting into the graphical inteface under runlevel5

Under runlevel3 I can run startx and everything just works.

---

