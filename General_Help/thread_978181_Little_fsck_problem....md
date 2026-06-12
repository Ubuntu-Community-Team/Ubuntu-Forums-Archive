---
title: "Little fsck problem..."
date: 2008-11-10
forum: General Help
---

### Post by MartyBuntu on 2008-11-10
So recently I did a clean install of Ubuntu 8.10. Previously I had been using Kubuntu 7.10.

For about 2 years now, I've done my system backups with Acronis True Image, no problems until I installed Ubuntu 8.10 (which is the only OS on my computer), now when I fire up my Acronis bootable recovery CD I've always used to do backups, I get a message saying "Some partitions contain errors and can be imaged only by sector-by-sector..."
So...okay, I can do a sector-by-sector image...but I think I might have a problem with my partition structure.

Okay, I load up the Ubuntu 8.10 LiveCD and start running fsck on my known partitions...(I have 4 hard disks in this computer...1 is for my OS and three are for storage)...

I get this message:
"Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd2 Could this be a zero-length partition?"


So, my partitions may be "messy" but my system is bootable and I can still mount any needed partitions. I'd still like to have "clean" partitions. I understand there may be a problem if the contents of my /etc/fstab do not match what are reported by fdisk...How can I procede?

---

