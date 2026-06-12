---
title: "Vista can't read NTFS-3g drives"
date: 2009-01-28
forum: Hardware
---

### Post by gzenitsky on 2009-01-28
I have two external USB drives attached to my Ubuntu 8.10 workstation that are both formatted NTFS-3G using Partition Editor. I need to transfer the data (mostly digital images) to a Vista Home Premium x_64 workstation. When I attach the drives to the Vista box, Vista cannot mount the drives. I see the drives in Device Manager and Disk Manager shows a Drive 1 and 2 but no partitions nor can I apply any action to the drives. I couldn't format them in Vista using Disk Manager even if I wanted to. I've searched NTFS-3g forums and have Googled this issue to death with no workable solutions. Has anyone experienced this issue or does anyone know of any solution? The NTFS-3g web site claims Vista compatibility so it could be some obscure issue with the drives or the Partition Editors format. Any help is greatly appreciated. By the way, I transfered data off one drive to the second external and formatted the empty drive in FAT32 and Vista could not see that drive as well. Thanks for your responses.

---

### Post by balaknair on 2009-01-29
Could the drives be encrypted/locked? Since you can't apply any action to them and Vista can't format them either.
Have you tried accessing them from a different computer?

That said, I can't access new ext partitions created with Ibex on WinXP SP3 either(I can access all partitions created by Gutsy- NTFS and ext using fs-driver for Windows). So maybe it's a regression in GParted in Ibex?

If retrieving the data is your sole concern, try using a CD/DVD, or delete the partition on the empty ExtHDD and see if Vista detects it as a raw partition and can format it.

---

### Post by gzenitsky on 2009-01-29
Thanks for your response. The drives are not encrypted or locked but I find it interesting you can't access using XP with the fs-driver because that was going to be one of my next experiments. I considered offloading the data to dual-layer DVD but I need an application that will manage multiple DVDs. I have approximately 85gb of memory which will require every bit of 13 or more DL DVDs. I will try your suggestion about connecting an empty drive to the Vista workstation. Thanks again for your input!

---

### Post by balaknair on 2009-01-31
> **gzenitsky said:**
> Thanks for your response. The drives are not encrypted or locked but I find it interesting you can't access using XP with the fs-driver because that was going to be one of my next experiments. I considered offloading the data to dual-layer DVD but I need an application that will manage multiple DVDs. I have approximately 85gb of memory which will require every bit of 13 or more DL DVDs. I will try your suggestion about connecting an empty drive to the Vista workstation. Thanks again for your input!

I'd really like to know how it goes.
Wishing you luck.

---

### Post by Yashiro on 2009-01-31
> that said, I can't access new ext partitions created with Ibex on WinXP SP3 either(I can access all partitions created by Gutsy- NTFS and ext using fs-driver for Windows). So maybe it's a regression in GParted in Ibex?Because in later versions of Ubuntu the default inode size is incompatible with the Windows driver. If you force inodes of 128 or less then it will work.

---

### Post by balaknair on 2009-01-31
> **Yashiro said:**
> Because in later versions of Ubuntu the default inode size is incompatible with the Windows driver. If you force inodes of 128 or less then it will work.

Thanks Yashiro. I knew Intrepid uses 256 byte inodes on ext3 by default, and know of the GRUB errors this caused with older versions of GRUB. I just didn't make the connection with ext2fs.sys not reading my Intrepid partitions. :D

Since inode size cannot be changed once the filesystem has been created, it would mean a reinstall of Intrepid. And since I now use XP on my desktop only to play games(Call of Duty 1 and 2 and Lord of the Rings: Battle for Middle Earth) and little else, I'm content to let it be.

---

### Post by gzenitsky on 2009-02-02
I'm not sure what I did to rectify this situation will lend any insight to the original problem. I was fortunate to have mirrored data on two different external drives so I took a chance on one of the drives and used gparted to format it to FAT32. I had previously tried this and it did not work on my Vista Home Premium x_64 workstation, but I gave it another try and sure enough Vista could not mount the drive. It appeared in device manager as I would expect but Disk Management could do nothing with the drive. I unattached the drive from the Vista box and attached it to my Mac running OS X 10.5.6. The iMac mounted the drive and I used Disk Utility to format it FAT32. This time when I reattached the drive to the Vista box, it mounted and I was able to re-format it to NTFS using Vista's Disk Management.

---

### Post by balaknair on 2009-02-02
Glad to know you got it working.

---

### Post by sandy8925 on 2009-04-07
Could be that Gparted didn't format it properly for some unkown reason. I've never had any such problems when using Ibex.

---

