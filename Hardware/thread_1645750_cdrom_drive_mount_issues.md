---
title: "cdrom drive mount issues"
date: 2010-12-15
forum: Hardware
---

### Post by tock on 2010-12-15
I've seen this problem on other posts but never a fix that works for me.  If I boot Ubuntu 10.04 with a cd in the cdrom it will load with the cd accessible.  After I remove the cd and insert a new one, the cdrom icon on the desktop never updates itself.  When I click on it, it will appear to load the disk but will display a empty folder and it never searches the cdrom again.  I have 2 burners 1 serial the other ide.  Both drives have the issue.  udisk --dump shows both drives.  One on sr0 the other on sr1.  I have tried adjusting the cdrom boot order. disabling cdrom boot, removing from fstab, udisks --poll-for-media /dev/sr0.  The drive that has the cd in it when the pc boots can be manually unmounted then remounted and it will see the new cd.

---

