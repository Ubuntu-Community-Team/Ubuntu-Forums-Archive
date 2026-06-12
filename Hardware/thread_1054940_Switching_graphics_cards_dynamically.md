---
title: "Switching graphics cards dynamically"
date: 2009-01-30
forum: Hardware
---

### Post by Michael.B on 2009-01-30
Hi,

I am looking at getting a Lenovo T400, on which I want to run Ubuntu.  From [www.linux-on-laptops.com](www.linux-on-laptops.com) I take it that it works.

There was one thing it does not cover; that is the possibility of switching graphic cards.  It comes with ATI Mobility Radeon 3470 discrete and Intel GMA X4500 integrated graphics cards.  The integrated uses less battery and the discrete preforms better.

On windows it is possible to switch between the two with out restarting.  Is it possible to do something similar on Linux?

---

### Post by bettlebrox on 2009-01-30
I just got a T400. Switchable graphics don't currently work under Ubuntu or any other version of Linux (yet). And it only works on Windows Vista (not XP). 

Otherwise, this laptop runs great under Ubuntu 8.10. To install Ubuntu you need to go to the BIOS settings and disable switchable graphics, and pick either the discrete or integrated graphics card to use. But you can't leave turn switchable graphics back on when Ubuntu is installed (it won't know what GPU to use).

If you look on the forum there's some hacks people have tried so they can boot into either the build in Intel GPU or the ATI GPU. I've been running with the ATI and get about 3 hours (or more) battery life with a 6 cell battery.

---

