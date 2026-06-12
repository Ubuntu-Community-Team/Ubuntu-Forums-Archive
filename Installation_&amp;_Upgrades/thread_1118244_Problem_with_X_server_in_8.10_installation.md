---
title: "Problem with X server in 8.10 installation"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by ger_macaco on 2009-04-06
I am trying to install Ubuntu Intrepid Ibex 32bit on an old PIII PC with a SIS 6326 PCI video card.

Video card is working fine, as I can perfectly see the first menu (Try Ubuntu - Install Ubuntu - etc.).

However, when trying to install, after the progress bar is completed, X Server fails and the screen remains completely black.
It sometimes goes to command line and tells me X is not working.

Why does it work in the beginning and not after the progress bar?
How can I configure X to work on this computer?

Many Thanks

---

### Post by upchucky on 2009-04-06
you are gonna have to manually set up the screen and resolution settings in the /home/etc/X11/xorg.conf

mine is nvidia so posting it here wont help you but you should be able to search here for your card and resolution settings or in the video card forum area.

---

