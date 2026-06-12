---
title: "Recurring error in ext4 partition superblock"
date: 2016-07-03
forum: Hardware
---

### Post by alechemi on 2016-07-03
Hi.
I have a ext4 partition on a usb drive (/dev/sdg2). Every time I eject/reinsert it (or even umount) something the fs type gets lost (gnome-disk-utility shows it as unknown).
fsck recognizes it as clean, and if run with -fy fixes it in about 10 minutes, with always the very same output about wrong free inodes number in various groups.
SMART test nor fsck -c record no hardware fault, yet the FS keep getting corrupted. Other partition on that disk give no problem.:confused:
There is no unreplaceble data on the partition, yet being 240GB in 25+M files deleting and recreating it is not a work I'd like to do "just to try".
Any hint?

Thanks

---

