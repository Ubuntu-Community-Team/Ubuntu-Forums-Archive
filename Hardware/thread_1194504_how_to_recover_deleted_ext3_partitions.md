---
title: "how to recover deleted ext3 partitions?"
date: 2009-06-22
forum: Hardware
---

### Post by Ndyanabo on 2009-06-22
About six months ago, I was trying to install ubuntu, probably 8.04, and did a really stupid thing. I was going to put the OS on a drive that I already had some stuff on. I got to the point where the installer asks where you want it, and I was going to customize it to put the OS in one partition, home on another, and have another partition of storage. 
I have some stuff on the disk, and I thought that the partitions were already in place. I was trying not to create new partitions, but use partitions that were already there.
Anyway, I felt that something wasn't right, and I panicked, and canceled out of the whole thing. Now, it appears that the changes I made to the partition table were written to the disk.  
It wasn’t like the disk was reformatted or anything, so most if not all of my data should be there (minus the parts over which new extended partition tables were written, if I understand things correctly). I’m hoping I can recover it with a little partition table kung-fu.

So, to get down to brass tacks:
-I’m reasonably certain that there were originally at least two ext3 partitions on the disk, perhaps three, and probably a swap as well. Anything that could have been ext3 would have been, since I always format to that. However, I was not sure exactly how things were, which is one reason I panicked and wanted to get out of the process.
-As I say, this was done in the Ubuntu installer probably for 8.04 or 8.10.

At this point, I've made an image of the screwed up partition with dd. I would like some help recovering the disk. 

here's the disk in question:

```
seth@pemba:~$ sudo fdisk -l 
Disk /dev/sdl: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000358cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1   *           1        1912    15358108+  83  Linux
/dev/sdl2            1913        2173     2096482+  82  Linux swap / Solaris
/dev/sdl3            2174       57345   443169090   83  Linux

```
TIA!

---

### Post by Ndyanabo on 2009-06-24
bump

---

### Post by Ndyanabo on 2009-06-27
bump

---

### Post by Ndyanabo on 2009-06-28
bump

---

### Post by cariboo on 2009-06-28
I would suggest you try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), it is in the repositories, and will help you recover missing partitions. Photorec is part of the testdisk package, it will help you recover missing files. Testdisk is in the repositories.

---

### Post by Ndyanabo on 2009-06-29
I'm not very sure of myself when it comes to testdisk. Here's what I got from the deep analysis. Should I go through with the write process?

```


Tue Jun 23 20:07:10 2009
Command line: TestDisk

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.28-13-generic (#44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009)
Compiler: GCC 4.1 - Jul 17 2008 09:54:04
ext2fs lib: 1.40.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
Warning: can't get size for /dev/mapper/control
Hard disk list
Disk /dev/sda - 400 GB / 372 GiB - CHS 48641 255 63, sector size=512 - ATA SAMSUNG HD403LJ
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST3500641NS
Disk /dev/sdc - 750 GB / 698 GiB - CHS 91201 255 63, sector size=512 - ATA ST3750330AS
Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST3500830AS
Disk /dev/sde - 750 GB / 698 GiB - CHS 91201 255 63, sector size=512 - ATA ST3750640AS
Disk /dev/sdf - 1500 GB / 1397 GiB - CHS 182401 255 63, sector size=512 - ATA ST31500341AS
Disk /dev/sdk - 512 MB / 488 MiB - CHS 993 16 63, sector size=512 - SanDisk Cruzer Micro
Disk /dev/sdl - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ST350032 0AS

Partition table type (auto): Intel
Disk /dev/sdl - 500 GB / 465 GiB - ST350032 0AS
Partition table type: Intel

Analyse Disk /dev/sdl - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
 1 * Linux                    0   1  1  1911 254 63   30716217
 2 P Linux Swap            1912   0  1  2172 254 63    4192965
 3 P Linux                 2173   0  1 57344 254 63  886338180
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sdl - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/117, s_mnt_count=1/27, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3839527
recover_EXT2: part_size 30716216
   D Linux                    0   1  1  1911 254 62   30716216
     EXT3 Large file Sparse superblock Recover, 15 GB / 14 GiB
   D Linux Swap            1912   0  1  2172 254 42    4192944
     SWAP2 version 1, 2146 MB / 2047 MiB

recover_EXT2: s_block_group_nr=0/3381, s_mnt_count=2/27, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 110792272
recover_EXT2: part_size 886338176
   D Linux                 2173   0  1 57344 254 59  886338176
     EXT3 Large file Sparse superblock Recover, 453 GB / 422 GiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * Linux                    0   1  1  1911 254 63   30716217
     EXT3 Large file Sparse superblock Recover, 15 GB / 14 GiB
   P Linux Swap            1912   0  1  2172 254 63    4192965
     SWAP2 version 1, 2146 MB / 2047 MiB
   P Linux                 2173   0  1 57344 254 63  886338180
     EXT3 Large file Sparse superblock Recover, 453 GB / 422 GiB

interface_write()
 1 * Linux                    0   1  1  1911 254 63   30716217
 2 P Linux Swap            1912   0  1  2172 254 63    4192965
 3 P Linux                 2173   0  1 57344 254 63  886338180

search_part()
Disk /dev/sdl - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/117, s_mnt_count=1/27, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3839527
recover_EXT2: part_size 30716216
   D Linux                    0   1  1  1911 254 62   30716216
     EXT3 Large file Sparse superblock Recover, 15 GB / 14 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/117, s_mnt_count=0/27, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3839527
recover_EXT2: part_size 30716216
   D Linux                    0   1  1  1911 254 62   30716216
     EXT3 Large file Sparse superblock Backup superblock, 15 GB / 14 GiB
   D Linux Swap            1912   0  1  2172 254 42    4192944
     SWAP2 version 1, 2146 MB / 2047 MiB

recover_EXT2: s_block_group_nr=0/3381, s_mnt_count=2/27, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 110792272
recover_EXT2: part_size 886338176
   D Linux                 2173   0  1 57344 254 59  886338176
     EXT3 Large file Sparse superblock Recover, 453 GB / 422 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/3381, s_mnt_count=0/27, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 110792272
recover_EXT2: part_size 886338176
   D Linux                 2173   0  1 57344 254 59  886338176
     EXT3 Large file Sparse superblock Backup superblock, 453 GB / 422 GiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * Linux                    0   1  1  1911 254 63   30716217
     EXT3 Large file Sparse superblock Recover, 15 GB / 14 GiB
   P Linux Swap            1912   0  1  2172 254 63    4192965
     SWAP2 version 1, 2146 MB / 2047 MiB
   P Linux                 2173   0  1 57344 254 63  886338180
     EXT3 Large file Sparse superblock Recover, 453 GB / 422 GiB

interface_write()
 1 * Linux                    0   1  1  1911 254 63   30716217
 2 P Linux Swap            1912   0  1  2172 254 63    4192965
 3 P Linux                 2173   0  1 57344 254 63  886338180
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

---

### Post by Ndyanabo on 2009-06-30
bump

---

### Post by Ndyanabo on 2009-07-03
bump

---

