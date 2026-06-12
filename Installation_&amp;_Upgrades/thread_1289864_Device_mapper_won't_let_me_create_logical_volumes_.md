---
title: "Device mapper won't let me create logical volumes on my raid server."
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2009-10-12
```
lvcreate --extents 100%FREE raid5
  device-mapper: reload ioctl failed: Invalid argument
  Aborting. Failed to activate new LV to wipe the start of it.
```

I tried installing ubuntu 9.04 i386. I upgraded both mdadm and lvm2. Same result:
Pls Help.

---

### Post by u-slayer on 2009-10-12
Solved. Solution here --> [http://ubuntuforums.org/showthread.php?t=1289094]("http://ubuntuforums.org/showthread.php?t=1289094")

---

