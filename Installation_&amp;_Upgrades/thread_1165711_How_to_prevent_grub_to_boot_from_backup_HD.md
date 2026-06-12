---
title: "How to prevent grub to boot from backup HD"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Mikkee on 2009-05-20
Hello,

I have WinXP (for games only) and Ubuntu 9.04 on the same harddisk. I also have a mirror disk (same size and same brand as the other one) made with clonezilla that i would use as a backup.

Booting with grub is no problem, but if my external USB HD (seagate agentpro) is on, grub seems to boot from the mirror disk. So i am loosing some of the changes made under linux and i'm back on from the day i made the backup on the mirror disk (or is it an old session saved somewhere ?). If the external USB HD is off when booting i got everything back as normal.

Thing to know:

-In the Bios i turned off the boot sequence to USB and also from the secondary HD.
-There is no operating system on the USB-HD


The simple solution i'm looking to try is a grub commands that i could add in the menu.lst that could prevent booting from the mirror disk. Anyone knows?

Thanks

Mike

---

### Post by logos34 on 2009-05-21
When you clone a partition, it is copied EXACTLY--including the UUID.  So you have two / partitions with the same #, and grub is booting the first one it finds.  Change the UUID for the clone partition on the USB:

> sudo tune2fs -U random /dev/sdb1

or whatever the usb is

(if you want to boot the clone don't forget to edit /etc/fstab and /boot/grub/menu.lst so the UUIDs match)

---

### Post by Mikkee on 2009-05-21
Thank you very much for the quick respond.


The mirror is effectively on the sdb but just to make sure and to understand, as this disk is partitioned: winXP is on sdb1 and Linux on sbd2 but the boot sector remain for both OS on the sbd1 so the code...

> sudo tune2fs -U random /dev/sdb1 

...remains good in my situation? And this has to be done after each cloning right?


Thanks again

Mike

The usb Hd is actually the 3rd hd taking place in my system so it may not be a major factor.

---

### Post by logos34 on 2009-05-21
> **Mikkee said:**
> winXP is on sdb1 and **Linux on sbd2** but the boot sector remain for both OS on the sbd1 so the code...

...

The usb Hd is actually the 3rd hd taking place in my system so it may not be a major factor.

in that case, then you want to do 

sudo fdisk -l

(just to make sure the usb with the clone is /dev/sdb.)
> 
sudo tune2fs -U random /dev/sdb**2**

---

### Post by maybeway36 on 2009-05-21
If that doesn't work, the other option would be to change /boot/grub/menu.lst not to use the UUID.

---

### Post by Mikkee on 2009-05-22
> 
[COLOR="Red"][SIZE="5"]Master disk[/SIZE][/COLOR]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
Disk identifier: 0xd6ded6de         

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40544   325669648+   7  HPFS/NTFS
/dev/sda2           40545       60801   162714352+   5  Extended
/dev/sda5           40545       59974   156071443+  83  Linux
/dev/sda6           59975       60801     6642846   82  Linux swap / Solaris

[COLOR="Red"][SIZE="5"]Clone disk[/SIZE][/COLOR]
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
Disk identifier: 0x7281076d                      

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40544   325669648+   7  HPFS/NTFS
/dev/sdb2           40545       60801   162714352+   5  Extended
/dev/sdb5           40545       59974   156071443+  83  Linux
/dev/sdb6           59975       60801     6642846   82  Linux swap / Solaris

[COLOR="Red"][SIZE="5"]USB disk [/SIZE][/COLOR]
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
Disk identifier: 0x000decdf                    

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       22403   179952066    7  HPFS/NTFS
/dev/sdc2           22404       38912   132608542+   f  W95 Ext'd (LBA)
/dev/sdc5           22404       38912   132608511    7  HPFS/NTFS

Note that the USB shouldn't have the clone of any of the above disks, it is used only for downloads and documents backup. But used to have a Ubuntu 8.10 installation previously.

---

### Post by Mikkee on 2009-05-22
> **maybeway36 said:**
> If that doesn't work, the other option would be to change /boot/grub/menu.lst not to use the UUID.


This could be interesting too, as long as i still have the choice of the booting device via the bios and i can change the from master to clone. What do i have to do so the UUID will be ignored ? Just delete it in the menu.lst? Is there any risks?

---

### Post by logos34 on 2009-05-22
> **Mikkee said:**
> This could be interesting too, as long as i still have the choice of the booting device via the bios and i can change the from master to clone. What do i have to do so the UUID will be ignored ? Just delete it in the menu.lst? Is there any risks?

With 3 disks (one usb), I wouldn't use '/dev/sdxy' format (-->boot sequence and recognition of devices/assigning of drive letters)...

---

### Post by Mikkee on 2009-05-22
ok, in my situation, the command work with 

> 
sudo tune2fs -U random /dev/sdb**5**

At this time i can't tell if the will resolve my problem. I just found out after I post my 1st message that the problem didn't come if the USB was on or off, but it was simply sporadic


> 
(if you want to boot the clone don't forget to edit /etc/fstab and /boot/grub/menu.lst so the UUIDs match)


[SIZE="3"]Now, how can i find the new UUID for the clone disk?[/SIZE]

---

