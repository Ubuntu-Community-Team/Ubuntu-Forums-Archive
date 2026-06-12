---
title: "Fatal Error on 'grub-install'"
date: 2008-08-18
forum: General Help
---

### Post by DDurcsak on 2008-08-18
Ubuntu Forum:

During the last part of the OS installation I receive a Fatal Error

Executing 'grub-install(hd0)' failed.

Should I be looking to install 'grub" at another point...there was a drop down list of locations??

I do have another hard drive. Both are in working order.

I was wondering if I should have chosen another of the options in the drop down list of install points for 'grub'??

/dev/sda (primary HD with partitioned for both WIN and Ubuntu)
/dev/sda1 MS WIN XP
/dev/sda2
/dev/sdb (Secondary drive partitioned for WIN data and Ubuntu Swap)
/dev/sdb5

Thank you

---

### Post by caljohnsmith on 2008-08-18
I've heard that is a bug that can be circumvented by formatting the Ubuntu partition to ext2 instead of ext3 when you install Ubuntu. Try that, and if it works you can later "ugrade" your file system to ext3 with:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know.

---

