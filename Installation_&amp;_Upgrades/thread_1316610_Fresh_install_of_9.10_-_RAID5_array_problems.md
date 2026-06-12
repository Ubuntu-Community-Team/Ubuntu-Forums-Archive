---
title: "Fresh install of 9.10 - RAID5 array problems"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by aquabubble on 2009-11-06
My machine has two RAID5 arrays, one of 6x250GB HDDs (md0) and another of 4x300GB HDDs (md1). These had previously been created under EVMS though not as EVMS volumes.
 
A few months ago I had a system drive failure and it's taken me until now to get around to fixing things. To first test that all other hardware was working properly, I booted the SystemRescueCD, which was able to assemble both of my RAID arrays as md0 and md1. Further examination revealed that one drive from md0 had failed though the array was still functioning in degraded mode. Thankfully, I was able to mount them and browse their filesystems.
 
**sudo mdadm --detail /dev/md0**
 
```
 
/dev/md0:
        Version : 00.90
  Creation Time : Sat Mar  4 18:31:44 2006
     Raid Level : raid5
     Array Size : 1220992000 (1164.43 GiB 1250.30 GB)
  Used Dev Size : 244198400 (232.89 GiB 250.06 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Fri Nov  6 08:58:20 2009
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-asymmetric
     Chunk Size : 128K
           UUID : ce9f5c43:5d44a130:2e63d74e:ed30a123
         Events : 0.6778878
    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8        0        1      active sync   /dev/sda
       2       8       16        2      active sync   /dev/sdb
       3       0        0        3      removed
       4       8       32        4      active sync   /dev/sdc
       5       8       96        5      active sync   /dev/sdg

```
 
Time to start rebuilding the server; downloaded 9.10 Server edition and set about re-installing on a fresh 80GB HDD. Install went well though on reboot, the boot stalled at the "Loading GRUB" message for a few minutes - (that's a different problem though)!
 
On logging in, I checked that the arrays were assembled and all-present. md1 mounted okay but md0 failed to mount.
 
**sudo mount /dev/md0 /mnt/raid_array_0**
 
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
 
Oh dear. What's this?
 
**dmesg | tail** 
 
```
[ 1008.730588]  --- rd:6 wd:5
[ 1008.730592]  disk 0, o:1, dev:sdf
[ 1008.730596]  disk 1, o:1, dev:sda
[ 1008.730600]  disk 2, o:1, dev:sdb
[ 1008.730603]  disk 4, o:1, dev:sdc
[ 1008.730607]  disk 5, o:1, dev:sdg
[ 1008.730681] md0: detected capacity change from 0 to 1250295808000
[ 1008.731251]  md0: unknown partition table
[ 2179.042477] EXT2-fs error (device md0): ext2_check_descriptors: Block bitmap for group 3968 not in group (block 126903275)!
[ 2179.042514] EXT2-fs: group descriptors corrupted!
```
 
Argh! How could this be. Delve deeper...
 
**sudo fsck -n /dev/md0**
 
```
 
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Group descriptors look bad... trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear? no
fsck.ext2: Illegal inode number while checking ext3 journal for raid5_arr0_vol0

```
 
Crikes. Any more info available I wonder? 
 
**sudo debugfs -c /dev/md0**
 
```
debugfs 1.41.9 (22-Aug-2009)
/dev/md0: catastrophic mode - not reading inode or group bitmaps
debugfs:  ncheck 8
Inode   Pathname
ncheck: Can't read next inode while doing inode scan
```
 
Well that didn't tell me anything, apart from I'm in trouble. I wonder what fdisk will tell me?
 
**sudo fdisk -l** 
 
```
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
8 heads, 1 sectors/track, 61049646 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16633       16882         995+  c7  Syrinx
/dev/sda2               1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sda3       268452089   268452338         995+  c7  Syrinx
/dev/sda4               1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sde doesn't contain a valid partition table
Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdf doesn't contain a valid partition table
Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdg doesn't contain a valid partition table
Disk /dev/sdh: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdh doesn't contain a valid partition table
Disk /dev/sdj: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001
   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1        9698    77899153+  8e  Linux LVM
/dev/sdj2            9699        9729      249007+   5  Extended
/dev/sdj5            9699        9729      248976   83  Linux
Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdi doesn't contain a valid partition table
Disk /dev/md1: 960.2 GB, 960218529792 bytes
2 heads, 4 sectors/track, 234428352 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000
Disk /dev/md1 doesn't contain a valid partition table
Disk /dev/md0: 1250.3 GB, 1250295808000 bytes
2 heads, 4 sectors/track, 305248000 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000
Disk /dev/md0 doesn't contain a valid partition table

```
 
Hang on... what's this Syrinx stuff doing on my /dev/sda device? 
 
Has the install of 9.10 killed my RAID5 array? How could it? Is it related to the GRUB problem? More importantly, does anybody know how can I recover from this? - apart from launching into fsck -y with reckless abandon?
 
This seems strangely similar to these other problems:
[http://ubuntuforums.org/showthread.php?t=1249102](http://ubuntuforums.org/showthread.php?t=1249102)
[http://ubuntuforums.org/showthread.php?t=833770](http://ubuntuforums.org/showthread.php?t=833770)
 
I'd be very grateful for any assistance.

---

### Post by jjuw51878 on 2010-12-08
Did you ever find a solution to this problem? I'm having similar messages in my error log.
 
thanks!

---

