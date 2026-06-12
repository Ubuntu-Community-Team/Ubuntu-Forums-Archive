---
title: "Question about reinstalling OS on a dual boot system."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by grs on 2009-02-12
I have Ubuntu 8.10 install in a PC that also has Windows XP on it, the PC has two drives, 1 with Windows XP and the other with Ubuntu.
I installed it by putting the disk in the drive when in XP a popup window had the option Install Within Windows, I selected that. What I'm wondering is if I reinstall Windows will I still be able to boot Ubuntu?

---

### Post by sleepyjon on 2009-02-12
No, you wont be able to boot ubuntu. XP will rewrite your MBR. That's not much of a problem though.

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by Mark Phelps on 2009-02-12
You said you installed "within windows" -- that means you used Wubi to install Ubuntu as an app inside Windows, even though you may have written the actual files to a different drive.

So, if you reinstall Windows, that will wipe out anything you did -- including the Ubuntu install. Don't know if it will wipe out the files on the other drive, but since you have two drives, a better solution might be to install Ubuntu on the other drive and dual-boot instead -- isn't that what you are planning to do anyway?

---

