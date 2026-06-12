---
title: "Hanging After Login"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Cindres on 2009-02-02
Well, my basic problem is this.
And i chose all variants because i had the issue in Ubuntu and Kubuntu.

I pop in the CD choose install Kubuntu (or Ubuntu), and install as instructed. Then i restart, remove the CD, Login....
That's it.

On ubuntu it hung at the orange screen, on Kubuntu it showed the drive icon, then the tools icon, then they dissapeared and that was it. 
I tried leaving it to see if it was just taking some time to load, but i left it for a good half an hour with no solution. The mouse is there, and responsive, but that's it.
(This issue i brought up as i was trying to install Kubuntu last night).

My specs are as follows:
CPU: Intel C2D, E6750 @ 2.66ghz
Memory: 2gb 
GPU: ATi Radeon HD4870 512mb
HDD: IDE 40gb (this is a spare one that im installing to, my main one is a 250gb SATA with Vista but i'm leaving that alone, the plan is to Dualboot).

Anything other info needed just ask and i'll find it out asap.

---

### Post by ajgreeny on 2009-02-02
I suspect you need to install/enable the proprietary graphics driver, but I'm not sure how you can do that if you have no GUI.  I am sure there will be a way, however, so wait for another answer.  You may just be able to get something up and running if you use vesa as your temporary graphics driver by editing the /etc/X11/xorg.conf file, but I'm not sure how much of that file even exists in 8.10.  Finally you can try booting to recovery mode from the grub menu, and then using **xfix** (I think that's what it's called) when you get to the small menu options.  I don't know if it will make any difference, but it is worth trying and may just get you a GUI.

---

### Post by Cindres on 2009-02-02
Well, i booted into recovery, ran xfix. Tried to boot, that didn't work.
I've got the official ATi drivers for my card now on a memory stick, but no way to install them.
I had another thing to say, but i forgot what it was..
EDIT: Now i remember
Another big issue
Ctrl+alt+F1, or CTRL+ALT+BACKSPACE both send me to a black blank screen, and my monitor pops up with "input not supported", i was going to use this to edit the xorg file but clearly i can't as this happens.

---

