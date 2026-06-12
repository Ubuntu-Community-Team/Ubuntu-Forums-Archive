---
title: "Mount error with code 13"
date: 2011-01-15
forum: Hardware
---

### Post by The Alby87 Project on 2011-01-15
Hi! I've a problem with my hard disk.

I've searched, maybe you can help me :)

I've my hard-disk partioned with 4 partition: 1 NTFS with W7, 1 NTFS for Data, 1 Ubuntu 10.10 and one Linux Swap.

When I was using W7, I had a BSOD, and PC shutted down. Now W7 won't start. Ubuntu won't mount with this error:

ntfs_attr_pread_i: ntfs _pread failed: Input/output error
Failer to read of MFT, mft=6 count=1 br=-1; Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda1': Input/output error

etceters

I've tried to start Windows 7 Installation to go to the recovery console, and CHKDSK /F C: it's extremely slow to go to the first phase (saying that the file system is NTFS), and the first phase itself it's really slow. After some error on first blocks, it freezes, and won't move. It saying that some blocks are bad, first of wich is 6 (similar to mft=6)

Testdisk says Boot sector and backup boot sector are both OK, when I select repair MFT it says "Can't read NTFS MFT"

Rebuild BS freeze TestDisk, alà CHKDSK from W7 DVD

I've done a backup of NTFS data, and Ext4 Partition, but my W7 partition would be very nice to recovery, at least for my emails.

Thank you in advance ;)

The Alby87 Project

---

