---
title: "USB drive problems Linux/windows"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by paul cooke on 2007-02-01
Help...

I was transferring large quantities of files from my Linux partition prior to re-installing and I was using my Maxtor USB hard disk to do it with. I'd copied the files off the USB disk onto a Windows XP machine and then deleted the files by holding down the shift key and right clicking on their directories and selecting delete, but when I mount the disk back in Linux (dapper) Kdiskfree and gparted are convinced I've only got 6 GB free on it whereas Windows reports 46GB free...

I suspect it may be some weird Windows system restore information thing, but clearing the last restore point on that drive and turning system restore off for it isn't freeing up space for Linux and also using a wipe utility to wipe the "deleted" files hasn't helped either.

Basically I'm baffled... Both OSes report nothing in the trashcan/recycle bin for that drive...

Looks like I'll have to copy the files in windows and then do the deletion in Linux after mounting it back on the other box.

Unless you know better???

---

### Post by allwin on 2007-02-01
Was it an ext3 partition?  I'm thinking maybe the recovery journal is still being "seen" by Linux.  Just a flat out guess.  Don't know what to do with it, though.  Maybe e2fsk utility can come in handy here and right things.

---

### Post by paul cooke on 2007-02-01
> **allwin said:**
> Was it an ext3 partition?  I'm thinking maybe the recovery journal is still being "seen" by Linux.  Just a flat out guess.  Don't know what to do with it, though.  Maybe e2fsk utility can come in handy here and right things.

no, it's vfat, the only way you can have something seen by both Linux and windows and be able to read and write. Basically I left the USB drive as it came out of the box.

---

### Post by paul cooke on 2007-02-04
I have a work-around to restore my drive space. It involves NOT deleting the copied files while in Windows and doing all the deletions in Linux. 

To get my space back, I created a temporary directory in the USB drive and using windows, copied into it the files I'd previously copied over in windows, and then did the deletion back in Linux. 

I've got my space back but we still have this problem where space "free'd" in Windows isn't there in Linux... could windows be doing some freaky stuff and not really deleting files properly. Something to do with System Restore?

---

