---
title: "can't find hard drive"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by shanepardue on 2006-02-04
i'm very new to ubuntu and i can't find me 2nd hard drive. i see it in this, but not sure how to access it or if needs partitioned. please help!

/dev/hda1   *           1        9351    75111876   83  Linux
/dev/hda2            9352        9729     3036285    5  Extended
/dev/hda5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24320   195350368+   7  HPFS/NTFS

---

### Post by taurus on 2006-02-04
You need to mount it before you can access it!!!  Try

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hdb1 /mnt/windows

---

### Post by shanepardue on 2006-02-04
sorry for the ignorance! i did what you said and it still isn't showing in the "computer" folder. here's this thing again....that hdb1 is what i need!!

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9351    75111876   83  Linux
/dev/hda2            9352        9729     3036285    5  Extended
/dev/hda5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24320   195350368+   7  HPFS/NTFS

---

### Post by shanepardue on 2006-02-04
also, i went into disks manager and saw that under the partition tab that is disabled and when i click enable it doesnt do anything. it stays disabled. don't know if that helps! any help is greatly appreciated!!!

---

### Post by Greg2 on 2006-02-04
[QUOTE=shanepardue]i'm very new to ubuntu and i can't find me 2nd hard drive. i see it in this, but not sure how to access it or if needs partitioned. please help!
[/QUOTE]
Here’s a very good how-to:
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
It also shows how to edit your fstab so that it mounts automatically at boot-up.

---

### Post by taurus on 2006-02-04
The reason you can't see it because perhaps you don't have the permission to read it!!!  It's an NTFS so I doubt if a user has a permission to view the content of it unless you specify otherwise...

---

### Post by shanepardue on 2006-02-04
thanks greg!! i got it working!! i appreciate all the help i got here!!

---

