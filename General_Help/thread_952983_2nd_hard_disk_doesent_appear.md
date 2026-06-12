---
title: "2nd hard disk doesent appear"
date: 2008-10-19
forum: General Help
---

### Post by Lazzz on 2008-10-19
Hi i installed ubuntu 8.04 hardy heron yesterday on my D drive and when i get on ubuntu the D drive doesent appear any help?

---

### Post by sea_monkey987 on 2008-10-19
the partition you install ubuntu on does not appear under the Computer in ubuntu.  the partition is mounted at '/.'  So just click on filesystem.  that is everything on your "D drive."

---

### Post by Sam on 2008-10-19
Taken from [this page](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/):
> In the Linux file system everything is considered a file–even devices, drives and removable media. It definitely is a bit different than what you might be used to in the Windows world, but after a quick rundown (below) hopefully the organization will make some more sense.

The base (or equivalent of C:\) is called the root folder or “/”. The closest equivalent of “Documents and Settings\User” would be “/home”. The “/home” folder stores each users files, settings, pictures, etc. Most of what you do is held within the /home folder.

---

### Post by Lazzz on 2008-10-19
ok the thing is that i have 2 OS  and i installed ubuntu on my d drive where i have all my games so i wanted to play a game and i could only find my c drive where my vista is installed on
so i checked the file system and i only found the ubuntu files
and when i go onto vista my games+ubuntu folder appears any help?

---

### Post by Sam on 2008-10-19
Did you install Ubuntu using the "wubi" method ?

---

### Post by Lazzz on 2008-10-19
> **Sam said:**
> Did you install Ubuntu using the "wubi" method ?

yeah but instead of downloading from wubi i downloaded from the ubuntu page

---

### Post by Sam on 2008-10-19
What is the ouput of```
sudo fdisk -l
``` ?

---

### Post by Lazzz on 2008-10-19
> **Sam said:**
> What is the ouput of```
sudo fdisk -l
``` ?
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddf36353

   Device Boot      Start          End         Blocks   Id  System
/dev/sda1               1         1274        10233373+  27  Unknown
/dev/sda2   *        1275        15855        117121882+   6  FAT16
/dev/sda3           15856        30401        116840745    7  HPFS/NTFS
david@david-desktop:~$
there

---

### Post by Sam on 2008-10-19
Hum maybe I'm wrong, but I'm not sure you can access the windows host partition with a wubi-installed Ubuntu.

---

### Post by oldos2er on 2008-10-19
> **Lazzz said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddf36353

   Device Boot      Start          End         Blocks   Id  System
/dev/sda1               1         1274        10233373+  27  Unknown
/dev/sda2   *        1275        15855        117121882+   6  FAT16
/dev/sda3           15856        30401        116840745    7  HPFS/NTFS
david@david-desktop:~$
there

 This shows you only have one hard disk.

---

### Post by Ankhwatcher on 2008-10-19
@oldos2er It probably looked like two hard drives from windows. You know how computer sellers are: partition partition partition...

---

