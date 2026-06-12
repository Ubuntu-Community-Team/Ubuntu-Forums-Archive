---
title: "How to add space to system files on a eee 701 from sd"
date: 2010-11-28
forum: Hardware
---

### Post by clearwood on 2010-11-28
Hello
I have a eee 701 with ubuntu remix on it and I want to upgrade to 10.04 from 9.04.
In order to be able to do that I need extra space on top of the 4GB internal hdd.  so I have added a sd card with 4GB on it and I have written in etc/fstab so that its got more space mounted.  But the 'system' is on one partition and the additional space is useless for upgrading so far.  can I change some configuration somewhere so that the system uses the sd card memory as well? In gparted I have two separate discs and I cant just resize the one to the other so that it all becomes one big disc.... Or can I?
Best regards

---

### Post by ajgreeny on 2010-11-28
> **clearwood said:**
> Hello
I have a eee 701 with ubuntu remix on it and I want to upgrade to 10.04 from 9.04.
In order to be able to do that I need extra space on top of the 4GB internal hdd.  so I have added a sd card with 4GB on it and I have written in etc/fstab so that its got more space mounted.  But the 'system' is on one partition and the additional space is useless for upgrading so far.  can I change some configuration somewhere so that the system uses the sd card memory as well? In gparted I have two separate discs and I cant just resize the one to the other so that it all becomes one big disc.... Or can I?
Best regards
No, you can not make those two partitions into one single partition as they are on separate disks.  It will be much more sensible to do a clean install of 10.04, and in any case, to upgrade from 9.04 to 10.04 you would need to do it twice, 9.04 to 9.10, then 9.10 to 10.04.  Really not worth doing, in my opinion.

Backup your home folder to the new sd disk, including all the hidden files and folders if you want to keep your configuration, having first formatted it to ext2, (or ext3 or ext4, but I think sd cards are best as ext2).  Then reinstall the system onto the machine, putting the root partition on the internal 4GB disk and putting your /home partition on the sd card, but making sure you do not format that partition during the install in order to keep all the home files you have just backed up to that disk.  You can easily do that by using manual partitioning (third option) when you install.  I think that will be the nearest you can get to what you want.

---

### Post by clearwood on 2010-11-28
Thank you for your reply.
Good idea.  It's just all that hassle having to first put remix 10.4 on a usb stick first.  By the way it's 9.10 I have on it now. Why is ext2 better than ext4 on the sdhc?
Best regards

---

### Post by ajgreeny on 2010-11-29
That is something to do with the number of read/write operations needed on a journaled file system such as ext3 or ext4, and the limited, though large I accept, number of operations guaranteed on sdhc cards.

ext2 is the same basic system, but without the journaling, and for a /home partition it should be fine.

---

### Post by clearwood on 2010-11-29
ok thanx

---

