---
title: "External HDD fails to mount after power failure"
date: 2014-09-08
forum: Hardware
---

### Post by linsey-young on 2014-09-08
Hi - I am having issues with an external drive after the power was interrupted on the machine which was transferring data to it. When I try to mount it I get the following dialogue:

Error mounting /dev/sdc1 at media/linsey/Elements: Command-line mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,dmask=0077,fmask=0177" "/dev/sdc1" "/media/linsey/Elements" exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).

---

### Post by yancek on 2014-09-08
It's a windows filesystem so I would start with running chkdsk from windows on that partition or try googling the error:  $MFTMirr does not match $MFT (record 0).

---

