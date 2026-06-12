---
title: "The best way to divide my laptop hdisk?"
date: 2010-12-01
forum: Hardware
---

### Post by fedemw on 2010-12-01
Hello,

I just have received a brand new laptop with 250 GB hard disk. I will delete the W7 and install Mint 10 after my great experience past year with Isadora 9.

Would you please recommend me how to partition my disk in the best way to:

- Boot from Linux or Windows 7
- Have a shared partition between both systems.

Please specify how to decide between expanded or native and where to fit in / , /home and /swap

Thanks!!!:popcorn:

---

### Post by swap_1712 on 2010-12-01
Based on my experience, I will recommend you to use this:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
so you can have a dual boot computer and you won't have to do anything for yourself.

---

### Post by fedemw on 2010-12-01
> **swap_1712 said:**
> Based on my experience, I will recommend you to use this:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
so you can have a dual boot computer and you won't have to do anything for yourself.

THanks but I would like to use a native Linux installation as W7 is only for some specific programs from my work.

 Best,

---

### Post by oldfred on 2010-12-01
So are you uninstalling win7 or dual booting. It makes a difference.:)

Often new computers with Windows use all 4 primary partitions, so you have to decide what to delete. I would use the vendor recovery partition to make a complete recovery DVDs and if offered a repair CD.
You may want to houseclean the cruft that is often installed an just make a back up of the windows partition.
One of many choices
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

You may want to backup the vendor utilities partition. You can reinstall in a logical partition if you want.

Then you can delete either the vendor recover or utilities partition, shrink windows with windows MMC,  and create with gparted an extended partition with logical partitions for Ubuntu. Do not attemp to use windows to create additional partitions as it will convert from basic to SFS (logical volumes) that are compatible with nothing.

If you have room make a shared NTFS partition for any data you want between systems. Windows will read data from a NTFS partition that is a logical partition.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

If you do not have a primary for / just use logical. Linux works just fine from logical partitions.

---

### Post by fedemw on 2010-12-01
> **oldfred said:**
> So are you uninstalling win7 or dual booting. It makes a difference.:)

Often new computers with Windows use all 4 primary partitions, so you have to decide what to delete. I would use the vendor recovery partition to make a complete recovery DVDs and if offered a repair CD.
You may want to houseclean the cruft that is often installed an just make a back up of the windows partition.
One of many choices
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

You may want to backup the vendor utilities partition. You can reinstall in a logical partition if you want.

Then you can delete either the vendor recover or utilities partition, shrink windows with windows MMC,  and create with gparted an extended partition with logical partitions for Ubuntu. Do not attemp to use windows to create additional partitions as it will convert from basic to SFS (logical volumes) that are compatible with nothing.

If you have room make a shared NTFS partition for any data you want between systems. Windows will read data from a NTFS partition that is a logical partition.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

If you do not have a primary for / just use logical. Linux works just fine from logical partitions.

Thanks. I do not care about W7 installed from HP; will delete and reinstall later with other version. 

So my disk will be:

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical
4. Windows 7 new version - GB - primary

Makes sense?

Where to put the primary/logical partition for data exchange between Linux & Windows 7?

Thanks mate!

---

### Post by oldfred on 2010-12-01
The NTFS data /shared partition can be primary or logical. Windows reads data from logical, but requires a primary partition for booting. You may want to just reserve the first primary as the windows NTFS with the boot flag. Then create the rest of the partitions.

You have to decide how much space for NTFS data vs. /home for Linux data that you do not need/want to share.

If you install windows second understand that you have to reinstall grub2 with a liveCD.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

