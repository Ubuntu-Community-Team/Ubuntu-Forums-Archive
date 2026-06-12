---
title: "External USB hard drive won't mount on startup"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by jalefkowit on 2007-10-29
I just bought a new PC (woo hoo!) and took the opportunity to do a clean install of Kubuntu Gutsy.

So far, everything seems to work OK except for one thing: my external USB 2.0 hard drive (a 250 GB Western Digital My Book) doesn't mount automatically on startup. It works fine if I mount it manually, but never mounts automatically like it should (and like it did on my old box running Dapper/Edgy/Feisty).

Here's the output of sudo fdisk -l:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa261a261

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34042   273442333+   7  HPFS/NTFS
/dev/sda2           34043       38659    37086052+  83  Linux
/dev/sda3           38660       38913     2040255   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)
```

(The 320GB disk is the internal SATA disk I'm booting from. The 250 GB disk is the My Book.)

Any thoughts?

---

### Post by jalefkowit on 2007-10-30
(bump)

anybody? anybody? Bueller?

---

### Post by jalefkowit on 2007-10-31
One thing I just noticed is that it's not just the external drive that doesn't mount at startup.  When I have a CD in the optical drive on startup, it doesn't mount either.  If I then unplug & re-plug the USB drive, *both* the USB drive and the CD mount. Weird!

---

### Post by taisao on 2007-10-31
this is what I have with my 400GB western digital mybook:

_/etc/fstab_
```
/dev/sdb5 /media/MM_HDII ntfs-3g rw,suid,dev,noexec,auto,nouser,async,locale=en_US.UTF-8 0 0
```

_/etc/rc.local_
```
sudo mount /dev/sdd5
exit 0
```

---

