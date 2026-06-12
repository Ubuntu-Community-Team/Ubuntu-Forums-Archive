---
title: "MBR backup lost after installing ubuntu 8.10 &amp; winXP"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by p007pramod on 2009-03-17
Hi, 
I have been trying to get ubuntu 8.10 and win xp dual boot on my laptop for the last week but have not had promising results.

when I instll ubuntu after xp, it corrupts ntfs partition and xp doesnt boot up

so i went ahead, took backup of my MBR and decided to reinstall xp in the same partition I created before to install XP.

> **x33a said:**
> [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)



try

```

dd if=/dev/hda of=/media/disk/hda.boot.mbr bs=512 count=1
```

here /media/disk = location of the usb drive.

I took the backup of my mbr and Partition table using the command mentioned above on my ubuntu home folder (my biggest mistake so far I guess) and installed WinXp on the partition-1.

But after I comlete the XP setup and try to restore MBR through LIVE CD, i was shocked to see that entire HDD which had 20Gb ext3 partition (on which ubuntu was running) had disappeared...

Now I can not find my MBR backup file. Has anybody ever encountered such issue?? Please help me, I dont want to reformat my stuff again and again. I have already been through too much pain doing that couple of times...

---

### Post by dandnsmith on 2009-03-17
I've just been doing the process you mentioned for restoring the MBR and partition pecord, and it worked (some fine detail wrong, due to the 16 partitions I have, but that's another story).

I'm not clear what stage you were at when you took the backup - was this when XP was working, when linux was working, or what?

If the backup file is not 'visible', how have you tried looking for it? It should be visible to linux, provided the usb drive was mounted, and might be visible on a Windows system.

---

