---
title: "usb drive input output error troubleshooting"
date: 2017-10-05
forum: Hardware
---

### Post by rare HERO on 2017-10-05
Hello I experienced a problem while using a Kingston DataTraveler 100 G3 64GB. I had been using it interchangeably with my Dell XPS 13 (Ubuntu 14.04 LTS) my custom build desktop (Ubuntu 16.04) and campus computers (Windows 7 Professional - I think).

Recently, Windows prompted the drive should be repaired, and I think I clicked to repair it.

At that point, the drive wouldn't read so I used a windows CMD command in an attempt to fix it. Unfortunately, I can't remember what I used nor could I find it in a search.

The result is my drive is now unusable.

Aside from commenting on my attempt to use windows CMD **do you have any advice on how to repair the drive or regain access to the data?**

Thanks in advance,

This is what I've tried using the terminal on my 16.04 system:

```
~$ sudo fdisk -l
Disk /dev/loop0: 81.4 MiB, 85385216 bytes, 166768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 81.4 MiB, 85348352 bytes, 166696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 80.5 MiB, 84393984 bytes, 164832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 111.7 MiB, 117141504 bytes, 228792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5F8B70C2-E65A-4614-A488-C9B88016925F

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624 201005055 199954432 95.4G Linux filesystem
/dev/sda3  201005056 234440703  33435648   16G Linux swap


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0002d122

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1          63 1953525167 1953525105 931.5G 83 Linux

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sde: 57.7 GiB, 61983424512 bytes, 121061376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x44fdc91c

Device     Boot Start       End   Sectors  Size Id Type
/dev/sde1       36112 121061375 121025264 57.7G  c W95 FAT32 (LBA)

~$ sudo mkdir /media/usb-drive-0x44fdc91c
~$ sudo mount /dev/sde /media/usb-drive-0x44fdc91c
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0  81.4M  1 loop /snap/core/2898
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/user/Backup Data
loop2    7:2    0  80.5M  1 loop /snap/core/2462
sde      8:64   1  57.7G  0 disk 
&#9492;&#9472;sde1   8:65   1  57.7G  0 part 
loop0    7:0    0  81.4M  1 loop /snap/core/2774
sdc      8:32   0 931.5G  0 disk 
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda2   8:2    0  95.4G  0 part /
&#9500;&#9472;sda3   8:3    0    16G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0   512M  0 part /boot/efi
loop3    7:3    0 111.7M  1 loop /snap/simplenote/2


~$ sudo parted /dev/sde p
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sde: 62.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      18.5MB  62.0GB  62.0GB  primary               lba

~$ sudo mount /dev/sde1 /mnt
mount: /dev/sde1: can't read superblock


~$ dmesg | tail -n 20
[ 9038.943217] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.107206] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.279197] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.300347] sd 6:0:0:0: [sde] Unaligned partial completion (resid=1011, sector_sz=512)
[ 9039.300350] sd 6:0:0:0: [sde] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 9039.300352] sd 6:0:0:0: [sde] tag#0 CDB: Read(10) 28 00 00 00 8d 12 00 00 02 00
[ 9039.300353] blk_update_request: I/O error, dev sde, sector 36114
[ 9039.300373] EXT4-fs (sde1): unable to read superblock
[ 9039.427168] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.591177] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.763161] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9039.931155] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9040.099200] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9040.263136] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 9040.284304] sd 6:0:0:0: [sde] Unaligned partial completion (resid=1011, sector_sz=512)
[ 9040.284307] sd 6:0:0:0: [sde] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 9040.284309] sd 6:0:0:0: [sde] tag#0 CDB: Read(10) 28 00 00 00 8d 10 00 00 02 00
[ 9040.284310] blk_update_request: I/O error, dev sde, sector 36112
[ 9040.284329] SQUASHFS error: squashfs_read_data failed to read block 0x0
[ 9040.284331] squashfs: SQUASHFS error: unable to read squashfs_super_block


~$ sudo gparted
======================
libparted : 3.2
======================
Input/output error during read on /dev/sde
Input/output error during read on /dev/sde
Input/output error during read on /dev/sde
Input/output error during read on /dev/sde
/dev/sde: unrecognised disk label
Input/output error during read on /dev/sde


~$ sudo cfdisk


~$ sudo cfdisk /dev/sde
cfdisk: cannot open /dev/sde: Input/output error

~$ sudo fsck /dev/sde
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sde
Could this be a zero-length partition?

```

---

