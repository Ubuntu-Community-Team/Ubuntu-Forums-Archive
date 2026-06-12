---
title: "[SOLVED] Wrong Mount Point"
date: 2008-08-16
forum: General Help
---

### Post by momalle1 on 2008-08-16
I have two SATA drives, the first is partitioned for XP, Vista and Ubuntu 8.04, the second drive is a single partition called backup. I mount the backup drive via fstab with

/dev/sdb1 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0

sometimes it's fine, sometimes when I boot, the XP drive gets mounted to /media/Backup, so when I mount the Backup drive from the places menu, it mounts to Backup_ even if I unmount the XP drive first. Sometimes I need to sudo to unmount the XP drive, sometimes not. Also, when I unmount the mis-labeled Backup drive, /media/Backup_ goes away, but the /media/Backup for the XP drive never goes away, I can't delete it and I can't unmount it, it says "The Volume 'WinXP' is not mounted".

How can I fix this?

---

### Post by sisco311 on 2008-08-16
Mount the partition by UUID:
> UUID=<insert-the-uuid-here> /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0

To get the uuid :
```
sudo blkid
```

---

### Post by momalle1 on 2008-08-16
Should I add that line to fstab or do you mean to mount it manually? 

I added a line to fstab to mount the WinXP volume in a specific location, rebooted, and it mounted Backup in the proper location but did not mount WinXP and if I try to do it via the locations menu, it says I don't have permission. Is fstab the right place to be "auto-mounting"?

I should mention I really have no need to constantly mount the WinXP volume, just the Backup.

Thanks for the quick response.

---

### Post by momalle1 on 2008-08-16
Added the suggested line in fstab, all seems well now. 

Thank you again!

---

