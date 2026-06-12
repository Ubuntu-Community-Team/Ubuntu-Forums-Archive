---
title: "ext2 driver in windows sees fat partition"
date: 2009-07-14
forum: Hardware
---

### Post by PurposeOfReason on 2009-07-14
A long time ago my storage hdd was a fat32 partition read on windows and linux. I got annoyed with the size limit and changed it to ext3 knowing I could install the driver for windows. The problem is, windows is still convinced that it is a fat partition and everything sees it as such. If I uninstall the device and reboot, windows lovely "searching reconfigured folders to install devices" pops up with no cancel option, because nobody would ever want to stop it. Thus, it rethinks it is a fat partition and I'm back to where I started.

---

### Post by lukeiamyourfather on 2009-07-14
How was the disk converted to ext3? Its possible that the disk was converted but some metadata on the disk that Windows is looking at wasn't changed. If another disk is available to temporarily store data, remove the partitions and setup the disk again with something like gparted. Cheers!

---

### Post by PurposeOfReason on 2009-07-14
It wasn't converted, but fully rewrited with cfdisk. I tried a different utility that sees the file system as ext3, but the partition type is fat32 and not linux like it should be. I don't feel like backing up 300GB right now. Would changing the partition type delete data?

Did it and all was good. Sadly the inode was 256 and the drive can't use that, but I found another that could.

---

