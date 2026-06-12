---
title: "Deleting vista partition"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by cnkt on 2009-01-05
My Windows Vista is on my first partition and ubuntu is on second.

Now, i want to wipe out Windows Vista and just use Ubuntu. How can i delete Vista partition (not just Vista, also the partition) and make my hdd with only 1 partition which is ubuntu?.

thanks.

---

### Post by Mark Phelps on 2009-01-05
Several ways to do this ...

One is to boot using the LiveCD, start the partition manager, and do the following:
1) Delete the Vista partition
2) Resize the Ubuntu partition to use the free space

If you're using GRUB to boot into Ubuntu and Vista, you will need to modify the /boot/grub/menu.lst file to:
1) remove the Vista stanza
2) change the Ubuntu stanzas so they point to the first partition on the drive.

Thus, if your Ubuntu stanzas now say (hd0,1), you will want to change them to say (hd0,0).

---

