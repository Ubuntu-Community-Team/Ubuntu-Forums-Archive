---
title: "Ubuntu 16.04 LTS will not detect my CD/DVD drive"
date: 2016-05-28
forum: Hardware
---

### Post by b_g2 on 2016-05-28
I cannot get Ubuntu 16.04 LTS to detect my internal CD/DVD drive. The drive model is TSSTcorp CD-RW/DVD-ROM TSL462D. The drive is receiving power and shows up in BIOS, but for some reason does not show up in Ubuntu. Any help will be appreciated.

---

### Post by Frogs Hair on 2016-05-29
Hello and Welcome b_g2

Is the drive missing from the Disks application ?

---

### Post by houstonbofh on 2016-05-30
Install lshw-gtk and run it with sudo. Now walk down the tree and see if you can fine the drive.

---

