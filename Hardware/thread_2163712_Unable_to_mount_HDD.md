---
title: "Unable to mount HDD"
date: 2013-07-19
forum: Hardware
---

### Post by SMOKE5 on 2013-07-19
I recently upgraded to Ubuntu 13.04 (or whatever the latest is) and when I plugin my external HDD, I get an error message:
```
Error mounting /dev/sdb at /media/smoke/SMOKE's HDD: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb" "/media/smoke/SMOKE's HDD"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```
This HDD mounts properly to my Windows PC, Im even able to transfer files.
Does anyone have an idea how to solve this?

---

### Post by dino99 on 2013-07-19
[http://wmarkito.wordpress.com/2010/12/29/how-to-fix-mftmirr-does-not-match-mft-record-0/](http://wmarkito.wordpress.com/2010/12/29/how-to-fix-mftmirr-does-not-match-mft-record-0/)

---

### Post by sudodus on 2013-07-19
.

---

### Post by SMOKE5 on 2013-07-19
> **dino99 said:**
> [http://wmarkito.wordpress.com/2010/12/29/how-to-fix-mftmirr-does-not-match-mft-record-0/](http://wmarkito.wordpress.com/2010/12/29/how-to-fix-mftmirr-does-not-match-mft-record-0/)

Thanks man, that fixed it

---

