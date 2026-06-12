---
title: "Troubled Bamboo P&amp;T"
date: 2011-06-03
forum: Hardware
---

### Post by KindOfLikeLint on 2011-06-03
Heya. I'm setting up my Wacom Bamboo Pen and Touch on a recent install of Ubuntu 10.04, and it's working except for a problem where after I press the pen on the tablet, it will no longer recognize any hovering motion until I take the pen out of the hovering range, which makes drawing impossible. I've installed the same tablet before without this problem, which is ever so vexing, though that might have been on 10.10. It seems to be the same problem discussed in this thread [http://ubuntuforums.org/showthread.php?t=1758579](http://ubuntuforums.org/showthread.php?t=1758579) and I've gone through the HOWTO and the commands

sudo dkms remove -m wacom -v 0.8.10.2 --all

sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

in the appropriate location without getting any error messages and rebooted, but it didn't solve the problem and I haven't been able to keep track of what was being done in that thread halfway through the second page after Kurtless got the stat error which I'm not facing.

I've been using Ubuntu for a couple months, so I know a just little bit about getting around (i.e. how to look up and paste commands, and what "sudo" means).

Any help will win you the appreciation of some guy you never heard of from somewhere out in the world.

Love <3

---

### Post by KindOfLikeLint on 2011-06-04
I couldn't figure out what was wrong, but I finally managed to fix it the old-fashioned way, by removing everything Wacom-related and reinstalling from scratch, which I had to try twice, though I don't know what I did differently... Probably something subtle somewhere in the instructions I was prone to getting tangled.

*smokebombs, disappears*

---

### Post by Favux on 2011-06-04
Nice work.  :)

---

