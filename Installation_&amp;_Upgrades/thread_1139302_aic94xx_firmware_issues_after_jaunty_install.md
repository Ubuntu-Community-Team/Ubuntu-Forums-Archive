---
title: "aic94xx firmware issues after jaunty install"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by mmontg1 on 2009-04-26
After fresh jaunty install on linux software raid /, /boot, and swap, boot fails an drops me to busybox complaining about the root device not being available.  After turning off quiet boot, I see that the aic94xx firmware is failing to load on boot with this:

aic94xx: Failed to load sequencer firmware file aic94xx-seq.fw, error -2

The firmware is in /lib/firmware, and I've manually copied it to /lib/firmware/2.6.28-*-generic and reran 'update-initramfs' on the kernel, verifying that it's adding aic94xx, and it's firmware to the initramfs.  No luck.

There are lots of mentions of this querying google, but nothing has pointed me to a solution.

This same custom built machine worked without issues with hardy, and intrepid, but after an upgrade, it fails to boot with this error.  Figured I'd backup my important data, and simply do a fresh install, but still no luck.

Any advice would be quite welcome.

Thanks

---

### Post by mmontg1 on 2009-05-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315763](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315763)

Bugged above...

---

### Post by mmontg1 on 2009-05-21
Anyone have any clues as to how this can be fixed?   Another confirmation was put into the launchpad bug, but nothing more.

Thanks

---

### Post by kylemallory on 2009-06-03
We need this fixed.  It was workable, if troublesome to configure pre-jaunty, but it seems to be outright broken now.

---

