---
title: "External USB LaCie Hard drive not mounting"
date: 2008-09-15
forum: Hardware
---

### Post by Netsurfer38 on 2008-09-15
I have an external **LaCie d2 Big Disk with triple interface**. The unit consists of 2 x 250 gb disks.

Under Ubuntu 6.06 LTS I had no problem, the drive would mount automatically.

At the moment I am using Linux Mint 5, one can see the drive when opening Computer, but I am unable to mount it. The same goes for Linux Mint 4 and Ubuntu 8.04.

What has changed?

When trying to mount it I get the following:
```
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```


One I thing that I noticed with Ubuntu 6.06 is that on boot up it would show **Start Raid..................................OK**

---

