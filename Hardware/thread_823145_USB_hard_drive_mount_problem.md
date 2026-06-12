---
title: "USB hard drive mount problem"
date: 2008-06-08
forum: Hardware
---

### Post by trorion on 2008-06-08
OK, I messed up trying to get my USB drive writeable and tried to change the some settings.  Now my USB hard drive won't mount it gives me an error:
mount_point cannot contain the following characters: blah blah blah.

Problem for me is that it doesn't show the drive in mstab or fstab.
Where are the settings saved on USB and removable media?

Thanks!

dmesg|tail
```

-laptop:~$ dmesg|tail
[ 1459.677318] sd 8:0:0:0: [sdb] Write Protect is off
[ 1459.677323] sd 8:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1459.677326] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1459.678910] sd 8:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1459.679719] sd 8:0:0:0: [sdb] Write Protect is off
[ 1459.679722] sd 8:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1459.679724] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1459.679730]  sdb: sdb1 sdb2 sdb3 sdb4
[ 1459.702646] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 1459.702691] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

---

