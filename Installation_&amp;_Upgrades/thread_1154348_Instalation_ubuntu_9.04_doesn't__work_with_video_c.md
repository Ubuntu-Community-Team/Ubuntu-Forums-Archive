---
title: "Instalation ubuntu 9.04 doesn't  work with video card NVIDIA 6500"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by dexter_123 on 2009-05-09
I'm trying install ubutnu 9.04 in my computer, but when I select the first option of live cd my computer lock.
When I remove my video card NVIDIA GEFORCE 6500 and use my on-board video card, it's run.
I tried with kubuntu 9.04 and i had the same problem. With older versions of ubuntu 8.04/8.10 I don't have the problem.
Someone knows how to fix it ?

---

### Post by tommcd on 2009-05-09
When you boot the live CD, hit F6 for more boot options and choose "install with safe graphics mode" or whatever it says exactly.

If that does not work, try installing with the onboard graphics. Then put the nvidia card back in and see if you can install the nvidia driver from the Ubuntu repos using: system > administration > hardware drivers.

If that does not work, you could try installing from the alternate install CD. Use the 32 bit alternate install CD for the most fail safe install.

Did you disable the onboard video in the BIOS when using the nvidia card?

And welcome to the Ubuntu forums!

---

### Post by dexter_123 on 2009-05-10
thanks for your explication. I'll try with the alternate CD.
I tried with safe mode graphic and I had the same problem.
My Bios don't have option to disable on-board video card I just put the NVIDIA viddeo card and it's run, but I'll looking for in manual of mother-boardl.

Thanks for your attetion.

---

### Post by dexter_123 on 2009-05-12
I tried install with alternate CD and didn't work too. Them I tried install with my on-board video card and after installed I put the NVIDIA video card and didn't work too.
I'm thinking that my mother-board Asus _P5VDC-MX_ has a conflict with NVIDIA video card.

---

### Post by dulzuras on 2009-05-27
Same problem with nvidia 6800 (w 256 Meg). Asus P5WDH. 4 gig RAM, 500 Gig HD. Installation and OS worked with 8.10. Tried to install from Live disk, Alternate install disk, Tried to update 8.10 from disk, no joy. Screen display/resolution goes weird and install locks up. Glad to see I am not the only one with issues. Hope someone can help.

---

