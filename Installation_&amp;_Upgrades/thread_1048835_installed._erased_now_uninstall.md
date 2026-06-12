---
title: "installed. erased? now uninstall"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by luckymoonboy1 on 2009-01-23
ok, several things, i installed ubuntu 8.04 over a virus infested, crashed, windows xp system i now need to use the drive as a slave drive for another xp computer. does ubuntu erase EVERYTHING? i need to know if this drive could pose a system security problem. and i also want to remove ubuntu and ALL data on the hard disk so that is a bare bones slave drive, how do i do this?

---

### Post by taurus on 2009-01-23
Boot from Ubuntu LiveCD.  Use gparted in System -> Administration and delete all the partitions on the drive.  Then, create one partition that take up the whole harddrive and format it to ntfs.  Now, windows should be able to read that drive.

---

### Post by luckymoonboy1 on 2009-01-24
THANKS!!! :p:p

---

