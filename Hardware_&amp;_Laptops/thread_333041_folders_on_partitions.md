---
title: "folders on partitions"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2007-01-06
I have three partitions on my computer and each partitions has the same folders in it.  I know they should be in the main partition hba6 but why are they in the others.  They are just taking up space and I want to know if I can delete them off the other partitions and not kill my computer. 

Below is a screen shot of one of the partitions that I want to delete.  Or should I use gpart and format the two partitions.

---

### Post by jpkotta on 2007-01-06
Before deleting, try just unmounting.  As far as the OS is concerned, it's the same thing, but not permanent.

```
sudo umount /dev/hda3
```

The umount command will not work if anything is using any files in that filesystem.  You can use lsof to find open files.

And to prevent it from mounting at boot time, make sure any lines for /dev/hda3 are commented out in /etc/fstab.  If everything works without that partition mounted, then it's probably OK to format.

---

### Post by ronbrooks on 2007-01-07
OK thanks a lot I was able to unmount the two drives and remount them so I guess it will be safe to delete the folders in the drive.  What I think I will do is burn them to a cd just incase I need them again. 

Thank Your for your help

---

