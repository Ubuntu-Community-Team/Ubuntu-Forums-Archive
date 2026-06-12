---
title: "How to remove Windows after successful WUBI install?"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by rwrouns on 2009-01-29
I was unable to get a live disk to operate on an old VAIO laptop which uses a pcmcia cd drive but was able to successfully install 8.10 "within windows" by using WUBI.  Is there any way I can eliminate Windows and have Ubuntu running on a ext3 partition just as though I had installed it directly from a live disk?  I have 20 gb of unallocated space on my hd.  Windows and Ubuntu are currently running on a 20 gb partition and I have no user data I need to preserve.  My reason for doing this is that it seems that the system is slower to boot and slower to run than other installations I have done where the live disk successfully loaded and Ubuntu was then installed as the only os.

---

### Post by avtolle on 2009-01-29
Since you have installed through Wubi, you will need to either: move your Wubi install to a dedicated partition using LVPM (see sticky in Wubi sub-forum) or do a fresh install on the unallocated partition in the traditional manner (although instead of using the Live CD, you might want to try the alternate install iso burned to CD). If you just "eliminate Windows", your Wubi install of Ubuntu will also be deleted.

---

### Post by rwrouns on 2009-01-29
Thanks.  It seems that LVPM is exactly what I was looking for.

---

### Post by rwrouns on 2009-01-30
I ran LVPM which installed Ubuntu in a new ext3 partition, but choosing it from the boot manager resulted in Error 17, Cannot mount selected partition.  How do I fix that?

---

### Post by avtolle on 2009-01-30
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17) may have some good information for you. From scanning it, I've a question; when you used LVPM to move the install to its own partition, did you format the partition as ext3?

---

### Post by avtolle on 2009-01-30
Also, looking at the LPVM sticky, it does not indicate that a Wubi install of 8.10 is supported by the script; did you use the alternate method? Just trying to figure out why you got the Error 17.

---

### Post by avtolle on 2009-01-30
One last thing; I think you will need to edit /boot/grub/menu.lst to indicate where the new ubuntu partition is. This is where any "expertise" I may have ends. ```
sudo fdisk -lu
```run from the terminal should give you a list of the partitions on the HDD. Run this, and post the results.

---

