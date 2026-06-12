---
title: "Is an external HD &quot;mounted&quot; when it shows on the Dash?"
date: 2014-07-26
forum: Hardware
---

### Post by Gnusboy on 2014-07-26
I have a new Toshiba external 1 Tb HD and want to know if it is connected properly.
I originally had it connected to my TV to copy a bunch of movies from an old Dishnet receiver over to a new one. Everything of the switch worked out fine and the movies were transferred. When I built this desktop I installed a 640 GB drive and divided it into 2 partitions. (I'm not certain of the partition sizes I made)

So now I want to use this drive as a backup disk for my computer. I connected it to the computer and 4 new HD partitions appeared on the dash. All of these show the partitions as different sizes I will call:

Partition 1 = 328 GB file system -  31.4 GB used  /  291.6 GB Free
Partition 2 = 537 GB File system - **33.6 MB used**  /  536.8 GB Free
Partition 3 = 1.1 GB file system - **33.6 MB used  /** 1.0 GB Free
Partition 4 = 462 GB File system - **33.6 MB Used ** /  462.2 Free

 I did not  create these partitions. I believe that the HD were formatted whto en I installed it to the TV, by Dish. But don't know how that would affect partitions of the HD when It was connected to the TV. It just happened without my input. All I did was connect the drive to my computer.
Can I just make a backup with Deja-dup and move it to any of the partitions shown on the dash without a problem restoring the data? 

I tried using Deja-dup a long time ago and it saved the identical backup over and over until the partition was nearly full and I couldn’t restore it.What am I doing wrong?

So if anyone can help me figure this out, I will appreciate it. I want to backup everything so I can upgrade to a newer version of Ubuntu.

---

### Post by bapoumba on 2014-07-28
Cannot help you with Déjà Dup as I'm not using it. For your other questions about the external drive partition, is this a usb drive ? **mount** will tell you what filesystems are currently mounted and **sudo fdisk -l** the different partitions the system sees.

---

### Post by vanadium on 2014-07-28
When the partitions show up in the dash, it indicates they have been recognized. If all is OK with the partitions, they will also be mounted.

ntfs partitions that are not 'clean' (i.e., have not been correctly unmounted previously, e.g because they were disconnected from a Windows system that was put in hibernation rather than fully been shut down) will show up, but will not be mounted. When you click the icon, the system will refuse to mount such partitions. To correct such a situation, the nfts volume must be connected to a Windows system. must preferably be checked using the Windows file system checking tools, and be cleanly unmounted there.

For making backups to transfer the data to a new install, you must reinstall Deja Dup. I do not like that, and I find it much safer to make a direct copy of the data that can be read and opened with any file manager.

---

