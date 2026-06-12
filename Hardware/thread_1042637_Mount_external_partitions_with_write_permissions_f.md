---
title: "Mount external partitions with write permissions for user"
date: 2009-01-17
forum: Hardware
---

### Post by rvbhute on 2009-01-17
I plan to create and use a 500GB USB external drive formatted to JFS. I am experimenting with a 2GB flash drive atthe moment :) .

The drive automounts perfectly. However I (as a normal user) cannot create directories/files on the drive. 

How do I set the JFS formatted drives to mount with permissions for normal user to write files - so that it behaves like a FAT32 formatted drive?

---

### Post by rvbhute on 2009-01-18
[http://reactivated.net/writing_udev_rules.html#ownership](http://reactivated.net/writing_udev_rules.html#ownership)

I added a udev rule as specified in the article above.

```
KERNEL=="sd?1", SUBSYSTEMS=="scsi", ATTRS{vendor}=="SanDisk", ATTRS{model}=="U3 Cruzer Micro", OWNER="username"
```

---

