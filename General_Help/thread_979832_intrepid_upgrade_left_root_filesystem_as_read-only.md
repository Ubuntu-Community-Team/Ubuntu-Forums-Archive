---
title: "intrepid upgrade left root filesystem as read-only"
date: 2008-11-12
forum: General Help
---

### Post by maestrobwh1 on 2008-11-12
My upgrade froze before "cleanup" and I rebooted into recovery and ran 

dpkg --configure -a and then was able to boot to my desktop.

I get a failed boot from the normal boot option where grub runs the splash: something about /tmp/.clean cannot be deleted because the filesystem is mounted read-only.

**I can get get a complete boot if I choose the _recovery mode_ and then just "resume"**

I also ran fsck on the root filesystem in recovery mode to make sure there were no errors.  There are none and I even used the -v flag.

The entry for fstab for my root filesystem is:

uuid=(my uuid) / ext3 defaults,errors=remount-ro,noatime 0 1

There are other entries for other partitions but they seem to be mounted fine and they are ntfs and swap.

I upgraded my laptop with no issue, and this is also the line in my laptop fstab as well.

There is a bug filed on this, but there is no "solution" listed.

Aside from changing errors=remount-ro to errors=continue which in the event there is a filesystem error in the future, I could end up with further damage.

Any ideas?

---

