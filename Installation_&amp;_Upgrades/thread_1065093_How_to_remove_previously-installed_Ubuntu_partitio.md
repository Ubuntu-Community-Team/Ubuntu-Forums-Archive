---
title: "How to remove previously-installed Ubuntu partitions"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by yankeeDDL on 2009-02-09
Hello again ...

after trying to fix my Ubuntu installation I decided to re-do it from scratch.
Inserter the CD and followed the normal installation flow.
When the installation completed I noticed that I have now 3 partitions on my drive:
- Windows XP (the "old" partition)
- Ubuntu 1st installation (corrupted: I want to delete it together with the corresponding swap)
- Ubuntu 2nd installation (clean: want to keep it).

Needless to say, I want to delete the "Ubuntu 1st installation" (both remove the partition and cleanup the Grub).
Would be nice to know also for when I get rid of Windows XP (I have installed VirtualBox on Ubuntu for those Win SW for which I can't find an equivalent in Linux).

I'm sure many have made the same mistake when re-installing ...

Thanks in advance!

---

### Post by Pumalite on 2009-02-09
Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Follow the Documentation:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by yankeeDDL on 2009-02-10
I will try. Thank you for the help.

---

### Post by yankeeDDL on 2009-02-10
> **Pumalite said:**
> Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Follow the Documentation:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Pumalite, one more question: how do I cleanup the Grub?
sudo gedit /boot/grub/menu.lst  ????
Or is there a more ... orthodox way?

---

### Post by Pumalite on 2009-02-10
You can fix your Windows MBR with your Installation Disk
You can also use Super Grub
You can have a new Grub by using available space and installing Ubuntu (Jaunty maybe)

---

### Post by yankeeDDL on 2009-02-10
I don;t really need to "fix it": if I manually delete the partitions by using Gparted, Grub will still list those partitions at startup.
So -I suppose- I will need to delete the corresponding entries from Grub manually as well.

---

