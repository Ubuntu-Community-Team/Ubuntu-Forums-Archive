---
title: "Error for mountuing"
date: 2016-05-28
forum: Hardware
---

### Post by v6rg2 on 2016-05-28
I have problem with my external Hard (Western Digital). I cant open it in Ubuntu 16.04
This is the error:

```
Error mounting /dev/sdb1 at /media/v6rg/v6rg: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/v6rg/v6rg"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.
```

---

