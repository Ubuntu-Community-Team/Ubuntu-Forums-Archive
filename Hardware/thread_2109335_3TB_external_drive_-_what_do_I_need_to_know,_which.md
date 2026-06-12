---
title: "3TB external drive - what do I need to know, which one to choose?"
date: 2013-01-27
forum: Hardware
---

### Post by arapaho on 2013-01-27
I want to buy 3TB external drive:

WD My Book Essential 3TB USB 3.0 [WDBACW0030HBK-EESN]
or
Seagate External Desktop Backup Plus 3TB USB 3.0 [STCA3000200]

Which one do you recommend?
What do I need to know about formating? Do I need to make partitions? Is Ubuntu able to handle 3TB?

I will use it for storing large video files from video camera and tons of pictures.

Is there a chance that the price will go down sometime this year?

---

### Post by oldfred on 2013-01-27
Do not know if one is better than the other.

With a drive over 2TB you have to use gpt partitioning not the old MBR as it cannot partition drives over 2TB. You do have to partition drive and with that large of a drive, you may not want one extremely large partition but for videos it may be ok as one. 
If working with Windows it needs to be NTFS, otherwise use a Linux format. Ext4 is most common but for some special cases another format may have some advantages. Some have had issues with one large NTFS partition when formatted from Windows. I would use gdisk or gparted.

If you need drive price should not be a concern. Generally prices do go down, but then we had the flood in Thailand a few years ago, that created shortages of drives and prices went way up.

       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

    
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
       gpt(GUID) is required for drives over 2TB, suggested for SSDs, and required for UEFI booting. Ubuntu will work with gpt partitioned drive with either BIOS or UEFI.
    
When you have a drive that large, I might consider having a small install of Ubuntu on the drive. I do not particularly recommend Knoppix as I prefer and know Ubuntu better, but agree with the logic of having an install on every large drive. Using 25GB for Ubuntu on a 3TB drive hardly uses any space.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by arapaho on 2013-01-28
> **oldfred said:**
> With a drive over 2TB you have to use gpt partitioning not the old MBR as it cannot partition drives over 2TB. 
I didn't know that external drives has to have gpt. Does every drive has gpt or MBR? Even pendrives have MBR?

This external drive was meant to be used for storage purpose only, not for running operating system.
> **oldfred said:**
> but agree with the logic of having an install on every large drive. Using 25GB for Ubuntu on a 3TB drive hardly uses any space.
Can you explain what is the logic behind install of operating system on every large drive, considering that I will conect to it only by USB port to store data?

Maybe there might be some issues with useage of storage disks that I am not aware of. If this is the case can you elaborate more on this, please?

---

### Post by oldfred on 2013-01-28
It is the size of the drive that determines whether you can use the old MBR or the new gpt(GUID). IF drive is over 2TB you cannot use MBR(msdos) unless you want drive to be only 2TB. 
You also have to use gpt with the new UEFI which is replacing BIOS and gpt is suggested for SSDs.
I have used gpt on a 16GB flash drive with a full install of Ubuntu just to see if it would work and it does. But since I boot with BIOS I have to add the bios_grub unformated 1MB partition.

LInk above on Knoppix has the reasons for an operating system on every drive. Many install Ubuntu to external drives as they do not want to change internal drive. I have Ubuntu full installs on several flash drives.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

One or two users have just written data to external drives without partitioning and had huge issues. I guess it can be done, but then is like a old floppy drive which had no partitions. But most systems and system tools expect partitions and you have huge issues if drive is not partitioned.

---

