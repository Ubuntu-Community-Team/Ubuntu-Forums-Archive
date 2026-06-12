---
title: "exited with non-zero exit status 32 mount wrong fs type bad option bad superblock"
date: 2018-01-27
forum: Hardware
---

### Post by z4ppy on 2018-01-27
please can some one help i have followed a few solutions but to no avail. My Toshiba HDD unencrypts when i enter password but it wont mount correctly.

this is the error

[IMG]https://imgur.com/a/NgBMx[/IMG]

here i the output of my fdisk

sudo fdisk -l
Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C93B224A-D7D5-428D-9898-8C420E705E1B

Device       Start        End   Sectors  Size Type
/dev/sda1     2048    1050623   1048576  512M EFI System
/dev/sda2  1050624    2050047    999424  488M Linux filesystem
/dev/sda3  2050048 1000214527 998164480  476G Linux filesystem


Disk /dev/mapper/sda3_crypt: 476 GiB, 511058116608 bytes, 998160384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 468.1 GiB, 502603448320 bytes, 981647360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 7.9 GiB, 8451522560 bytes, 16506880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 7.9 GiB, 8450998272 bytes, 16505856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sde: 465.8 GiB, 500107859968 bytes, 976773164 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x12b683a2

Device     Boot Start       End   Sectors   Size Id Type
/dev/sde1        2048 976769023 976766976 465.8G 83 Linux


SECOND OUTPUT

sudo e2fsck -f /dev/sde1
e2fsck 1.43.4 (31-Jan-2017)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sde1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/sde1 contains a crypto_LUKS filesystem

---

