---
title: "/dev/sda1 100% - mySQL and other services failing"
date: 2008-11-04
forum: General Help
---

### Post by Fynn on 2008-11-04
Hi,

My Ubuntu server (8.04) is having multiple problems (CUPS, mySQL, Apache, BlueDragon, SlimServer all failing)

/dev/sda1 (boot partition) shows 100% use (7GB) so I'm thinking this could be the problem.

Still kinda new to all this and would appreciate any ideas as to how to resolve.

Thanks

---

### Post by Coreigh on 2008-11-04
Yes if the disk /dev/sda1 is full and is the / partition or is any partition used by any process or part of the OS then the system will quickly become almost unusable. One possible short cut is to move or delete some files to another disk or external drive. However 7GB is pretty small these days, its time to upgrade.

---

### Post by Fynn on 2008-11-04
Thanks,

---

