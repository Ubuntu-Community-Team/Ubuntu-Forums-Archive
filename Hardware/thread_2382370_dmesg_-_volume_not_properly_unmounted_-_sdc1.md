---
title: "dmesg - volume not properly unmounted - sdc1"
date: 2018-01-12
forum: Hardware
---

### Post by istvan5 on 2018-01-12
Hi !

I did a mistake, I think this was it, I deleted the folder "system information" on a FAT formatted MicroSD card,
--> now I cannot access the MicroSD card any more
--> how to fix this
--> no data on it, so formatting would be no problem


0. sdc is not shown in GPARTED,

1. dmesg shows 

> 
[ 8430.607901] sd 4:0:0:0: [sdc] 1984000 512-byte logical blocks: (1.02 GB/969 MiB)
[ 8430.616147]  sdc: sdc1
[ 8430.937423] sd 4:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8430.937437] sd 4:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[ 8430.937445] sd 4:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[ 8430.937462] sd 4:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 00 f9 00 00 08 00
[ 8430.937467] blk_update_request: I/O error, dev sdc, sector 249
[ 8430.939340] sd 4:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8430.939346] sd 4:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[ 8430.939352] sd 4:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[ 8430.939357] sd 4:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 00 f9 00 00 01 00
[ 8430.939361] blk_update_request: I/O error, dev sdc, sector 249
[ 8430.939368] Buffer I/O error on dev sdc1, logical block 0, async page read
[ 8430.940850] sd 4:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8430.940871] sd 4:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[ 8430.940878] sd 4:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[ 8430.940885] sd 4:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 00 fa 00 00 07 00
[ 8430.940890] blk_update_request: I/O error, dev sdc, sector 250
[ 8430.940897] Buffer I/O error on dev sdc1, logical block 1, async page read
[ 8430.940904] Buffer I/O error on dev sdc1, logical block 2, async page read
[ 8430.940908] Buffer I/O error on dev sdc1, logical block 3, async page read
[ 8430.940912] Buffer I/O error on dev sdc1, logical block 4, async page read
[ 8430.940916] Buffer I/O error on dev sdc1, logical block 5, async page read
[ 8430.940919] Buffer I/O error on dev sdc1, logical block 6, async page read
[ 8430.940923] Buffer I/O error on dev sdc1, logical block 7, async page read
[ 8443.408578] sd 4:0:0:0: [sdc] 1984000 512-byte logical blocks: (1.02 GB/969 MiB)
[ 8443.416169]  sdc: sdc1

sd 4:0:0:0: [sdc] 61896704 512-byte logical blocks: (31.7 GB/29.5 GiB)
sdc: sdc1
FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.


2. FDISK dont show the drive sdc / sdc1

> sudo fdisk -l

3. i tried FSCK

> 
sudo fsck -a /dev/sdc


gives me --> 


fsck from util-linux 2.27.1
fsck.ext2: No medium found while trying to open /dev/sdc
/dev/sdc: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


4. i tried
> 
sudo fsck -a /dev/sdc1

gives me -->
fsck from util-linux 2.27.1
fsck.ext2: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?



5. i tried E2FSCK on sdc

> 
sudo e2fsck -b 8193 /dev/sdc

gives me -->
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



6. i tried E2FSCK on sdc1

> 
sudo e2fsck -b 8193 /dev/sdc1

7. tried to mount and to demount, --> dont work too

gives me -->

e2fsck 1.42.13 (17-May-2015)
e2fsck: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?




how can i solve this ??

thx

---

### Post by VMC on 2018-01-12
did you try ```
sudo fdisk /dev/sdc
```, then 'm' will give info. You then delete partitions, format ,etc

edit: after you delete partitions, then add a new one. Use "mkfs.vfat /dev/sdc1" to format it.

---

