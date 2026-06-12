---
title: "Problems accessing ntfs drive"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by FredPiano on 2006-09-04
One of my computers recently tanked, so I took the hard drive out and put it in my Dapper machine as the primary slave.  It shows up fine in Bios, and after some messing around, I got it mounted with ntfs-3g.  Unfortunately, when I try to open it, it says "you don't have the priveleges..."  I can only get into it as root.  This is what I get when I try to chmod: "chmod: changing permissions of `/media/<mount point>': Operation not supported" and the same thing happens with chown.  When I'm root, I can't copy anything from the partition.  I do cp /media/<mount point>/Music /home/<user>/Desktop and it gives me "cp: omitting directory `/media/<mount point>/Music'"  This is a bad thing.:(   Any help would be appreciated!

---

