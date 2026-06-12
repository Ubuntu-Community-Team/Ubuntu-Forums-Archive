---
title: "Partition 1 does not end on cylinder boundary."
date: 2009-02-15
forum: Hardware
---

### Post by HunkirDowne on 2009-02-15
Hello,

I have a new laptop that I am configuring for the kids' school use so Vista must remain.  But the laptop did not come with a rescue disk or installation media so I'm doing my own backup with a combination of partimage and dd.

My question is about my fdisk report that states: "Partition 1 does not end on cylinder boundary."  What/why/how?  Does this mean that my partimage of sda1 is no good?  What about my partimage of sda2 which starts on the same cylinder as sda1 ends on?

'fdisk -l':
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb10bcfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       30402   242660536    7  HPFS/NTFS


Id 27 is not listed in fdisk's list of known partition types (hence, probably, the "Unknown" in 'System' above.

Any ideas or caveats?

This is, by the way, on a Toshiba Satellite L355D-S7825 with Vista Home Premium installed.  VHP does not have full disk backup capabilities and I really didn't want to download a windows program when I can do it in Linux.  I've been bit by Norton Ghost in the past and am not going back for personal use -- work use only but that's their decision, not mine.  ;-)

My plan going forward is to repartition the hdd so that sda2 is smaller and will accommodate the space necessary for sda3 (primary) and sda4 (extended).  I will clone sda2 to sda3 using my partimage of sda2 and use sda4 for NTFS, FAT32, and several ext3 partitions.  sda5 will become a documents repository labeled 'D:' in Vista (pronounced VEEEEStah) which will be NTFS and large enough for a few DVD iso images.  FAT32 will be there for public transfer and labeled 'E:' and probably not much more than 4 GB.  The rest will be split into partitions for Linux usage that the munchkins will likely not see much of unless I change my mind.  (This is a school computer for them so they will not have internet access or a password to an account that does.  But I may want to give them restricted internet access in Ubuntu just in case they need it for school, hence the 32-bit FAT partition).

Thanks in advance to any and all!

---

### Post by caljohnsmith on 2009-02-15
> **HunkirDowne said:**
> 
My question is about my fdisk report that states: "Partition 1 does not end on cylinder boundary."  What/why/how?  Does this mean that my partimage of sda1 is no good?  What about my partimage of sda2 which starts on the same cylinder as sda1 ends on?

Fortunately you don't need to worry at all about the "partition does not end on a cylinder boundary" type warning. "Cylinder" is mostly relevant to the ancient times when HDDs were less than 8.4 GB, and drives were accessed using the CHS geometry (Cylinders/Heads/Sectors) of the drive. Now that HDDs have outgrown the 8.4 GB limit of CHS notation, all modern HDDs use "LBA" (Logical Block Addressing) in order to access the data on the HDD, rather than the CHS method; LBA notation is limited to a max drive size of 2 TB, so it is far more suitable for modern drives, although even it is now becoming dated. But since the standard MS-DOS MBR (Master Boot Record) partition table hasn't changed since those times, partition editors still have to "fill in the blanks" for the CHS notation that is included in the partition table. Since CHS geometry has no physical relevance to modern drives, that means that it is entirely arbitrary which CHS geometry the partition editor assumes when it sets up the partitions. And it just so happens that most Windows partition editors assume a different geometry than the standard that Linux uses, i.e. 255 Heads, 63 sectors/track geometry. So bottom line, often Linux will report "partition does not end on a cylinder boundary" warnings when reading the partition table of drives that were partitioned with Windows software, but that's entirely OK and nothing to be concerned about. :)

---

### Post by HunkirDowne on 2009-02-15
> **caljohnsmith said:**
> Fortunately you don't need to worry at all about the "partition does not end on a cylinder boundary" type warning. 

<snip>

So bottom line, often Linux will report "partition does not end on a cylinder boundary" warnings when reading the partition table of drives that were partitioned with Windows software, but that's entirely OK and nothing to be concerned about. :)

Many thanks!  I'll keep my partimage stuff and will decide what to do with the dd image if it ever finishes cleanly.  :-/

---

### Post by AlexanderDGreat on 2010-07-05
Thanks this post helped clarify my confusions in my head. Straightforward yet very detailed answer. :)

---

### Post by AlexanderDGreat on 2010-07-05
For some strange reason, just boot from a LIVE CD and it will properly "fix" the message: Partition 1 does not end on cylinder boundary.

I don't know what it did, but I don't have the errors now, maybe it rounded it to cylinders. No clue. But it seems ok now, though I saw some 5mb and 1mb unallocated space in my hard disk. Which before wasn't the case.

---

### Post by HunkirDowne on 2010-07-05
> **AlexanderDGreat said:**
> For some strange reason, just boot from a LIVE CD and it will properly "fix" the message: Partition 1 does not end on cylinder boundary.

I don't know what it did, but I don't have the errors now, maybe it rounded it to cylinders. No clue. But it seems ok now, though I saw some 5mb and 1mb unallocated space in my hard disk. Which before wasn't the case.

This sounds a bit odd -- at least at first glance.  Unless your partition table actually changed, I would think you would still see that message.  **However,** if you are using different programs (or possibly different versions of the same program) you might see the message in one and not the other.

For instance, I see the message in fdisk but not cfdisk or parted.  Again, it's not an issue normally.  But I generally prefer a bit more order and would have nuked it long ago if we didn't have to have Windows installed on this computer.  Nevertheless, here are some snippets from different programs regarding the same device.

```
fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb10bcfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193        6718    52420095    7  HPFS/NTFS
/dev/sda3            6719        6734      128520   83  Linux

```

```
cfdisk -Pt /dev/sda
Partition Table for /dev/sda

         ---Starting----      ----Ending-----    Start     Number of
 # Flags Head Sect  Cyl   ID  Head Sect  Cyl     Sector    Sectors
-- ----- ---- ---- ----- ---- ---- ---- ----- ----------- -----------
 1  0x00   32   33     0 0x27   89   26   191        2048     3072000
 2  0x80    0    1   192 0x07  254   63  6717     3084480   104840190
 3  0x00    0    1  6718 0x83  254   63  6733   107924670      257040

```

```
parted -l
Model: ATA TOSHIBA MK2552GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            diag
 2      1579MB  55.3GB  53.7GB  primary   ntfs            boot
 3      55.3GB  55.4GB  132MB   primary   ext3

```

And finally my versions:
```
root@tree2:drain0# fdisk -v
fdisk (util-linux-ng 2.17.2)
root@tree2:drain0# cfdisk -v
cfdisk (util-linux-ng 2.17.2)
Copyright (C) 1994-2002 Kevin E. Martin & aeb
root@tree2:drain0# parted -v
parted (GNU parted) 2.3
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by <http://git.debian.org/?p=parted/parted.git;a=blob_plain;f=AUTHORS>.
root@tree2:drain0# uname -r
2.6.34-0.slh.11-sidux-686

```

As you can see I'm not in Ubuntu at the moment so your versions probably vary somewhat, but the output should be similar.

---

