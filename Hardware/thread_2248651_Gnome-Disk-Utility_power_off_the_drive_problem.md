---
title: "Gnome-Disk-Utility power off the drive problem"
date: 2014-10-16
forum: Hardware
---

### Post by argonvegell on 2014-10-16
Whenever I use the 'Power off the drive' option on Gnome-Disk-Utility, my USB Flash Drive does power off, but after a few seconds, my USB Flash Drive powers on again, how do I fix this, so I can safely remove my USB from the USB port?

My OS is Xubuntu 14.04.

---

### Post by ajgreeny on 2014-10-16
It may remain powered up but as long as the drive does not remount itself automatically you should be able to remove it without problem, just the same as a separately powered USB drive, where you simply remove the power supply once it's unmounted.

---

### Post by Stormlord on 2014-10-16
I'm using Xubuntu 14.04 too.  The system installs udisks2 and certain GUI apps, like the Power manager for example, are not compatible with it and that's why the hard disk management options appear disabled in the power manager.  I am always installing udisks after a system installation and power manager options appear ok again.  I have a similar flash drive I switch off the same way and it stays off till I unplug it.  Try installing udisks and see what happens.  It does not remove udisks2.  You just have both installed.

Other than that, ajgreeny is right.  Make sure it's unmounted and unplug it.

---

