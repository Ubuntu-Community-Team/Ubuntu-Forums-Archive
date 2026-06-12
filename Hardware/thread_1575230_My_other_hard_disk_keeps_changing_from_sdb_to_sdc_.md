---
title: "My other hard disk keeps changing from sdb to sdc at each boot-up on ubuntu - Help!"
date: 2010-09-15
forum: Hardware
---

### Post by bergqvistjl on 2010-09-15
Hi, basically I am trying to configure a SATA drive (i'm using AHCI for the sata drive, but my ubuntu install is on an IDE drive), but unfortunatley ubuntu never assigns it the same ID, its either sdb, or sdc. (I have another sata drive plugged into my system as well which i'm not using with ubuntu). The letter changes at each boot-up, so i can't specify the disk to always mount on startup, because the drive letter is different every other time. I think its because i've enabled AHCI for my sata disks, although I installed ubuntu with AHCI active for the SATA disks anyway. Is there anything i can do, without taking AHCI off or having to mount it manually? Its an ntfs drive i want to mount, and i'm using ntfs-config to do it for me. all that doesnt work is that the drive ID changes on each bootup.

---

### Post by arrange on 2010-09-15
Use UUID od LABEL instead.
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

