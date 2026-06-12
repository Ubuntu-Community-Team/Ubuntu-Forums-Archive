---
title: "partitioner shows no partitions"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Nycticorax on 2009-02-12
I'm trying to install ubuntu onto a machine which currently has Windows.
However when I start the install process from CD, the partitioner starts up but does not display any partitions.

Furthermore, I have a pseudo-Ubuntu / Ubuntu Live living on my windows partition which appears at the boot menu as unetbootin. That runs OK, and when I run gparted from within ubuntu live, it does show the two windows partitions:

/dev/sda1 ntfs    [main windows partition]
/dev/sda2 fat32   [this is some sort of windows back-up partition, known as D: from within windows where it is inaccessible/heavily guarded]

I need to create a partition in /dev/sda1 for ubuntu. However /dev/sda1 comes up as mounted at /cdrom, and I can not unmount it (it says media in use). I believe that unmounting it is the first step towards creating a partition in it.

What can I do, short of using partition magic from within windows?

Thanks,

Dan

---

### Post by Pumalite on 2009-02-12
Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

