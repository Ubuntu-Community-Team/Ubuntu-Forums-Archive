---
title: "disappearing text in menus"
date: 2008-11-11
forum: General Help
---

### Post by snuffler on 2008-11-11
Hello,
        As of the last couple of days several applications on my system have no visible text on most/all of their menus.The applications include

quanta,open office word processor and gFTP and there are probably more.
The text sometimes appears for maybe 0.3 second and then disappears when you make the menu box visible at first.All that is visible is a "-" character and the menu icons at left.I have noticed something similar with programs running on wine on my own computer and a friends but I dont have that particular problem right now.Just the first one and it is making the above programs useless so any help would be very much appreciated.I am wondering if someone has hacked into my computer or something.

---

### Post by snuffler on 2008-11-12
When I use an older kernel via the grub menu the problem disappears.I tried re installing the latest kernel (with synaptic package manager) but the problem persists with that kernel.I would like to be using the latest kernel if possible,any ideas where I can go from here?

---

### Post by vanepelw on 2008-11-13
Are you using an nVidia graphics card with the new version 09 driver?  That was my problem.  See the following post, which fixed it for me.

[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

---

### Post by snuffler on 2008-11-17
Thanks for that reply.I am using an nvidia graphics card with the version 0.96 driver.I followed the instructions according to the link but it didn't fix the problem.However I disabled the driver and that fixed the problem! 
That was one of the first things I had tried previously but I didn't reboot as I didn't see a message saying that I should.So I had assumed it was not a graphics driver problem.

---

### Post by misterdasher on 2008-11-30
That worked! I didn't bother with the HAL udpates, as the xorg.conf and Font fixes took care of the problem.

More than took care of it -- *all* of my fonts and menu bars look better.  Except for weird placement of the trash and volume controls, this is the best Ubuntu has looked since I finally started using it about 6 months ago.

Thanks!

---

