---
title: "Can not upgrade to Ubuntu 8.10"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by scottym on 2009-04-28
First of all my cdrom is malfunctioning and so I can not do the upgrade using a disk. I have been trying to upgrade using update manager but it keeps failing because there is not enough disk space. my df -h is:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.2G  3.2G  799M  81% /
varrun                311M  112K  311M   1% /var/run
varlock               311M  4.0K  311M   1% /var/lock
udev                  311M   44K  311M   1% /dev
devshm                311M  100K  311M   1% /dev/shm
lrm                   311M   40M  272M  13% /lib/modules/2.6.24-24-generic/volatile
/dev/sda2             122M   95M   22M  82% /boot
/dev/sda1              14G  2.3G   11G  18% /home

I have cleaned up my file system but it does not have any effect on the /dev/sda3 which is where my Ubuntu os is and when it is in the upgrade process it stops because there is not enough room on the disk. I have not encountered this before when using the same procedure for upgrading. In fact I last upgraded to Hardy using this method. Anyone have any ideas on what to do? Are there files I can erase from the / area of my drive? I need about 122 megs if memory serves.

Thanks everyone.

---

### Post by emusbau on 2009-05-22
Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Software Sources
          *

            intrepid_upgrade1.png
   2. click on the "Updates" tab and change "Show new distribution release" to "Normal releases"
          *

            intrepid_upgrade2.png
   3. Start System/Administration/Update Manager
          *

            intrepid_upgrade2.5.png
   4.

      Click the Check button to check for new updates.
   5.

      If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   6. A message will appear informing you of the availability of the new release.
          *

            update-manager-upgrade-810.png
   7.

      Click Upgrade.
   8. Follow the on-screen instructions.

---

### Post by scottym on 2009-05-23
Please reread my message as what you recommend is exactly what I have tried and it does not work at present.

---

