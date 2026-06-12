---
title: "Dual-boot with Windows 7: Where to partition?"
date: 2010-05-09
forum: Hardware
---

### Post by DigiTan on 2010-05-09
Hey there everybody.  I recently got an Asus netbook pre-loaded with Windows 7.  I'm looking to partition in Eeebuntu or Ubuntu NBR.  The weird thing is there's three Win7 partitions and the one I need to shrink is at the beginning of the disk instead of the end.

I can shrink the first partition down enough to fit Ubuntu in, but will that cause any problems?  Is there any danger in adding a 4th partition to the middle of drive instead of the end?

---

### Post by dino99 on 2010-05-10
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

warning: this forum is fullfiled with users complaints about w7 resizing partitions, w7 will not boot then .

what you can do: with w7, resize sda1 only, then follow the link above, dont modify the other partitions.

---

### Post by wilee-nilee on 2010-05-10
The problems are not with resizing W7 if you use the disk manager in W7, defragg first, then install the dual boot without putting grub in every partition or any partition.

Thread starter you will just have to let the W7 partition manager to shrink, and then do a restart of W7 to make sure it's working. Leave a open space for Linux or build the partitions for a custom install, just make sure when you install that grub only goes into sda the mbr of the HD.

If it were me I would get a install disc from the manufacturer and remove the recovery partition, just make sure you know the oem key for a reinstall. This will remove the recovery, and the extra stuff that will generally make the computer run slower or at a higher amount of cpu and memory usage.

---

### Post by DigiTan on 2010-05-10
Okay, I'll just take a stab at shrinking the partition within Disk Manager first.  I'm pretty sure this Win7 will reject the partition table if I change the boot partition, so I'll avoid doing that.  So grub can definitely go on the partition that windows is on?

```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31990983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29094   233690112    7  HPFS/NTFS
/dev/sda2           29094       30399    10485760   1b  Hidden W95 FAT32
/dev/sda3           30399       30401       19136+  ef  EFI (FAT-12/16/32)
```

---

### Post by wilee-nilee on 2010-05-10
> **DigiTan said:**
> Okay, I'll just take a stab at shrinking the partition within Disk Manager first.  I'm pretty sure this Win7 will reject the partition table if I change the boot partition, so I'll avoid doing that.  So grub can definitely go on the partition that windows is on?

```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31990983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29094   233690112    7  HPFS/NTFS
/dev/sda2           29094       30399    10485760   1b  Hidden W95 FAT32
/dev/sda3           30399       30401       19136+  ef  EFI (FAT-12/16/32)
```

Grub should not go on any partition it goes to the hard drive master boot record sda. I think you may be confused with what a partition is, it is any thing with a nuber past the HD=sda partition=sda1 or any other numbers. Leave a open space for the Ubuntu install and choose install to open space in the install partitions and check the final install gui click advanced and make sure it is set to sda no numbers following sda.

---

### Post by DigiTan on 2010-05-10
Is it still necessary to make slash, home, and swap in Ubuntu NBR beforehand or will I get those options in the installion GUI?

---

### Post by wilee-nilee on 2010-05-10
> **DigiTan said:**
> Is it still necessary to make slash, home, and swap in Ubuntu NBR beforehand or will I get those options in the installion GUI?

If you leave a unallocated space and use the install in the free space all this will be done automatically. I would not use the UNR I have seen problems with it use at your own risk and make sure it actually runs before installing, Now just because it works before installing doesn't mean it will once installed. I have tried many versions of the UNR and had problems with everyone of them, when my computers will run anything else with very little if any problems. Now you need to have a backup of your W7 or a install DVD just in case of problems and/or a backup of anything you can't afford to lose.

---

### Post by DigiTan on 2010-05-10
Yeah, I'm just trialing this distro for now.  There's plenty of other .iso's on deck for if something doesn't work out.
--------

Both Ubuntu NBR and Windows 7 seem to be running smoothly so far.  I gave the Ubuntu partition a generous amount of space compared to last time.  If this it turns out to be **too** generous, is there a good procedure for shrinking the Ubuntu partition?

---

### Post by wilee-nilee on 2010-05-10
> **DigiTan said:**
> Yeah, I'm just trialing this distro for now.  There's plenty of other .iso's on deck for if something doesn't work out.
--------

Both Ubuntu NBR and Windows 7 seem to be running smoothly so far.  I gave the Ubuntu partition a generous amount of space compared to last time.  If this it turns out to be **too** generous, is there a good procedure for shrinking the Ubuntu partition?

You were smart to ask pertinent questions ahead of time, especially about grub, and knowing about the W7 disk manager tool, glad everything is up and running. ;) If more people would do a little research then things would generally go okay for them.

---

### Post by DigiTan on 2010-05-12
Yeah, I figure there were bound to be some common roadblocks to watch out for.  But Ubuntu NBR seems to be going extremely well for a first try.  I guess the only thing I'm missing is a way for Win 7 to read my ext4 stuff.  I'm wondering if it's too late for a shared partition or maybe I could find some kind of Windows driver to help with that.

---

