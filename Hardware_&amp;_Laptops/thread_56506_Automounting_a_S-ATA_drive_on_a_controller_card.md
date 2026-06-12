---
title: "Automounting a S-ATA drive on a controller card"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by nim278 on 2005-08-12
I have 3 drives on my computer that have an NTFS file system and am trying to have them automount on boot. The relevant lines in my fstab are as follows:

/dev/sda1       /media/sata-ntfs  ntfs    nls=utf8,umask=0222 0       0
/dev/hda1       /media/maxtor-ntfs  ntfs    nls=utf8,umask=0222 0       0
/dev/hdd1       /media/old-ntfs  ntfs    nls=utf8,umask=0222 0       0

But only the IDE drives mount, the SATA drive does not. However, running "sudo mount /dev/sda1" will mount the drive after boot. On the text that shows up while booting it says something to the effect of the device not existing. Any thoughts?

Maciej

---

