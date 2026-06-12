---
title: "Repartitioning using parted command"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-09-25
hi,
  I am using 
  $ sudo parted
command for resizing my partition I seen in my gprated tool that in the Partition tool on toolbar> resize/move option in hidden, thats why i am using this command but i am confused about 
how to use

(parted) resize number start end
command

partition      filesystem  mount point     size        sizeused   unused                  first sector lastsector
/dev/sda5  ext3             /                   13.97GiB  13.27GiB   716.62MiB           176136723 205439219
/dev/sda6  ext3             /home          45.50 GiB 18.58 GiB  26.91 GiB            205439283 300849254
/dev/sda7  linux swap                         5.59 GiB                                               300849318 312576704


please help me,I am confused regarding what should be first sector and last sector,I dont want to lose data.

---

### Post by Lars Noodén on 2009-09-25
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25)

[http://ftp.gnu.org/pub/old-gnu/Manuals/parted-1.6.1/html_node/parted_32.html](http://ftp.gnu.org/pub/old-gnu/Manuals/parted-1.6.1/html_node/parted_32.html)

---

