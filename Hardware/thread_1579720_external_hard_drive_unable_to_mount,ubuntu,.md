---
title: "external hard drive unable to mount,ubuntu,"
date: 2010-09-22
forum: Hardware
---

### Post by BAB SWAIN on 2010-09-22
hi
 i am unable to mount my transcend 320 GB external hard drive. when i am trying to mount ,i am getting msg like 
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=6 count=1 br=-1: Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
i am expecting some suggestion and help from the community
Thank you

---

### Post by mikewhatever on 2010-09-22
> un chkdsk /f on Windows
then reboot into Windows twice

There are errors in the file system, and doing the above will try fixing them.

---

