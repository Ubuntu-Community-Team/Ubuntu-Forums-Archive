---
title: "help on setting up my system.."
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by theromanone on 2009-02-25
Hi there, basically just want to have a fresh hard drive as both windows and ubuntu have major problems as of now. I have 3-4 partitions, and have all my files on DVD's, with a windows xp 64-bit and ubunti 8.10 installation disks.

Question is how could I just go to my original hard drive, could I just write zero's to the whole drive with BIOS to delete all partitions and make one single empty "partition"?

My goal is to eventually have that one drive, and then  install ubuntu on a 10GB Partition, afterwards install XP on another 5-10GB partition, and have a third partition for files (music, movies, documents).

Thanks!

---

### Post by taurus on 2009-02-25
Boot with Ubuntu LiveCD.  Then open gparted, System -> Administration -> Partition Editor, and delete all the partition.  If you see a keys in front of the swap partition, click the partition with the right button and run swapoff.  Then, you can delete everything and repartition whichever way you want.  If you want to reinstall windows on the first partition, make sure you format that to ntfs or windows won't be able to detect it.

---

### Post by theromanone on 2009-02-25
thanks!

---

