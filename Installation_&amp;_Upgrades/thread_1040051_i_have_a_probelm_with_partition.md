---
title: "i have a probelm with partition"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by casperon on 2009-01-15
Hello, i'm trying to join the Ubuntu family, but facing some issues.
i have 2 hard drives. one of them (500 GB) was partiotioned like this: 400Gb/100Gb. (the partiotion was made threw windows).
now, i want to install ubuntu on the 100gb part. 
on installation at the partition phase, i went with manual.
i chose the 100gb as the partiotion for the installation. and i get a prompt that say: " no root (**something**) was selcted....").
i don't want to loose the data i have on the 400gb partition.
any help would be appritiated.
thank you very much.
:guitar:

---

### Post by Tim Sharitt on 2009-01-15
When you are in the partition editor, you need to be sure to set the partiotions mount point to / and make sure to format it to a native linux filesystem (ext3 is the standard)

---

### Post by wjp.reg on 2009-01-15
if you delete the 100g partition and let ubuntu auto select that free space then you should be ok following the bouncing ball.  There are numerous guides and tutorials for installing a dual-boot windows/linux system

cheers,

wolf

---

