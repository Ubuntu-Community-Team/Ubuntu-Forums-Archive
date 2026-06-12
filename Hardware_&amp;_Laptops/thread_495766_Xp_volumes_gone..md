---
title: "Xp volumes gone."
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by madmox on 2007-07-08
I had access to all my ntfs and fat32 volumes right from the get go but I installed wine and they all disappeared.
I have tried uninstalling and ntfs 3g but they won't show up in the computer or in the usb drive's case, the desktop anymore.
Is there anyway to get them to list again so I have access?
I don't need to write to them only read access.
Thanks for any help, Dave

---

### Post by aquavitae on 2007-07-08
Open a terminal (under the menus somewhere) and post the output of the following two commands:
```

sudo fdisk -l
cat /etc/fstab

```
The first lists the drives and partitions in your pc, with the associated device names (e.g. /dev/sda1).  The second command lists the partitions that linux will mount.

---

