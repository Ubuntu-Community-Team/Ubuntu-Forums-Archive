---
title: "Monitor plugged into motherboard boots up to black screen."
date: 2016-05-17
forum: Hardware
---

### Post by sagarmonkeyboy on 2016-05-17
Hey, I just did a fresh install of Ubuntu-Gnome and I am having some trouble getting my 3rd monitor to work. My set up consists of 2 monitors plugged into my GTX 970 graphics card, and one plugged into the mother board. The one plugged into the motherboard is booting up to a black screen. This set up works perfectly on windows, so its not a bios related problem (I have enabled the options in the bios).

After doing a lot of research, I have a feeling it has something to do with the grub. When I boot up the computer initially, the monitor does show an image of the ubuntu-gnome loading circle, but promptly freezes while the other two monitors load up the login screen. At this point the the other two monitors are displaying the login screen while the motherboard monitor is displaying a frozen image of the loading circle. Note that I can't slide my mouse over to that monitor either. Once I hit login all three monitors go black and the 2 monitors load up the desktop while the mother board monitor remains black. The monitor at this point isn't "off", its on but just displaying 100% black.

I have installed the Nvidia proprietary drivers for my graphics card and tried several things in Grub like setting nomodeset and removing the splash altogether but the most I have got it to do is display some terminal output on that monitor ([http://imgur.com/By9OEQJ](http://imgur.com/By9OEQJ)). Another thing to note is that plymouth crashes on startup as well.

Any ideas?

---

