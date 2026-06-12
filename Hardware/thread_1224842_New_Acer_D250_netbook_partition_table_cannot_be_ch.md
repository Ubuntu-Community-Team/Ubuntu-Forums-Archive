---
title: "New Acer D250 netbook partition table cannot be changed!!"
date: 2009-07-27
forum: Hardware
---

### Post by aaronphughes on 2009-07-27
I have just recently bought an Acer Aspire One D250 netbook. It has an 8.9 inch screen, 160GB HDD and 1GB of RAM (built in webcam, mic, speakers). It looks like this
[http://www.pclaunches.com/entry_images/0509/11/acer_aspire-one-d250.php](http://www.pclaunches.com/entry_images/0509/11/acer_aspire-one-d250.php)

I was very excited to install Ubuntu on there but it seems impossible to change the partition table.

They have it set up as a 7GB recovery partition NTFS, followed by 142GB WinXP NTFS partition. I know this from looking at Windows Disk Manager. Note that XP *does not* have the shrink drive option that Vista has.

So I have tried GParted that comes with Ubuntu 8.10 and it lists the partition table as unallocated 149.05 iB (it does not see anything but one big empty drive)
I have created a bootable USB drive with GParted Live and it says the same thing
I have created a bootable USB drive with Win98 + Partition Magic (PQMagic) and it lists the partition table as error 105, I can't see anything

What's strange is I can mount the drives fine using the bootable USB Ubuntu, I can see the files etc. But when I bring up GParted, it just says unallocated.

I want it to be a dual boot

I'm open to suggestions. Note that the netbook doesn't have any networking yet so it is hard to do apt-get sort of things.

Please help,
Thanks,
Aaron

---

### Post by lrgmmc on 2009-07-27
whats your fdisk say?

---

### Post by aaronphughes on 2009-07-28
**fdisk -lu**
Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000484f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2040254     1020096    6  FAT16

Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8084f2f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         233      999935      499851+   6  FAT16


**sfdisk -d**
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  2040192, Id= 6, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=      233, size=   999703, Id= 6, bootable
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0

---

### Post by aaronphughes on 2009-07-28
I downloaded Ubuntu 9.04 and it is the same. It can *see* the main ACER partition and I can read files off of it, but GParted thinks it is all unallocated??

On the plus side, with 9.04, the network card works so I can use apt-get if needed. 

Any thoughts on why GParted can't do anything with this disk?

---

### Post by aaronphughes on 2009-07-28
I found this CD here [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/) called Hirens Boot CD 9.9
After booting to it through a USB CD rom drive I ran Partition Magic first, which crashed, but then Acronis disk director suite partition saw everything perfectly and allowed me to resize the 160GB drive.

After a reboot and trying Ubuntu again, now GParted saw everything. So I suspect that the partition table had errors (maybe even intentionally from ACER), but once Acronis disk director corrected them, all is well.

Thus I'm installing Ubuntu as I type this to it's own partition *and* it detected the other drive so I suspect GRUB will work fine too.

I hope this helps anyone else who buys this netbook.

---

### Post by chevymanusa on 2009-12-22
aaronphughes,
I am stuck on your method of creating and resizing a new partition. 
I have tired the gparted live cd 4.6.1 and have also tired the method you describe in your last post (using Hirens Boot CD). I am stumped. Everything shows up just fine when you enter the Acronis Disk Director Suite, however as soon as you try to re-size any partition the the ACER labeled partition (main part.) shows the entire drive is full and there is no space. 

Anyone have any ideas or suggestions?
Please if you can respond asap as I am setting this up for someone for Christmas.


Thank you in advance!
-Chevy

---

