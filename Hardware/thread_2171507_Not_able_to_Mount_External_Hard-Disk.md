---
title: "Not able to Mount External Hard-Disk"
date: 2013-08-31
forum: Hardware
---

### Post by 7Starphy on 2013-08-31
I am using Ubuntu 12.10 , it is not mounting one of my External Hard Disk. I get the following error

 ```
Error mounting /dev/sdc1 at /media/gyroscope/Elements: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdc1" "/media/gyroscope/Elements"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output errorFailed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

Can anyone help me out here ?

---

### Post by sudodus on 2013-08-31
1. Have you got or can you borrow a Windows computer to run the command that is recommended?

```
chkdsk /f
```

2. Do you have RAID or has there been RAID on the drive or is it some kind of hybrid SSD + HHD drive, which uses RAID under the hood?

---

