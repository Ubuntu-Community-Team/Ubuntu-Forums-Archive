---
title: "Can't mount /dev/sda5 on boot"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2006-01-16
I'm having trouble mounting a FAT32 partition an a SATA drive at boot time. 

Doing "sudo mount /dev/sda5" from the terminal works just fine, but it won't get mounted on boot. When I used Hoary, the boot messages would say something like "/dev/sda5" not available. I recently upgraded to Breezy, and now there is much less info during the boot sequence, so now I don't see that error message, but the error remains.

The last line of my /etc/fstab is 
/dev/sda5 /mnt/artibus vfat defaults 0 2

Is that wrong?

---

### Post by taurus on 2006-01-16
What does "fdisk -l /dev/sda" say anyway?

---

### Post by jazzgossen on 2006-01-16
```
$ fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5233    42034041    7  HPFS/NTFS
/dev/sda2            5234       14596    75208297+   f  W95 Ext'd (LBA)
/dev/sda5            5234       14596    75208266    b  W95 FAT32

```

Does that help?

---

### Post by taurus on 2006-01-16
What does the error message from either "dmesg" or "/var/log/messages" say about your SATA, /dev/sda5, when it tries to mount it at boot?

dmesg | more
-or-
more /var/log/messages

---

