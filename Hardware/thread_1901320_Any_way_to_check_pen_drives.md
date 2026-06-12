---
title: "Any way to check pen drives?"
date: 2011-12-28
forum: Hardware
---

### Post by Jayhawker on 2011-12-28
I've a pen drive which unexpectedly doesn't work no longer. Please, is there any way in Linux Ubuntu to check this pen in order to solve the problem? 

Thank You

---

### Post by utnubuuser on 2011-12-28
Places, maybe? (Nautilus)
or,
In terminal: lsusb, then: cd /dev/sdX, (X being letter of drive found with lsusb
or,
In terminal: lsusb, then: cd /media/sdX, (X being letter of drive found with lsusb
or
In terminal: blkid, then: cd /dev/XXXXXXXXXXXXXXXXX (X=uuid found with blkid)
or,
In terminal blkid, then: cd /media/XXXXXXXXXXXXXXXXXXX (X=uuid found with blkid)
or use gparted to have a look at the drive... (sudo apt-get install gparted, then System>>Gparted

---

