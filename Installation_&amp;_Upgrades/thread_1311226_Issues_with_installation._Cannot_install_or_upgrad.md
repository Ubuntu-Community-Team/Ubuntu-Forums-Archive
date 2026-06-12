---
title: "Issues with installation. Cannot install or upgrade."
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by k3mist on 2009-11-02
Fairly disgusted and disappointed with Karmic.

For starters, it will not upgrade from 9.04. Kept giving me a 404 for two of the software locations when updating the package lists during the upgrade and reverts back. Even after several reboots, deleting list cache, etc.

Downloaded and burned the live CD. Just additional problems.

On my desktop, I have 4 drives all on the same sata2 controller, nvidia raid controller which is disabled in the bios and set to work as standard ide. There is another gigabyte raid controller on system but nothing is connected to it.

2 of the drives are identical model 250gb and the other 2 drives are identical 200g. Jaunty sees sda1 (250gb) as my winxp installation which is just used for gaming only. sdb1 (250gb) is the jaunty installation. sdc1 (200gb) is ntfs and used for storage. sdd1 (200gb) is ext4 and used for storage.

During the installer or live cd of Karmic, it see's sda1 as ntfs and it groups sdc1 and sdd1 together as a 400gb raid array, which is obviously disabled in the bios. It does not see sdb1 at all. 

HOWEVER, gparted in Karmic live cd see's each drive as it should. I used gparted to format and redo the partitions on sdb1. Ran the installer and still does not see it. Rebooted and still does not see it. Took the machine down (disconnected power). Disconnected every drive but sdb1. Gparted in karmic now sees sdb1 as sda1 however still does not see the drive during the installer.

So there is clearly a huge issue in Karmic. 

#1. Why is software raid initialized when it's clearly disabled in the bios.
#2. Why is the karmic installer refusing to see this drive when gparted has zero issue with the drive, formatting, setting partitions sizes, etc?

---

