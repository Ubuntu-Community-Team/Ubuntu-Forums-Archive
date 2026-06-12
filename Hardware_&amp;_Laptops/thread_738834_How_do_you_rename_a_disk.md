---
title: "How do you rename a disk?"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by MONODA on 2008-03-29
I just realized that all of my USB flash disks and hard disks are named "disk". I want to change it to something like "Backup" how can I do it. BTW I am running gnome.

---

### Post by girishv on 2008-03-29
Hi,

Renaming of the disks depends on the format of the disk themselves. If they are formatted using
FAT32/NTFS, you can just plugin them to any windows system and rename by right clicking on the drive and selecting change drive/label name. Or, if you do not have any data on them, you can simply re-format the disk and while doing it, you can assign any name to it.

For ext2/3, you can use the label command of mke2fs

girish

---

### Post by MONODA on 2008-03-29
hmm well they are formatted to fat 32 and i dont have access to windows computers so...

---

### Post by metol on 2008-03-29
Hello,

I renamed a FAT32 flash drive a while back using mtools.  There is a nice How-To in the community docs: [RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive").

Regards,
Metol

---

