---
title: "Help diagnosing dead video card"
date: 2008-04-22
forum: Hardware
---

### Post by Zyrshnikashnu on 2008-04-22
Hey, Ubunteros, I'm looking for a little aid in diagnosing a recent problem with my video card. I think it's pretty much shot, but I'm no expert, so I'm looking for a second opinion. Here's the situation:

I booted Ubuntu (7.10) today and found that the screen went completely black and stayed that way after the boot completed (but before the login screen appeared).
I restarted and found the same results.
Suspicious, I tried booting Vista. Vista crashed without so much as showing me the boot-up progress bar, then asked to run in safe mode when I tried again. Safe mode also gave me nothing.
Fortunately, I was able to boot into Ubuntu's safe mode for terminal access and was able to take my class notes. :P
Later, I tried a normal boot again. This time, the X display config dialogue met me before the login screen and told me it didn't recognize my configuration. I left it on some safe settings, and now I have an ugly version of my Gnome desktop.

Hardware information:
Dell Inspiron 1420 laptop
Nvidia 8400M GS video card
Intel Core 2 Duo 1.5 GHz processor

I checked dmesg, but didn't find anything interesting. I've attached it for the sake of completeness, though.

EDIT:
Dell *assures* me that both operating systems suddenly don't recognize the card's drivers and I should reinstall Vista. This seems unlikely, but we'll see.

EDIT AGAIN:
I installed the drivers with Envy and suddenly everything works. Of course, this doesn't explain why Windows freaked out.

---

### Post by Fafler on 2010-12-07
It seems to be a quite common problem with with both normal and laptop geforce cards. 
The solder pads apparently looses connections to the PCB and that makes the card unstable.

You could try this procedure: [http://hardforum.com/showpost.php?p=1034145333&postcount=1](http://hardforum.com/showpost.php?p=1034145333&postcount=1) but it will be hard to do with a complete laptop board and you might ruin something else instead.

Edit: Or even better: [http://hardforum.com/showthread.php?t=1531323](http://hardforum.com/showthread.php?t=1531323)

If you're real lucky, you might have a MXM board. Look at [http://www.mxm-upgrade.com/Table.html](http://www.mxm-upgrade.com/Table.html)

---

