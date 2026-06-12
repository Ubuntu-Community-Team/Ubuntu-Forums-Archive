---
title: "External HDD Woxter Pocket DivX problem"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by arrizaba on 2005-02-20
Hi! 
I have problems when plugging in my external HDD Woxter pocket DivX. In the beginning everything works fine, I can read and write from the disk. Then, if I write on it, after few seconds it becomes 'read only'.  I am also unable to unmount the drive.
This is what comes with dmesg:

[INDENT]
usb 3-2: new high speed USB device using address 4
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: Genesys   Model: USB to IDE Disk   Rev: 0002
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 117304992 512-byte hdwr sectors (60060 MB)
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1 < p5 >
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
USB Mass Storage device found at 4
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sda1.
attempt to access beyond end of device
sda1: rw=0, want=68, limit=2
attempt to access beyond end of device
sda1: rw=0, want=1252, limit=2
attempt to access beyond end of device
sda1: rw=0, want=1028, limit=2
UDF-fs: No partition found (1)
attempt to access beyond end of device
sda1: rw=0, want=66, limit=2
isofs_fill_super: bread failed, dev=sda1, iso_blknum=16, block=32
attempt to access beyond end of device
sda1: rw=0, want=3, limit=2
HFS+-fs: unable to find HFS+ superblock
attempt to access beyond end of device
sda1: rw=0, want=3, limit=2
VFS: Can't find a HFS filesystem on dev sda1.
attempt to access beyond end of device
sda1: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock
attempt to access beyond end of device
sda1: rw=0, want=4, limit=2
EXT2-fs: unable to read superblock
attempt to access beyond end of device
sda1: rw=0, want=18, limit=2
ReiserFS: sda1: warning: sh-2006: read_super_block: bread failed (dev sda1, block 8, size 1024)
attempt to access beyond end of device
sda1: rw=0, want=130, limit=2
ReiserFS: sda1: warning: sh-2006: read_super_block: bread failed (dev sda1, block 64, size 1024)
ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
attempt to access beyond end of device
sda1: rw=0, want=8, limit=2
XFS: SB read failed
attempt to access beyond end of device
sda1: rw=0, want=72, limit=2
attempt to access beyond end of device
sda1: rw=0, want=128, limit=2
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
    File system has been set read-only
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)
FAT: Filesystem panic (dev sda5)
    fat_get_cluster: invalid cluster chain (i_pos 458689)[/INDENT]

When I do "fdisk -l":
[INDENT]
Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7301    58637250    f  W95 Ext'd (LBA)
/dev/sda5               2        7301    58637218+   b  W95 FAT32[/INDENT]

Can anyone help me here? It is nasty to have to use Windows for transfering files to the drive.... :( .Any help would be much appreciated.

---

### Post by phen on 2005-05-22
hello all!

have got the same problem with my mp3 player. it works (and is mounted in rw-mode), but when i write something on it, it turns read-only with the same dmesg output.

if anyone has a solution, please let us know!

thank you

cheers,

kai

---

