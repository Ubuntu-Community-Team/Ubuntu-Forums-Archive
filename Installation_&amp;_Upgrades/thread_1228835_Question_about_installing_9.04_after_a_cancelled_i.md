---
title: "Question about installing 9.04 after a cancelled install"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by sebas215 on 2009-08-01
I tried installing Ubuntu before and it stopped at 63% so I cancelled. Now when I reburned and have a good installation disk with no errors I go back to reinstall I am confused on what to do with the partitions. Before I just picked the unallocated space I made.

Anyone have any ideas.

:confused:

---

### Post by mikewhatever on 2009-08-01
You can delete the created partitions and then try the unallocated space option again. If not sure what to delete, post the output of **sudo fdisk -l** command from Applications->Accessories->Terminal.

---

### Post by starcraft.man on 2009-08-01
See the [documentation here]("http://gparted.sourceforge.net/documentation.php") to understand partitioning. If the install was interrupted midway, then those linux partitions (the EXT3/4 ones) made for the install are useless. You can either just delete them and recreate them as you like or simply edit them, and set them to be formatted. If you edit, ensure your mounting them to the correct mountpoint (i,e. at least one needs to be root, one might be home). Please see documentation for a complete explanation.

If you've any questions after reading just reply.

---

### Post by sebas215 on 2009-08-01
well under management it is called free space now. and when I right click and go to delete partition it says ( this is an extended parition if you delete it it will become inaccessible. Are you sure you want to delete it.)

Im not sure if I should delete it then

---

### Post by mikewhatever on 2009-08-01
An extended partition is just a container for logical partitions. If you don't have any logical ones, it's safe to delete it, otherwise don't.

---

### Post by sebas215 on 2009-08-01
I deleted now its just 30gbs of unallocated space perfect now i can install! thanks for the help :D

---

