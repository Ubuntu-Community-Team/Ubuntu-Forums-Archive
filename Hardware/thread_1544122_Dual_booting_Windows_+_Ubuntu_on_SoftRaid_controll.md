---
title: "Dual booting Windows + Ubuntu on SoftRaid controller"
date: 2010-08-02
forum: Hardware
---

### Post by acidrop on 2010-08-02
Hello!

I have a machine with 2x1TB HDs on a Silicon Image Sil3512A adapter configured as RAID-1.
I have installed WinXp + Win7 x64 + Ubuntu 8.04 x64 on mirror set and i can boot successfully on all of them.
The only problem is that on Ubuntu GParted shows both of hard disks as sda and sdb and on Windows it just shows 1 hard disk as it should since it is a raid1 mirror set.
I suspect that the problem is that ubuntu drivers for sil3512 does not recognize correctly the mirror set but it just show them as simple disks.
I searched the forum and i found that i can use dmraid to be able to nest both hds on linux.
Is this safe? I mean if i do it i will be able to boot on all O/S without problem?
Having both softraid from sil3512 drivers on windows and dmraid on linux could generate any conflicts?


Thank you

---

### Post by ronparent on 2010-08-03
How you proceed depends on which Ubuntu release you are working with. In general when dmraid is installed you are able to work in a raid environment and see your raid drive with all its partitions as such. Exactly what it takes to install to or to mount partitions varires from release to release.

---

