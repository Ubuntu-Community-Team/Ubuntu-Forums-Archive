---
title: "Lost my hard drives"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Pakia on 2009-05-31
I have a machine with 3 hard drives my OS (9.01 server with xubuntu desktop) runs of a 20GB (sda1) on IDE1 socket. The other 2 drives are both 250GB being sdb1 and sdc1 respectively running on socket IDE2 in parallel while i use a flash disk sdd5 for swap. All was working well when in the ex3 format. I tried to create RAID1 for sdb1 and sdc1 using the live CD and have lost both sdb1 and sdc1. I tried using the live cd to re format but it cannot find the two hard drives. have tried gnome patrition editor, startup manager, storage device manager as well as LVM and kgrub editor but not one of them identifies the two hard drives. I reset my CMOS and ensured the IDE controller is active. I have tried installing another HD (in the place of sda1) with ubuntu 8.01 which also cannot find the two hard drives (which says to me it is not a setting in my OS). I disconnected the two drives and hot reconnected but still they are not picked up. When I  list my hardware the 2 drives are not seen. Both HD are new and where working fine when in the ex3 format. any advice will be appreciated and thanks in advance

---

### Post by Pakia on 2009-05-31
Fixed!
Had to uninstall the two drives connect it by usb to another machine and reformatted to ext3. Bit of a long way round but i can get back to giving RAID1 a go.

---

