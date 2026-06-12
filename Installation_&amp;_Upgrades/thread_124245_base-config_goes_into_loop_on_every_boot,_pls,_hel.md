---
title: "base-config goes into loop on every boot, pls, help!"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by niceTry100 on 2006-02-01
After I installed Ubuntu 5.10 from CD, every time, my system boots, base-config keeps trying to install sql-common package, then finds dependency problem and gives "was a problem installing selected software" message. After I hit OK, everything repeats again. Here is the message from tty4:
"The fillowing packages have unmet dependencies:
mysql-common: Conflicts: mysql-common-4.1 but 4.1.12-1ubuntu3.1 is installed
mysql-common-4.1: Conflicts: mysql-common but 4.0.24-10ubuntu2 is to be installed".
Is there anything I could use to clean this mess?
If I run "base-config" manually from another console, the loop stops, but after reboot, it appears again! I tried to uninstall sql-common completely from "dselect", but it returns again!

---

