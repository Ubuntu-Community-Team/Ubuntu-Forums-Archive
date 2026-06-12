---
title: "cdrom mounts under username in media"
date: 2013-03-27
forum: Hardware
---

### Post by EAZ on 2013-03-27
I've got this irritating "bug" which mounts all my portable drives (CD, USB, DVD) under /media/username/drivename

Since i bought CrossOver for Ubuntu Linux, the program CrossOver does not find my cdrom, because it's simply not under /media/cdrom, but it's under /media/username/cdrom...

Can anybody help me with this annoying bug?

---

### Post by Toz on 2013-03-27
It's not a bug, it was a change made by udisks2 and further modified by ubuntu. See [here]("http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location") for more info plus a possible solution (Florian Diesch's suggestion).

More info in this bug report: [https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1020759]("https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1020759").

---

