---
title: "server 8.1 minstall fail at disk detect/partition"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by tmoble on 2009-02-21
Hi All

single SATA disk set up in BIOS as IDE, not RAID. BIOS identifies disk correctly.  When the install gets to the disk detect section it claims to find one or more  drives containing SATA RAID configurations.  Wants to know if I want to activate these RAID devices.  If I choose Yes it fails the disk detect step and gives option to try again or do something else.  try again and choose no to activate SATA RAID devices it goes to the partition screen.

In the partition section it shows the screen as usual but the partitioning choices are missing.  It has a line "Help on partitioning" then two blank lines, then "Undo changes to partitions" then "Finish partitioning and write changes to disk."  scroll up and down the choices with up and down arrow keys works, but the blank lines remain blank.  If I chose the Finish partitioning option it complains about no root partition being defined.

I tried changing the BIOS to use the RAID option but that fails as there is only one disk.

It's weird because I had this system set up using this disk before, worked fine.

It's an ECS board with quad AMD and 4GB.

Any bright ideas?  I thought about booting with the GPARTD live disk and partitioning it that way but it really doesn't address the issue.  Any help appreciated.

---

### Post by tmoble on 2009-02-21
any help out there?  post already to the bottom of the second page.

---

