---
title: "Need Assistance ASAP: External Hard Drive Not Found."
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by RJ Fighter on 2007-11-23
Basically put, ever since I upgraded from Feisty to Gutsy, I have not been able to find my external hard drive nor mount it.  Every time I try to mount it, it says:

```
mount: /dev/sdb1 already mounted or /media/sdb1 busy
```

When I know it hasn't been mounted at all.  I check to see anyway using the umount code, and it says that it was never mounted in the first place.  I also have tried using pmount, which doesn't work either.  My fdisk -l shows that the hard drive is indeed there.  It's formatted as fat32.

```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7275d231

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)
```

I seriously need help.  ALL of my personal files are stored on here from when I migrated from Windows over to Ubuntu a few days ago.  All of the files are intact.  Previously, in Feisty, it would not recognize the HDD either, but then I could pmount it and it would be fine, but now, I can't do anything.

EDIT:

Here's what I try to do:

```
sudo mount -t vfat /dev/sdb1 /media/sdb1
mount: /dev/sdb1 already mounted or /media/sdb1 busy
umount dev/sdb1
umount: dev/sdb1 is not mounted (according to mtab)
```

EDIT:

Never mind, I just needed to switch to a different USB port and mounting it worked fine after that.

---

