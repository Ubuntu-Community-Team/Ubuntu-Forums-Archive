---
title: "Grub 2 Probe Auto Problem"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by mhbell on 2009-11-03
I installed grub2 1.96 on my Ubuntu 9.04 which is sda (hd0) I then installed Ubuntu 9.10 on another HD with a /boot partion that drive is now sdb (hd1) the /boot partion is the first partition on that drive. I want to use the Grub2 on sda to boot  9.10 on sdb. the root for 9.10 is sdb5. I run the update-grub and it finds all of the drives but does not put a entry in grub.cfg. it finds root which is sdb5 but the /boot is sdb1 also grub2 is installed to the mbr of sdb.

another problem is when I run update-grub it makes a new grub.cfg.new it does not change the current grub.cfg I then have to go in and rename the grub.cfg files for changes to take place. no big deal except it does not put the drive that has 9.10 in it.
I have read and read and downloaded and printed documents out about grub 2 but still can't get it to work.
any help would be appreciated
TIA
Mel

The Problem is solved and all is working well. Had to put another entry in the /boot/grub/device.map file. (hd1)  /dev/sdb
Mel

---

