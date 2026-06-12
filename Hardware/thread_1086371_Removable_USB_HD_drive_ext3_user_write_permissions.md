---
title: "Removable USB HD drive ext3 user write permissions"
date: 2009-03-03
forum: Hardware
---

### Post by sb73542 on 2009-03-03
Hi,

How are you supposed to set regular user write permissions on an external hard drive formatted with ext3?  It automounts, but as read-only for regular user.  You can't just change chown or chmod the /media/DEVICE-NAME directory, because that directory is dynamically created by udev every time you re-plug the device.

Thanks!

---

### Post by x22 on 2009-03-04
when a USB HD connects to this system, it is known
as /dev/sdd, with partitions such as /dev/sdd1. /dev/sdd2, etc.

personally, I mount those myself--usually on /mnt--and then
if I wanted users to have write permission, as root I'd say

"chmod a+w /mnt"

tho I don't want to do this.

---

### Post by sb73542 on 2009-03-04
> **x22 said:**
> when a USB HD connects to this system, it is known
as /dev/sdd, with partitions such as /dev/sdd1. /dev/sdd2, etc.

That's part of the problem, if I have different USB HD formatted with different file systems, whichever one is first plugged into the system will be /dev/sda1, and the second will be /dev/sda2, and it doesn't take into account the filesystem.

---

