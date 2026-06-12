---
title: "FakeRaid Raid 5 AMD"
date: 2011-03-12
forum: Hardware
---

### Post by TheFuzz4 on 2011-03-12
Good Afternoon Ladies and Gentlemen,

So I just got done rebuilding my beast of a machine, the rebuild consisted of a new Mobo, proc, mem and fakeraid controller.  So in the previous machine I had the Nvidia chipset but apparently in the years since I did my initial build out and now Nvidia is no longer doing the chipsets and it is now an AMD chipset. 
So in the new build I have a Gigabyte GA-890GPA-UD3H which has the AMD SB850 raid controller.  In the past I was able to just mount my Raid5 with dmraid however that does not seem to be a possibility any longer.  In the Ubuntu Disk utility it does see the 4 drives as a raid setup as you can see in my attachment.  However I cannot for the life of me figure out how to gain access to the Raid5.  I know that it is a fakeraid and a controller card would be the ideal way to go about this but that is not really an option at the moment.  I did see that back in 2010 AMD had yet to release how to go about talking to the controller but didn't know if maybe I missed something along the way. Its not a huge deal breaker if I can't get it to work but I would like to,  the raid is a NTFS partition and all I would really like it for in Linux is for movie ripping and also to throw my VM's on there as well. 
Here is my output from sudo fdisk -l
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x193d20e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       57992   465817600    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a829a82

Disk /dev/sdc doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83bfba6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       57992   465817600    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d9adfa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sde2              13       25497   204696576    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sde3           25497      121602   771960833    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sde5           25497       27321    14647296   83  Linux
/dev/sde6           27321       27807     3905536   82  Linux swap / Solaris
/dev/sde7           27807      121602   753405952   83  Linux

Disk /dev/sdi: 2097 MB, 2097152000 bytes
66 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 4158 * 512 = 2128896 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1         985     2047746+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(984, 65, 63) logical=(984, 65, 49)
jhamilto@TheBeastLinux:~$ sudo fdisk -l
[sudo] password for jhamilto: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x193d20e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       57992   465817600    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a829a82

Disk /dev/sdc doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83bfba6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       57992   465817600    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d9adfa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sde2              13       25497   204696576    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sde3           25497      121602   771960833    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sde5           25497       27321    14647296   83  Linux
/dev/sde6           27321       27807     3905536   82  Linux swap / Solaris
/dev/sde7           27807      121602   753405952   83  Linux

Disk /dev/sdi: 2097 MB, 2097152000 bytes
66 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 4158 * 512 = 2128896 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1         985     2047746+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(984, 65, 63) logical=(984, 65, 49)

```
and the output from dmraid -ay
```
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: pdc: zero sectors on /dev/sda
ERROR: pdc: setting up RAID device /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_cjegifid" [2/4] on /dev/sdb
ERROR: nvidia: wrong # of devices in RAID set "nvidia_cjegifid" [2/4] on /dev/sdc
ERROR: removing inconsistent RAID set "nvidia_cjegifid"
ERROR: no RAID set found
no raid sets

```
and lastly sudo dmraid -r
```
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: pdc: zero sectors on /dev/sda
ERROR: pdc: setting up RAID device /dev/sda
/dev/sdc: nvidia, "nvidia_cjegifid", raid5_ls, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_cjegifid", raid5_ls, ok, 312581806 sectors, data@ 0

```
I hope that I was able to provide enough information on this and anymore information that you might need to help me fix this please let me know and I will provide it.  I thank you all in advance for your help with this and I hope that it also helps someone else out as well.  Thank you.

---

### Post by TheFuzz4 on 2011-03-12
So it would appear that I am not alone at all in this problem and AMD just hasn't played nice with the Linux community as of yet.  Ah well I'll just have to wait this one out and I know that we will find a solution.

---

### Post by srs5694 on 2011-03-12
My knowledge of motherboard-based software RAID (what many people call "fake RAID") is limited; however, my understanding is that the formats used for this vary from one chipset to another. If this is correct, then there's no way you'll be able to access the data on your disks in your new motherboard, under *any* OS. If your disks hold vital data, you'll have to move them back to your old system (or another computer that uses an nVidia disk controller), back the data up, move the disks over to the new computer, and restore your data.

Linux's own software RAID solution works the same way no matter what your disk hardware is, so you wouldn't have had this problem if you'd used Linux's software RAID rather than the motherboard-specific software RAID; however, Linux's software RAID can't be used by Windows.

Another comment: Several of your disks provoked an fdisk warning about GPT data being present on the disks, yet they produced valid MBR partition tables. If this situation reflects a change from GPT to MBR partitioning at some point rather than some odd effect from the way you partitioned using software RAID, it should be corrected. The leftover GPT data can confuse some utilities, which may show the disk as unallocated or use the old GPT data rather than the newer MBR data. You can wipe the old GPT data using my [FixParts](http://www.rodsbooks.com/fixparts) program; however, I don't advise doing this until you've backed up you disks and gotten them back into a working state for your new system. It's possible that those actions will correct the problem.

---

