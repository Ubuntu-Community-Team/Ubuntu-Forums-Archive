---
title: "mounting other partitions"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by stevetxt on 2005-01-24
I installed Ubuntu on my laptop yesterday, following all the defaults except that I deleted an old partition and combined that with the rest of the free space for Ubuntu.  The installation successfully recognized my partitions for Windows XP and Debian 3.0, and put them in the Grub menu.  

Now I want to be able to occasionally access those other drives, to bring some files over.  Should I put them in my fstab file, or is there a way to mount them by hand on an occasional basis?  What is the easiest way here?

Also, will I be able to read from or write to the XP partition, which has the ntfs file system, from Ubuntu?  (If not, I have another partition in FAT which I have used in the past for transfers.

Thanks.

Steve

---

### Post by shmonkey on 2005-01-25
Well I would add them to the fstab - then they will show up in nautilus.
As far as ntfs I think you will only have read access to this.

---

### Post by stevetxt on 2005-01-25
OK, thanks, Shmonkey.  I'll do that.

Steve

---

