---
title: "Windows vista or 7 fails to boot after moving the partition."
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Mgiacchetti on 2009-03-13
Here we go, learn from this guys.

Situation...

You had Two installs of vista, win7 or whatever.  
You also decided that the second one you installed is obsolete.
You also deleted that partition using windows' disk management area.

You also have installed ubuntu, and placed the GRUB on the MBR.


How to fix it....
More than likely, without knowing it, you installed windows' boot loader to the partition you have just deleted.

This is a simple fix, if you happen to have the disk with the windows OS you wish to keep.

Pop the disk in, and boot from it.  

It will scan your system, and tell you there are problems.  Let it fix them, reboot, choose windows loader, it may give an error here, continue.

You will enter the CD again, (automatically) and continue the process until it is repaired.

This WILL NOT MESS UP GRUB.


Hope this helps someone.

---

### Post by Mgiacchetti on 2009-03-13
Please also CHKDSK DEFRAG CHKDSK before doing ANYTHING with a windows partition!

---

