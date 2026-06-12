---
title: "Error when trying to mount a USB Drive"
date: 2009-04-04
forum: Hardware
---

### Post by Ranger1230 on 2009-04-04
When I try to mount my USB flash drive I get the error:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

it works fine with windows so I know the drive itself is fine.

---

### Post by taurus on 2009-04-04
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
p.s.  Did you use the _safely remove hardware_ option (lower right corner) to unmount it first before you unplugged it the last time you used it in windows?

---

### Post by Ranger1230 on 2009-04-04
I get:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0a2c9a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         972     7801856   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         972       22753   174953648    7  HPFS/NTFS
/dev/sda3           22753       27852    40958972    7  HPFS/NTFS
/dev/sda4           27852       30402    20480000+   f  W95 Ext'd (LBA)
/dev/sda5           27852       30402    20480000   83  Linux

Disk /dev/sdb: 32.3 GB, 32346472448 bytes
255 heads, 63 sectors/track, 3932 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x015285dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3933    31588320+   c  W95 FAT32 (LBA)


and no I did the eject on windows
Safely removing did nothing different

---

