---
title: "Installed but lost"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by iceman_ch on 2009-01-30
I have an M1530.  I already have Vista. I resized the partition and then started with the live cd.  When it loaded up I used the manual option for the partitioning.  I created three new partitions. one for the swap one for / and the last one for grub.  I had read somewhere that if I install grub into its own partition I could avoid haveing a self destruct button and still beable to load media direct.  Well everything installed but the computer goes right into cista and dosn't give me any other options.  I know that I missed a step but, I'm not sure what step I missed because I can't find the walkthru.

---

### Post by lemming465 on 2009-02-01
When you installed grub onto a separate partition nothing was done to the MBR to point at it.  So either you have to add a linux boot option to your vista start menu, or you have to put GRUB on the MBR (master boot record, the first 443 bytes of the first disk sector).  Write back with your choice and the output from *sudo fdisk -lu; sudo blkid* from the live desktop CD, and we'll give you more particular directions.

---

