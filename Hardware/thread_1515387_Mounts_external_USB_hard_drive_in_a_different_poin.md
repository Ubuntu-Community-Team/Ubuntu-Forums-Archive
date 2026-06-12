---
title: "Mounts external USB hard drive in a different point after resuming from suspend"
date: 2010-06-22
forum: Hardware
---

### Post by rbp on 2010-06-22
On a computer with Ubuntu 9.04 and latest updates (kernel 2.6.31-22) I am getting the bug described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/230671]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/230671")

After resume from suspend, the old mount point (e.g. /media/disk) is somehow occupied and therefore the external disk has to be mounted to "disk_", if you do the suspend-resume cycle several times, there will be more "deserted" mount point, and the final one could be "disk______" (several underscore)

When I do "ls -l /media", it shows that the old mount point belongs to root.

I have only started experiencing this in the last month.
Any ideas?

---

