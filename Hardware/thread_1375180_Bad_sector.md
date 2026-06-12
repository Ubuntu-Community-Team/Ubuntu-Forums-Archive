---
title: "Bad sector"
date: 2010-01-07
forum: Hardware
---

### Post by ska050791 on 2010-01-07
I am using ubuntu 9.10
and my disk utility says that i have bad sectors. i have 2 bad sectors under the id number 197 called current pending sector count. how can i fix this  error?

---

### Post by MooPi on 2010-01-07
Ubuntu comes with files system checking utilities, e2fsck, mke2fs, and tune2fs, & dumpe2fs, chattr, and lsattr. I've used e2fsck but am not familiar with the others. Man pages should illuminate you to there potential. You will need to use a live Cd to use these utilities. Boot in a live CD session the open a terminal.  > sudo e2fsck /dev/sda1 /dev/sda1 representing the drive you want checked.

---

