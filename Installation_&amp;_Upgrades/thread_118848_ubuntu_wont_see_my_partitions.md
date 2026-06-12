---
title: "ubuntu wont see my partitions"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by time_shift on 2006-01-17
ubuntu wont see my partitions on my 160gb disc and partition magic says its bad and that my partions are out of range or something

---

### Post by Sef on 2006-01-17
A) Have you tried from the terminal:  sudo fdisk -l?

B) Use the Ubuntu Live CD and see if you can see your partitions.  

    -) Applications ----> System Tools ----> GParted

C) Did you use Partition Magic to make the partitions?  

     1) Partition Magic does not always make Linux partitions well.  There have                  been written numerous posts about it.

     2) Use GParted from the Live CD to fix your paritions. 

     3) Download a rescue CD from FrozenTech:  [http://www.frozentech.com/content/livecd.php?pick=Linux_x86&showonly=Rescue&sort=&sm=1]("http://www.frozentech.com/content/livecd.php?pick=Linux_x86&showonly=Rescue&sort=&sm=1")

---

