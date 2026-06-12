---
title: "Deleted Windows Partition and Now Grub Does not Load"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by teknodude on 2008-12-12
I have a dual boot with ubuntu 8.04 and windows xp. I had some problems with windows xp, so I decided to start over (reinstall it).

I booted from the windows xp install cd and it showed 4 partitions . I deleted the partition labeled C, because this is where I had windows xp installed. However when I tried to install xp in the unpartitioned space, it gave me an error saying that I already have the max amount of partitions on my drive. I did notice that when I deleted partition C, the other three partitions had their drive letters changed. 

Now when I start up my computer, the dual boot screen does not show up. It just says no bootable drive.

---

### Post by Pumalite on 2008-12-12
Boot your Live CD and post:

```
sudo fdisk -lu
```

---

### Post by teknodude on 2008-12-12
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20da20da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        86477895    90381689     1951897+  82  Linux swap / Solaris
/dev/sda2        90381690    90767249      192780   83  Linux
/dev/sda3        90767250   117210239    13221495   83  Linux
ubuntu@ubuntu:~$ 

```

this is what shows up when i run the command sudo fdisk -lu

---

### Post by caljohnsmith on 2008-12-12
Have you tried using Ubuntu's partition editor gparted to make an NTFS partition for Windows to install to? I would try that. If you boot your Live CD, just go to System > Admin > Partition Editor. Also, make sure you create a primary NTFS partition for Windows and not a logical one. How about giving that a shot and let us know how it goes.

---

### Post by teknodude on 2008-12-13
Thanks for the help. Using the partition editor fixed the problem with installing windows xp again. All I have to do now is fix the boot menu problem. I think I just need to get GRUB back on the master boot record again.

---

### Post by Partyboi2 on 2008-12-13
You can boot a ubuntu live cd and restore grub. See [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

