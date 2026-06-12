---
title: "USB hard disk (ext3) not mounted at startup (only if newly plugged in)"
date: 2009-06-04
forum: Hardware
---

### Post by gerryg on 2009-06-04
Hi there,

while my external USB hard disk (ext3) is being mounted automatically when I (newly) plug the USB cable, it won't be mounted during startup. What would I have to do to get it mounted at startup?

An entry in fstab didn't help, probably because the device (sdb1) is not existing. It is created only if the USB cable is newly plugged in, but not at startup. However, lshal always shows the device, but obviously it doesn't get through to gnome-mount (or whoever is doing the mount job). What kind of information would be needed to get on with this question?

Many thanks,
Gerald
(Ubuntu 9.04 on a HP 6735b Laptop)

---

### Post by cherva on 2009-06-04
What about a startup script ?

---

### Post by gerryg on 2009-06-04
cherva,

what would be the content of that startup script?
A mount command wouldn't work because there is no device (like sdb1) to be mounted. Looks like I need to get the device first, but how?

Thx,
Gerald

---

### Post by cherva on 2009-06-05
Hmm lshal shows the device, but it is not in /dev ?
Can you reboot and when you login type in a terminal ```
sudo fdisk -l
``` and then unplug the HDD, plug it again and type the same command. Then paste the results here.

---

### Post by gerryg on 2009-06-05
Here you go...

At start:
```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14563   116977266    7  HPFS/NTFS
/dev/sda2           14564       19457    39311055    5  Extended
/dev/sda5           14564       19250    37648296   83  Linux
/dev/sda6           19251       19457     1662696   82  Linux swap / Solaris
```

And after unplugging and plugging again:
```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14563   116977266    7  HPFS/NTFS
/dev/sda2           14564       19457    39311055    5  Extended
/dev/sda5           14564       19250    37648296   83  Linux
/dev/sda6           19251       19457     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```

Thx,
Gerald

---

### Post by cherva on 2009-06-05
Hmm thats strange .... sry I have no idea how to fix this. Maybe you should file a bug report on launchpad.

---

### Post by eddietours on 2009-06-05
am not sure about this but try usermount from the terminal

---

### Post by gerryg on 2009-06-05
> **eddietours said:**
> am not sure about this but try usermount from the terminal

This seems to be based on /etc/fstab, thus requiring a device (again)...

---

### Post by AC_Soaring on 2009-06-15
My results exactly matched gerryg.  I bought a nice new 1TB USB drive for backups and could not access it.  Found this forum topic and not much success in the posts.  Then I tried plugging into my Vista PC and the drive came up as needing to be formatted.  The format took most of a day, but the drive now works under both OS's.

- Al

---

### Post by gerryg on 2009-06-18
> **AC_Soaring said:**
> Then I tried plugging into my Vista PC and the drive came up as needing to be formatted. The format took most of a day, but the drive now works under both OS's.

So you formatted it as FAT32?

I'd rather like an ext3 filesystem...

There must be some additional information (besides the file system) ensuring the drive is found at startup. Any ideas?

Gerald

---

### Post by gerryg on 2009-06-24
Good news: With the latest updates (kernel 2.6.28-13 and hal 0.5.12~rc1+git20090403-0ubuntu3) the problem has vanished!

Regards,
Gerald

---

