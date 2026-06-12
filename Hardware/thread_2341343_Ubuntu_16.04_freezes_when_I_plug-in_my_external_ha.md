---
title: "Ubuntu 16.04 freezes when I plug-in my external hard drive"
date: 2016-10-27
forum: Hardware
---

### Post by simonbesn on 2016-10-27
I just installed ubuntu 16.04 and whenever I plug-in my external hard-drive, my system slows down and even freezes. I was using linux mint before and I did not have such issues with the same external hard-drive. Anyone would know how to fix this mounting issue? 


Here is the ouput of ```
sudo fdisk -l

```



   ```
 Device     Boot     Start       End   Sectors   Size Id Type
    /dev/sda1            2046  29296639  29294594    14G  5 Extended
    /dev/sda2  *     29296640 107421695  78125056  37,3G 83 Linux
    /dev/sda3       107421696 126953471  19531776   9,3G 83 Linux
    /dev/sda4       126953472 976771071 849817600 405,2G 83 Linux
    /dev/sda5            2048  29296639  29294592    14G 82 Linux swap / Solaris
    
    Partition 1 does not start on physical sector boundary.
    Partition table entries are not in disk order.
    
    
    Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x101b4728
    
    Device     Boot Start        End    Sectors   Size Id Type
    /dev/sdb1        2048 1953521663 1953519616 931,5G  7 HPFS/NTFS/exFAT

```

I have tried to plug-in another hard drive and it works well. It has such configuration:


   ```
 Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x6e0a8dca
    
    Device     Boot Start       End   Sectors   Size Id Type
    /dev/sdb1  *       63 976768064 976768002 465,8G  c W95 FAT32 (LBA)

```

---

