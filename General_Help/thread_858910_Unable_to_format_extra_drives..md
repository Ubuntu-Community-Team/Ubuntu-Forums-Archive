---
title: "Unable to format extra drives."
date: 2008-07-14
forum: General Help
---

### Post by blackjackjester on 2008-07-14
Hello everyone,

I recently had 4 500GB drives in a RAID5 on a personal file server.  I decided to reinstall some stuff, and change some things, so I ended up moving from Fedora over to Ubuntu.

Now, when I try to format any of the drives that were previously in the RAID, i get a "The device apparently does not exist; did you specify it correctly?" error for all of the drives.

I initially used mdadm, which showed the drives in use by the array md0.  I then turned off the array, hoping the drives would be free from their no-formatting bondage.  No luck.

I read a suggestion to fdisk -dd on the drives, but fdisk doesn't seem to have that option?  At this point, I'm pretty stuck.  Next step for me is to Boot and Nuke every drive, then go from there, unless anyone has any other ideas =P.

The goal is to be able to format the drives ext3 independently.

---

### Post by justleen on 2008-07-14
can you post the output of "sudo fdisk -l" so we can see what the drive look like?

---

### Post by blackjackjester on 2008-07-14
/dev/sda is the boot drive, and the other four were in the RAID.


phoenix@adele:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9928

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9354    75135973+  83  Linux
/dev/sda2            9355        9729     3012187+   5  Extended
/dev/sda5            9355        9729     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005c002

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000737d7

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00089def

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6a3a

   Device Boot      Start         End      Blocks   Id  System
phoenix@adele:~$

---

### Post by blackjackjester on 2008-07-15
Shameless bump.  Anyone have any ideas?

---

### Post by fjgaude on 2008-07-16
I think you need to wipe the drives with something like:

```
sudo dd if=/dev/urandom of=/dev/sd[n]
```

Can't remember the command for sure. What the issue is is that filesystem can't write over the mdadm area what declares the drive an auto Linux raid device, something like that.

There needs to be a book covering all the issues that come up with mdadm raid.

---

