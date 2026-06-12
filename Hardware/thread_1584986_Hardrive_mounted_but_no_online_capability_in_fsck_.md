---
title: "Hardrive mounted but no online capability in fsck tool for file system"
date: 2010-09-29
forum: Hardware
---

### Post by laodan on 2010-09-29
Hi everyone,




[COLOR="Blue"]After a reinstall of Ubuntu 10.04 I can no longer open my secondary harddrive (backup) and all my data are lost. In short:[/COLOR]



1. Initially: accidental reinstall of Ubuntu on that secondary drive while I meant to re-install on my primary drive. Not knowing that the re-install had been done on my secondary drive I was surprise to find the reboot of my system was not working. So I again re-installed and this time it was realized on my primary drive. After successfully booting I discovered that my backup had disappeared on my secondary drive and that instead it contained an install of Ubuntu 10.04.
That's how I understood what had happened.

2. I used "sudo testdisk" to try to recover the content of my secondary drive. Log follows:
 
""""""""
Wed Sep 29 17:17:00 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.32-25-generic (#44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:48:38
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       321672960 sectors
/dev/sda: user_max   321672960 sectors
/dev/sda: native_max 2905856 sectors
/dev/sda: dco        321672960 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       1250263728 sectors
/dev/sdb: user_max   1250263728 sectors
/dev/sdb: native_max 8749744 sectors
/dev/sdb: dco        1250263728 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 164 GB / 153 GiB - CHS 20023 255 63, sector size=512 - ATA HDT722516DLAT80
Disk /dev/sdb - 640 GB / 596 GiB - CHS 77825 255 63, sector size=512 - ATA WDC WD6400AACS-0

Partition table type (auto): Intel
/dev/sda: Device Configuration Overlay (DCO) present.
Disk /dev/sda - 164 GB / 153 GiB - ATA HDT722516DLAT80
Partition table type: Intel

Analyse Disk /dev/sda - 164 GB / 153 GiB - CHS 20023 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
 1 P Linux                    0   1  1 19834 254 63  318649212 [Backup]
 2 E extended LBA         19835   0  1 20022 254 63    3020220
No partition is bootable
 5 L Linux Swap           19835   1  1 20022 254 63    3020157
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 164 GB / 153 GiB - CHS 20023 255 63

recover_EXT2: s_block_group_nr=0/1215, s_mnt_count=16/30, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 39831151
recover_EXT2: part_size 318649208
     Linux                    0   1  1 19834 254 59  318649208 [Backup]
     EXT2 Large file Sparse superblock, 163 GB / 151 GiB
     Linux Swap           19835   1  1 20022 254 42    3020136
     SWAP2 version 1, 1546 MB / 1474 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * Linux                    0   1  1 19834 254 63  318649212 [Backup]
     EXT2 Large file Sparse superblock, 163 GB / 151 GiB
   L Linux Swap           19835   1  1 20022 254 63    3020157
     SWAP2 version 1, 1546 MB / 1474 MiB

interface_write()
 1 * Linux                    0   1  1 19834 254 63  318649212 [Backup]
 2 E extended LBA         19835   0  1 20022 254 63    3020220
 5 L Linux Swap           19835   1  1 20022 254 63    3020157

search_part()
Disk /dev/sda - 164 GB / 153 GiB - CHS 20023 255 63

recover_EXT2: s_block_group_nr=0/1215, s_mnt_count=16/30, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 39831151
recover_EXT2: part_size 318649208
     Linux                    0   1  1 19834 254 59  318649208 [Backup]
     EXT2 Large file Sparse superblock, 163 GB / 151 GiB

recover_EXT2: s_block_group_nr=0/1176, s_mnt_count=8/25, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 38566400
recover_EXT2: part_size 308531200
     Linux                    0  32 33 19205  78  9  308531200 [Data]
     EXT4 Large file Sparse superblock, 157 GB / 147 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/1215, s_mnt_count=14/30, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 39831151
recover_EXT2: part_size 318649208
     Linux                    0   1  1 19834 254 59  318649208 [Backup]
     EXT2 Large file Sparse superblock Backup superblock, 163 GB / 151 GiB
     Linux Swap           19835   1  1 20022 254 42    3020136
     SWAP2 version 1, 1546 MB / 1474 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
     Linux                    0   1  1 19834 254 59  318649208 [Backup]
     EXT2 Large file Sparse superblock, 163 GB / 151 GiB
     Linux                    0  32 33 19205  78  9  308531200 [Data]
     EXT4 Large file Sparse superblock, 157 GB / 147 GiB
   * Linux Swap           19835   1  1 20022 254 42    3020136
     SWAP2 version 1, 1546 MB / 1474 MiB

interface_write()
 1 P Linux                    0   1  1 19834 254 59  318649208 [Backup]
 2 * Linux Swap           19835   1  1 20022 254 42    3020136
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
You will have to reboot for the change to take effect.
""""""""




[COLOR="Blue"]Seeing the Linux Backup partition I thought TestDisk had recovered my backup...
But opening the drive at 
/media/3b3cd79f-d182-4717-8fa5-85312b17a193 I get a message "(empty)".
So my initial optimism suddenly vanished.[/COLOR]





When checking the file system in disk utility I get the following message:

""""""""
Error checking filesystem on volume

An error occured while performing an operation on "163 GB Filesystem" (Partition 1 of ATA HDT722516DLAT80): The device is busy


Details
Device is mounted and no online capability in fsck tool for file system
""""""""





I tried "gksudo pysdm" to check and get the following:
- sda
sda1   type: swap   Options: sw   name: sdb5   model: WDC   Serial: unknown   Bus: scsi
sda5   name: sda5   Mountpoint: /media/sda5   Type: swap  Options: default    model: HDT722516DLAT80   Serial: unknown   Bus: scsi





In summary this secondary drive is mounted, in my primary drive, at 
/media/3b3cd79f-d182-4717-8fa5-85312b17a193

When right clicking the "Properties" of the drive I get:
- name: 3b3cd79f-d182-4717-8fa5-85312b17a193
- Type: folder (inode/directory)
- Contents: nothing
- Location: /media
- Volume: 163 GB Filesystem
- Free space: 100.3 GB
- Used: 49.2 GB
- Free: 100.3 GB
- Total capacity: 149.6 GB
- Filesystem type: ext3/ext4

The used 49.2 GB corresponds to the backup of my primary drive. 





[COLOR="Blue"]Is there someone out there who has an idea how to recover those 49.2Gb of used space on sda5?

Thanks in advance.

laodan[/COLOR]

---

### Post by psusi on 2010-09-29
You have to unmount it to fsck it, and no, your data is at least mostly gone.  You might get some luck with photorec.

---

### Post by laodan on 2010-09-30
Thanks [psusi]("http://ubuntuforums.org/member.php?u=41311"),

photorec recovered some files. But few...

---

