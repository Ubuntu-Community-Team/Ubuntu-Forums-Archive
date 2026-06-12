---
title: "The whole disk unallocated?"
date: 2012-04-29
forum: Hardware
---

### Post by khaos1 on 2012-04-29
Hi guys. I have a netbook with: ubuntu, windows7 and 2 other linux distros installed on them. All are in the /dev/sda hard disk in partitions. After a broken partition table, I run testdisk to fix the table in order to fix the grub  entries and all worked great. But when I used the ubuntu 12.04LTS installer to install it in one partition the installer can't find the partitions. It shows only the /dev/sda unallocated. The same thing appeared when I'm trying to run gparted. So I run gparted from terminal and the error is:

> khaos1@netbook:~$ sudo gparted
======================
libparted : 2.3
======================
Can't have a partition outside the disk!

In the GUI it shows the /dev/sda disk that is unallocated without any partitions. 

The grub is working ok and all the distros (windows,linux) are booting ok. 

My fdisk -l output:

> [http://pastebin.com/unDvV9mw](http://pastebin.com/unDvV9mw)

Any help on how to fix that? because I don't want to format the drive now
Is anything wrong about the boot partition?
Thanks in advance

---

### Post by coffeecat on 2012-04-29
> Can't have a partition outside the disk! 

What's almost certainly happened is that although testdisk repaired your partition table, it created a partition table illegality, and this is why gparted is showing the whole drive as unallocated. Two bugs which conspire to create a problem which is often seen.

Your fdisk output looks as though it was from a pre-11.10 version of Ubuntu, because "fdisk -l" has given output in cylinders, which is usually unhelpful. This time though, it does seem to have identified the problem: extended partition ending at 30402 cylinders with a disc of only 30401 cylinders.

That being said, measuring in cylinders is obsolete and can be misleading. I suggest you run "sudo fdisk -lu" which in any version of Ubuntu will give you output in sectors. Compare the end sector of sda4, your extended partition, and the end sector of the drive. If sda4 appears to be beyond the physical end of the drive, then the problem is definitely identified. Post the output if you need help with this.

If that is the problem, it is easily fixed with the fixparts utility. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Make sure you download fixparts and not gdisk. Some people have accidentally downloaded gdisk and converted their mbr partition tables into GPTs - frying pan into fire - hence Rod's warning on that page.

---

### Post by khaos1 on 2012-04-29
> **coffeecat said:**
> What's almost certainly happened is that although testdisk repaired your partition table, it created a partition table illegality, and this is why gparted is showing the whole drive as unallocated. Two bugs which conspire to create a problem which is often seen.

Your fdisk output looks as though it was from a pre-11.10 version of Ubuntu, because "fdisk -l" has given output in cylinders, which is usually unhelpful. This time though, it does seem to have identified the problem: extended partition ending at 30402 cylinders with a disc of only 30401 cylinders.

That being said, measuring in cylinders is obsolete and can be misleading. I suggest you run "sudo fdisk -lu" which in any version of Ubuntu will give you output in sectors. Compare the end sector of sda4, your extended partition, and the end sector of the drive. If sda4 appears to be beyond the physical end of the drive, then the problem is definitely identified. Post the output if you need help with this.

If that is the problem, it is easily fixed with the fixparts utility. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Make sure you download fixparts and not gdisk. Some people have accidentally downloaded gdisk and converted their mbr partition tables into GPTs - frying pan into fire - hence Rod's warning on that page.

Thanks for your reply! First of all my fdisk -lu output:

[http://pastebin.com/cqyaA5wS](http://pastebin.com/cqyaA5wS)

My ubuntu version is 10.10 and I want to keep it for offline use and to install 12.04 in the /dev/sda10 with swap: /dev/sda11

With this output the fixparts will help? Thanks in advance!!

---

### Post by coffeecat on 2012-04-29
> **khaos1 said:**
> With this output the fixparts will help? Thanks in advance!!

Yes, fixparts will help.

I'll repost your fdisk -lu output. It's easier to refer to it that way.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR="Red"]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c18ab71
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    27265023    13631488    7  HPFS/NTFS
/dev/sda2        27265024    35653631     4194304    c  W95 FAT32 (LBA)
/dev/sda3        35653632    35858431      102400    7  HPFS/NTFS
/dev/sda4        35858466   [COLOR="Red"]488408129[/COLOR]   226274832    f  W95 Ext'd (LBA)
/dev/sda5        35860480   167671392    65905456+   7  HPFS/NTFS
/dev/sda6       167671808   212711423    22519808   83  Linux
/dev/sda7       212713472   214757359     1021944   82  Linux swap / Solaris
/dev/sda8       214767616   392495103    88863744   83  Linux
/dev/sda9       392497152   410075119     8788984   82  Linux swap / Solaris
/dev/sda10      410081280   485089279    37504000   83  Linux
/dev/sda11      485091328   [COLOR="Red"]488396783[/COLOR]     1652728   82  Linux swap / Solaris
```

I've highlighted the relevant data in red. Your partition table is trying to tell us that the last sector of sda4, your extended partition, is beyond the last sector of the drive, which is of course impossible. However, the last sector of sda11, the last logical partition, is within the drive boundary. If you recall the cylinder output, it misled us with the latter.

The fixparts tutorial in the link I posted is quite clear and fixparts usually fixes this particular problem in moments. Don't forget to make a backup of your current partition table with the sfdisk command as shown. Keep a copy on a separate medium in the extremely unlikely event of something unexpected happening.

Good luck!

---

### Post by khaos1 on 2012-04-29
Thanks for the reply and for your time. Really apreciate this :)
I have understood the mistake :) 

So, I will try the fixparts. In order not to destroy the laptop I will type here the commands and If you can check them in order not to have damage:

1) boot in my ubuntu 10.10 and downloading the x86 deb package. Instalation.

# sfdisk -d /dev/sda > parts.txt
and copy this file to an external disk

after:

fixparts /dev/sda
type:
p and w for write?

Are that commands correct? 
Can I type them in my ubuntu or I must type them in a live usb stick ubuntu distro?

Thanks in advance

---

### Post by coffeecat on 2012-04-29
Those fixparts commands look OK, but use the '?' at the fixparts prompt to see all the commands available, and double-check against the tutorial. You'll probably find that it's clearer what's happening when you are actually running fixparts.

You can install fixparts to your current 10.10 system or to a live USB session - it doesn't matter. If the live USB doesn't have persistence, fixparts will be installed to RAM and will be lost when you power down, but that doesn't matter much since it is a tiny download and easily re-installed if you need to.

---

### Post by khaos1 on 2012-04-29
> **coffeecat said:**
> Those fixparts commands look OK, but use the '?' at the fixparts prompt to see all the commands available, and double-check against the tutorial. You'll probably find that it's clearer what's happening when you are actually running fixparts.

You can install fixparts to your current 10.10 system or to a live USB session - it doesn't matter. If the live USB doesn't have persistence, fixparts will be installed to RAM and will be lost when you power down, but that doesn't matter much since it is a tiny download and easily re-installed if you need to.

This worked great. Confirmed by rebooting my system and running gparted. All partitions are there. Now I will procceed to the ubuntu 12.04 installation in /dev/sda10 and 11 for swap. I will install grub in /dev/sda and I hope that will recognise the other linux and the windows distro.

Thanks!!

---

### Post by coffeecat on 2012-04-29
Good luck! :)

---

### Post by khaos1 on 2012-04-29
> **coffeecat said:**
> Good luck! :)

Thanks for the help. The installation was ok :) Thanks again

---

