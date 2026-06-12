---
title: "this dd command writes 0 bytes -- why?"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-02-28
```
dd if=/dev/null of=/dev/sdX bs=446 count=1
```I want to remove grub from a drive while leaving the partition table in place.

when I run this on sda, dd reports 0 bytes out. I can't figure out why.

what is the right way to use this command (or similar) to remove grub?

Reference: [http://ubuntuforums.org/showthread.php?t=641665](http://ubuntuforums.org/showthread.php?t=641665)

UPDATE: sda is a SCSI hardware RAID array. Ubuntu sees it as a single disk.

---

### Post by amauk on 2009-02-28
you can't read from /dev/null
you can only write to it (and all writes are discarded)

I really don't think this is a safe thing to do, but use /dev/zero instead to write null bytes

---

### Post by MountainX on 2009-02-28
Perfect! That was the fix I needed. Thank you.

---

