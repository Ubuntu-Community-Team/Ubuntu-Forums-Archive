---
title: "No space left on device"
date: 2015-02-04
forum: Hardware
---

### Post by bobx on 2015-02-04
I am running 12.04. I have an USB 1TB external drive. I get the error message "no more space left on device" when I try to create a new file ("touch xx"). There is plenty of disk space and inodes.
```

Filesystem        Inodes   IUsed     IFree IUse% Mounted on
/dev/sdc5      169661136 4909824 164751312    3% /media/5AF

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sdc5      976751968 812006032 164745936  84% /media/5AF
```


I counted the number of files on the drive and it was 4,901,244 files. It appears to be a number of files issue. If I delete a file I can copy a huge file in its place. But If I try to add a small new file without deleting an old file I get the "no more space left on device" message.

The drive is formatted NTFS.
   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sdc5           16128  1953520064   976751968+   7  HPFS/NTFS/exFAT
```


/dev/sdc5 on /media/5AF type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

What is stopping me from added new files to the drive ????

Bob

---

### Post by TheFu on 2015-02-04
Are any other partitions full?  Some programs use temporary files?

---

### Post by bobx on 2015-02-04
There are no full partitions. The / device is only 53% full

---

### Post by TheFu on 2015-02-04
Anything in the log files?

If you umount and mount it - any errors?

Can you run a chkdsk/scandisk from Windows on the partition?

Sorry - just brainstorming here. Really don't have any answer.

---

### Post by bobx on 2015-02-04
I looked in the log files and syslog has "No free mft record for $MFT: No space left on device"

---

### Post by TheFu on 2015-02-04
I googled that error - lots of interesting information. None of it seemed to provide a resolution that I could see.

---

### Post by bobx on 2015-02-04
I also looked for the error and did not find anything helpful. I did have trouble with this drive a while back and had to repair the "table". I think I used fsck under linux because windows repair did not work.

---

### Post by weatherman2 on 2015-02-04
Try running Windows chkdsk on the disk in question.  Boot a Windows disc if you have to.

---

### Post by bobx on 2015-02-04
I did try Windows chkdsk when I had problems with the drive a while back. chkdsk did not recognize the drive so I "repaired" it with linux fsck. I did not recheck with windows chkdsk since linux fsck said it was fixed and the drive worked.

---

### Post by mörgæs on 2015-02-04
> **bobx said:**
> 
I counted the number of files on the drive and it was 4,901,244 files.

What are you storing on that drive?

---

### Post by bobx on 2015-02-04
Backups

---

### Post by weatherman2 on 2015-02-04
Have you checked the drive's S.M.A.R.T. health lately?  Try GSmartControl.  See if any Attributes are highlighted in pink or red.  You can also run the extended S.M.A.R.T. test which usually takes at least a few hours.

---

### Post by TheFu on 2015-02-04
FYI - running Linux tools on NTFS partitions is a bad idea. Always use the native OS for the file system to fix issues.  There is no fsck for NTFS.

---

### Post by bobx on 2015-02-04
I did run a linux tool to fix the NTFS partition, I do not remember which one (not fsck), maybe it was ntfsfix. I first tried to fix it with windows tools but that did not work. I am running TestDisk on it now when it finishes I will hook it up to windows and see what happens.

---

### Post by bobx on 2015-02-05
TestDisk finished it found a problem with the MFT. Not sure what to do now. Here is the log from TestDisk


Wed Feb  4 16:08:05 2015
Command line: TestDisk

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 3.2.0-58-generic-pae (#88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013) i686
Compiler: GCC 4.4
Compilation date: 2013-07-30T14:11:17
ext2fs lib: 1.41.12, ntfs lib: libntfs-3g, reiserfs lib: 0.3.1-rc8, ewf lib: 20120504
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488397168 sectors
/dev/sda: user_max   488397168 sectors
/dev/sda: native_max 488397168 sectors
/dev/sda: dco        488397168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 1 sectors, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - WDC WD2500BEVT-75ZCT2, S/N:WD-WXH808990475, FW:11.01A11
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - MD10000- AQDW-RO

Partition table type (auto): Intel
Disk /dev/sdc - 1000 GB / 931 GiB - MD10000- AQDW-RO
Partition table type: Intel

Analyse Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 1/1/1
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4
Current partition structure:
 1 E extended LBA             1   0  1 121600 254 63 1953504000
No partition is bootable
 5 L HPFS - NTFS              1   1  1 121600 254 63 1953503937

search_part()
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
NTFS at 1/1/1
filesystem size           1953503937
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               122093996
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              1   1  1 121600 254 63 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L HPFS - NTFS              1   1  1 121600 254 63 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
add_ext_part_i386: max
add_ext_part_i386: min

interface_write()
 1 E extended LBA             1   0  1 121600 254 63 1953504000
 5 L HPFS - NTFS              1   1  1 121600 254 63 1953503937

search_part()
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
NTFS at 1/1/1
filesystem size           1953503937
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               122093996
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              1   1  1 121600 254 63 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
NTFS at 121600/254/63
filesystem size           1953503937
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               122093996
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              1   1  1 121600 254 63 1953503937
     NTFS found using backup sector, blocksize=4096, 1000 GB / 931 GiB
NTFS at 121600/254/63
filesystem size           1953503937
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               122093996
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS: Can't read MFT
     HPFS - NTFS          121600 254 63 243200 253 62 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
This partition ends after the disk limits. (start=1953520064, size=1953503937, end=3907024000, disk end=1953525168)
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (1000 GB / 931 GiB) seems too small! (< 2000 GB / 1863 GiB)
The following partition can't be recovered:
     HPFS - NTFS          121600 254 63 243200 253 62 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L HPFS - NTFS              1   1  1 121600 254 63 1953503937
     NTFS, blocksize=4096, 1000 GB / 931 GiB
add_ext_part_i386: max
add_ext_part_i386: min

interface_write()
 1 E extended LBA             1   0  1 121600 254 63 1953504000
 5 L HPFS - NTFS              1   1  1 121600 254 63 1953503937
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
write_all_log_i386: CHS: 1/0/1,lba=16065

TestDisk exited normally.

---

