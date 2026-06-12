---
title: "Software Raid and OS re-install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ant2ne on 2009-04-27
I had this system failure, [here]("http://ubuntuforums.org/showthread.php?t=1137838"). I'm afraid I'm going to have to re-install my OS.  I'm using software RAID as described, [here]("http://advosys.ca/viewpoints/2007/0/setting-up-software-raid-in-ubuntu-server/"). And, [here]("http://ubuntuforums.org/showthread.php?t=725448&highlight=raid").

My question is, when I re-install the OS will I need to use the alternate installer disk? Will I need to set up the RAID array again? Or will the partitions remain and I just install to MD2 again?

---

### Post by josno on 2009-04-28
You will definitely need the alternate CD if you want to use RAID again. You'll probably find that your MDs persist, but at worst you'll just have to recreate them - your partitions on your physical disks will definitely persist.

A word of warning though - many people (myself included) seem to be having issues with RAID in 9.04. Just search 'raid' in the Installation and Upgrades forum...

---

