---
title: "USB drive automount at cdrom1"
date: 2008-10-28
forum: General Help
---

### Post by shador on 2008-10-28
I have a 160 GB Lacie USB drive that by some reason decided that it should automount itself on /media/cdrom0

I would like to setup so that the drive automounts it on a proper location so that I can actually use it ^^

Problem is I don't know much about fstab. The device's name is sdb1.


EDIT: Ubuntu fixed my problem! I removed the line with sdb1 and the system then created a correct mount point after I removed and plugged in the device again.

---

