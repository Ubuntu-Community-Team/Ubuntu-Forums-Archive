---
title: "Need help installing my ati radeon 200m drivers on 9.04"
date: 2009-05-15
forum: Hardware
---

### Post by DarkenSX on 2009-05-15
Hi I need help installing my Ati radeon xpress 200M card on ubuntu 9.04 desktop edition
on my Toshiba Satellite A135-S2256 laptop i have already downloaded the drivers that were on ati's website but thats as far as i got. please let me know what info you need to assist me with this problem and ill try to provide it as best as i can.
My Specs:
Model: Satellite A135-S2256
Video: Ati radeon xpress 200M R410
Processor: Intel Celeron M 430 @ 1.7Ghz
Ram: 2GB
OS: Ubuntu 9.04 "Desktop version"
__________________
Also im aware that im using desktop os on a laptop Reason was i couldnt boot from usb for laptop remix. thxs vista

---

### Post by dawonn on 2009-05-18
Same laptop, same issue. No solution yet. Just installing the catalyst driver ended up giving me a dead Xserver, so don't recommend that. If you get it working, please post what you did!):P

From what I read, it hasn't sounded good so far though. T_T

---

### Post by eggplant37 on 2009-05-25
> **DarkenSX said:**
> Hi I need help installing my Ati radeon xpress 200M card on ubuntu 9.04 desktop edition
on my Toshiba Satellite A135-S2256 laptop i have already downloaded the drivers that were on ati's website but thats as far as i got. please let me know what info you need to assist me with this problem and ill try to provide it as best as i can.
My Specs:
Model: Satellite A135-S2256
Video: Ati radeon xpress 200M R410
Processor: Intel Celeron M 430 @ 1.7Ghz
Ram: 2GB
OS: Ubuntu 9.04 "Desktop version"
__________________
Also im aware that im using desktop os on a laptop Reason was i couldnt boot from usb for laptop remix. thxs vista

Be aware that since the release of 9.04, xorg-server 1.6 is now the default Xwindow server.  ATi's commercial drivers from version 9.3 and earlier won't work with that version. ATi's commercial drivers from version 9.4 on have now also dropped support for what they call "legacy" cards, including some of the lower end chipsets that are only 2-3 years old and including the Radeon Xpress 200m. 

Why they did these things, I have no idea. They claim that it's so they can focus on writing better software to support their newer chipsets, but they've effectively abandoned a huge segment of their user base. Others that I've spoken to about the problem say the same as I do, that they'll never buy another ATi product again until this situation is cleared up and these older chips supported again in the commercial driver.  For now, we have to wait until better open source driver code gets written. 

Of course, the biggest stumbling block is getting ATi to release specifications on how to program this hardware, but the usual BS corporate excuses about protecting intellectual property come into play. I have no problem with them keeping their secrets safe, but what's secret about getting hardware to work with software using standardized OpenGL calls?

There's hope: In the last month, we saw ATi release specs on their R600 line of chipsets. Let's hope they get better specs out so that the xorg folks can work on better open source drivers for this gear.

I should add, too, that in order to solve this, I would have had to do a reformat/reload. Since all I had on this laptop was an 80gb drive, I upped it to a 320g and installed back to 8.10 from scratch, then moved data from the old drive. I wasn't all that happy to have to do it, either.

---

### Post by dawonn on 2009-05-26
I should note that the Open Source driver works REALLY well on this chip. All the Desktop effects and goodies are running great!

What I need the proprietary drivers for is FFXI, where there are no textures rendered in the FOSS drivers. T_T Interestingly enough the same thin happens on an intel, ATI, and Nvidia card.... If I install the Closed Source Drivers for Nvidia or another ATI card, life is good.... 

I just wish I could be of help adding in the last touch of support to free myself and others...:KS

---

