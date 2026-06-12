---
title: "New Hard Drive Installation"
date: 2011-06-26
forum: Hardware
---

### Post by Iqbal_ on 2011-06-26
Hi,
I have to install a new hard disk of 500 GB on my laptop. I have to install Vista and Ubuntu thereon.

Please tell me, how to make partitions and install both OS on the disk.

---

### Post by An Sanct on 2011-06-26
Hi,

You could boot into the Ubuntu Live CD and from there create two partitions on that disk, both unformatted. From there make sure to **install Windows FIRST** and to the first partition. When Windows installation is finished, install Ubuntu, this way the two OSes will not have a fight.

---

### Post by grahammechanical on 2011-06-26
After installing Ubuntu run the live CD again and use the partitioner program to look at your partitions. You will see that the Ubuntu install process has created an Extended partition and in that partition a logical partition has been created that is called swap.

You might want to create a separate partition as your /home partition. Then if you need to re-install Ubuntu you will not loose your data.

1) Shrink the Ubuntu partition to create unused space.

2) expand the extended partition to use up the unused space.

3) create an new logical partition in the unused space.

4) reinstall Ubuntu to tell Ubuntu it now has a /home partition and not a /home folder. Mark the Ubuntu partition to be mounted as /.    Mark the new logical partition to be mounted as /home. Both can be marked to be formatted. Mark the swap partition to be mounted as swap.

As you are not yet using Ubuntu and so you do not have any data to loose, you can learn how to partition. All you loose is some time but you gain experience.

Regards.

---

