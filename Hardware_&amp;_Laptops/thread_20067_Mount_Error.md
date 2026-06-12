---
title: "Mount Error"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by kilishan on 2005-03-15
Hey all, 

I've got a second hard drive, it's pretty old and only 1GB of space, but through WinXP I formatted it to FAT32. In Ubuntu, I've edited my fstab file as follows:

[FONT=Fixedsys]
/dev/hdb1       /mnt/winxp	vfat    umask=000       0       0[/FONT]

when I run mount -a, it gives me the following error:

[FONT=Fixedsys]mount: unknown filesystem type 'vfat'[/FONT]

Any ideas? 
Thanks

---

