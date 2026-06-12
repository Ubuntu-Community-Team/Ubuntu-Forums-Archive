---
title: "Problems with back up drive"
date: 2008-10-20
forum: General Help
---

### Post by Titan8990 on 2008-10-20
I recently went on vacation for a week. When I get back I find that my backups have not been occurring. The drive is hooked up via USB due to issues I was having with extra internals with a my 3Ware RAID controller. 

The issue I am having is the backup drive is gone. fdisk -l locks up after finding the filesystem drive. lsusb does nothing either.

I can't unmount its location as it is showing that the device is busy. I used  grep to find the rsync processes that had been running for days and stopped them. The drive still showed as being busy.

Does anyone have any ideas on why this went belly up?

---

### Post by fjgaude on 2008-10-20
Suggest hardware failure of one form or another.

---

### Post by Titan8990 on 2008-10-21
Well, the issue was resolved from rebooting the computer. I really hope this was a one time thing....

---

### Post by fjgaude on 2008-10-21
I suppose you could have had a random memory error and the reboot fixed whatever the error set into motion.

Glad it's all running correctly now.

---

### Post by Titan8990 on 2008-10-21
Well, I can easily understand that this is hardware issue because when I had the drive connected via SATA instead of USB it would just lose the connection in a similar fashion. It would even cause the POST of the machine to hang.

---

### Post by fjgaude on 2008-10-21
All I can say is: have backups of all important data. I use three, one online, one near-line, and finally, one off-line. Designs don't come easy, notice my signature. <smile>

---

