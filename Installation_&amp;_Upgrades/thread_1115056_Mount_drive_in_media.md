---
title: "Mount drive in /media"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by houcem on 2009-04-03
F-Spot indicates "These files are on apicture CD" while I'm browsing a hard drive, I have mounted my windows partition and my storage partition (both NTFS) in /media instead of /mnt, in the windows one there is no message.
So is there a difference between mounting disks to /media and /mnt?

---

### Post by cariboo on 2009-04-03
Ubuntu auto mounts drives in /media by default. It should make any difference where the drives are mounted. I mount my second internal hard drive, formatted as ext4, in /home using fstab, and my external eSATA drive automagically mounts in /media.

Jim

---

