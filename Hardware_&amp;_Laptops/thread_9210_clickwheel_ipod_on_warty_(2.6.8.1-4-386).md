---
title: "clickwheel ipod on warty (2.6.8.1-4-386)"
date: 2004-12-25
forum: Hardware &amp; Laptops
---

### Post by Golovko on 2004-12-25
This is dmesg output when I plug the clickwheel ipod into the dock connected via USB cable (and my laptop is only USB 1.1). Also note the ipod is in condition as shipped from apple (i.e. in Mac format, hfs+?):

usb 1-1: new full speed USB device using address 8
scsi4 : SCSI emulation for USB Mass Storage devices
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 02
sda: Spinning up disk.......ready
SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: [mac] p1 p2 p3
Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0 USB Mass Storage device found at 8
FAT: invalid media value (0x74)
VFS: Can't find a valid FAT filesystem on dev sda1.
attempt to access beyond end of device
sda1: rw=0, want=68, limit=62
attempt to access beyond end of device
sda1: rw=0, want=1252, limit=62
attempt to access beyond end of device
sda1: rw=0, want=1028, limit=62
UDF-fs: No partition found (1)
attempt to access beyond end of device
sda1: rw=0, want=66, limit=62
isofs_fill_super: bread failed, dev=sda1, iso_blknum=16, block=32
attempt to access beyond end of device
sda1: rw=0, want=65602, limit=62
HFS+-fs: unable to find HFS+ superblock
attempt to access beyond end of device
sda1: rw=0, want=65602, limit=62
VFS: Can't find a HFS filesystem on dev sda1.
VFS: Can't find ext3 filesystem on dev sda1.
VFS: Can't find ext2 filesystem on dev sda1.
attempt to access beyond end of device
sda1: rw=0, want=130, limit=62
ReiserFS: sda1: warning: sh-2006: read_super_block: bread failed (dev sda1, block 64, size 1024)
ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
XFS: bad magic number
XFS: SB validate failed
attempt to access beyond end of device
sda1: rw=0, want=72, limit=62
attempt to access beyond end of device
sda1: rw=0, want=128, limit=62
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sda2.
UDF-fs: No VRS found
Unable to identify CD-ROM format.
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sda2.
VFS: Can't find ext3 filesystem on dev sda2.
VFS: Can't find ext2 filesystem on dev sda2.
ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
XFS: bad magic number
XFS: SB validate failed
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sda3.
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.
HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

After this occurs a nautilus browser window automatically pops up pointing to /media/sda3. The ipod goes into "Do not disconnect" mode. I am able to browse the ipod directory structure via this nautilus window (Calendar, Contacts, iPod_Control, Notes).

Have not had much success with gtkpod. From browsing google it seems clickwheels (4th gen) along with mini's have issues in linux due to a CONFIG_EFI_PARTITION option in kernels that causes the device to return incorrect number of blocks, and not allowing it to be mounted. However mine obviously does mount. Secondly, looking at the config-2.6.1.8-4-386 in /boot shows that CONFIG_EFI_PARTITION is not set.

Anybody had success with an 4th gen ipod or mini on ubuntu warty? I could upgrade to hoary if will help.

Gol

---

### Post by dgantony on 2004-12-26
I think the ipod needs to be formated as vfat. I have the same 4th gen ipod formated as vfat (aka windows ipod) and it works great. Check out this [how-to](http://www.cs.duke.edu/~geha/ipod/) .

---

### Post by yoha on 2005-03-19
golovko -> visit [HOWTO: Use 4th gen. iPod (usb) with Linux](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=327)

---

