---
title: "ext2fs issues"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by Finsta on 2007-03-10
I don't know where to post this but this morning, I booted up my Edgy build of Xubuntu and I have 6 partitions between 3 drives. One 40GB holds Windows and Xubuntu/Swap, one 160GB on SATA holds pretty much everything crucial and another on IDE which has yet to be used. The SATA one errors out on startup. On startup it always errors with this...I'm assuming the FS is dead.

fsck.ext2: Unable to resolve 'UUID=40e3c6c8-b0be-4f23-a960-07cf419ce7bb'

Anybody have any ideas on how to fix this, it's much appreciated.

---

### Post by taurus on 2007-03-10
Instead of using UUID in /etc/fstab, I think you should go back to the old way, using /dev/sda1 or whatever the partition is.  Therefore, you need to boot with a LiveCD, mount your /, and edit /etc/fstab.

---

### Post by Finsta on 2007-03-10
> **taurus said:**
> Instead of using UUID in /etc/fstab, I think you should go back to the old way, using /dev/sda1 or whatever the partition is.  Therefore, you need to boot with a LiveCD, mount your /, and edit /etc/fstab.
The SATA 160 isn't the boot device and I did try that. I get an errored output on e2fsck:

e2fsck 1.39 (29-May-2006)
e2fsck: No such file or directory while trying to open /dev/hdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Also, I tried an alternate superblock and it still gave me that output.

---

### Post by taurus on 2007-03-10
Is /dev/hdd1 where / (Ubuntu) resided?

Can you post the output of this command from a terminal and point to which partition is your /?

```
sudo fdisk -l
```

---

### Post by Finsta on 2007-03-10
Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551        4795    18032962+  83  Linux
/dev/hdc3            4796        4865      562275   82  Linux swap / Solaris

Disk /dev/sda: 163.9 GB, 163925425664 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19929   160079661   83  Linux


It isn't. Still, my issue at hand is /dev/hdd1 which doesn't display because it can't mount. I believe it corrupted.

---

### Post by taurus on 2007-03-10
> **Finsta said:**
> Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551        4795    18032962+  83  Linux
/dev/hdc3            4796        4865      562275   82  Linux swap / Solaris

Disk /dev/sda: 163.9 GB, 163925425664 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19929   160079661   83  Linux


It isn't. Still, my issue at hand is /dev/hdd1 which doesn't display because it can't mount. I believe it corrupted.

I don't see any /dev/hdd1!  I think your / partition is on /dev/hdc2 so at the terminal from the LiveCD, do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdc2 /mnt/ubuntu
cat /mnt/ubuntu/etc/fstab
```
Paste the output of the last commnad here.

---

