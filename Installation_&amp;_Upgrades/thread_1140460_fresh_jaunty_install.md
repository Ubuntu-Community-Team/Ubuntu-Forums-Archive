---
title: "fresh jaunty install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by leemajors on 2009-04-27
i have my /home directory on a separate partition....

what's the process for installing a new jaunty onto my boot partition and making sure my /home directory doesn't get wiped?

---

### Post by lovinglinux on 2009-04-27
When you get to the partition stuff of the installation process, choose manual configuration, then click the home partition and select "Edit". Then, put "/home" in the mount point option and DON'T TICK the "format" option.

The root partition should be formated with you preferred file system and mounted as "/". You probably won't be able to edit the swap partition, but there is no need to do it, unless you want to change the size of it, then you should delete it and delete the root partition first and redistribute the free space again by creating the partitions with new sizes.

When you click next, you will be prompted to confirm. Check if the home partition is not listed in the formated partitions to make sure. It shouldn't be. At this point you still can revert the changes without wiping the drive.

---

