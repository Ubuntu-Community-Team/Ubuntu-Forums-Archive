---
title: "can not detect my drives"
date: 2009-03-18
forum: Hardware
---

### Post by chekha on 2009-03-18
hello,

it's actually regarding linux-mint.

but i try to ask here since:
- i already have an account here
- mint is based on ubuntu 

************************

i have two hard drives (250 GB) connected to a PCI raid-card.

on linux-mint 5 they are detected.

while on linux-mint 6 they are not detected for some reasons.

fdisk from mint 5: 
> 
mint@mint ~ $ sudo fdisk -l

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73677367

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       30401   244196001   83  Linux

Disk /dev/hdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8037dfe4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       30401   244196001   83  Linux

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fde642f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566   83  Linux
/dev/sda2            9404        9733     2650725    5  Extended
/dev/sda5            9404        9733     2650693+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c259cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
mint@mint ~ $



fdisk from mint-6:
> 
mint@mint ~/Desktop $ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fde642f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566   83  Linux
/dev/sda2            9404        9733     2650725    5  Extended
/dev/sda5            9404        9733     2650693+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c259cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux



any ideas? :o

---

### Post by Admiral Nesquick on 2009-03-18
What RAID card are we talking about ?

---

### Post by chekha on 2009-03-18
hello,

we are talking about this card:
HighPoint RocketRAID 100 2P ATA100

---

### Post by chekha on 2009-03-19
anyone?

---

### Post by chekha on 2009-03-20
bump

---

### Post by chekha on 2009-03-23
anyone???

---

### Post by chekha on 2009-03-25
bump

---

### Post by chekha on 2009-03-30
nobody knows? :(:confused:

---

### Post by chekha on 2009-04-01
](*,)](*,)](*,):-(:-(:frown:

---

