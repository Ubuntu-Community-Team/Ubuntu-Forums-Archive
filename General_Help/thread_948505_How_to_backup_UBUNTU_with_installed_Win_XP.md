---
title: "How to backup UBUNTU with installed Win XP?"
date: 2008-10-15
forum: General Help
---

### Post by rado3105 on 2008-10-15
Hi, I have first installed windows xp on C/hda1/.
Then I installed ubuntu on hda3, hda2 is swap.
I use grub as bootmanager.
How to backup ubuntu and windows and also grub?

---

### Post by khughitt on 2008-10-15
Can you explain in a little more detail what your goal is? Are you planning to backup your documents and then wipe your hard-drive and reinstall everything?

---

### Post by rado3105 on 2008-10-15
No I want to make complete image of partitions with installed system/but only used space by system not free space/.
Maybe using some boot cd that can backup ext3 and MBR/probably needed by windows xp/. I want to do it because I am changing hardisk but computer will be the same.

---

### Post by az on 2008-10-15
Connect the destination drive, boot a live cd and run:

sudo dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc


That's assuming that your destination hard disk is sdb.

To find out what your disks are, run

sudo lshw -C disk -short


Then, open up the partition editor and adjust the partition table of the new disk to accommodate the new size.  If the target drive is the exact same size as the source disk, nevermind.

If you want to image each partition individually, you can use partimage from the live cd.  It creates a compressed image of the used blocks of a partition.  It can also back up the MBR.

---

### Post by KeyserSoze93 on 2008-10-15
If you want to backup from within ubuntu, use dd

If you want to backup from within XP, there is a neat (Open Source) tool called SelfImage that should do the job (and allows to to do stuff like compressing the image on the fly etc.)

---

