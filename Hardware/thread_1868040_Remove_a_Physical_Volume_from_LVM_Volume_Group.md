---
title: "Remove a Physical Volume from LVM Volume Group"
date: 2011-10-23
forum: Hardware
---

### Post by Catalyph on 2011-10-23
I would like to remove a Physical Disk from a Volume Group that I JUST added it to. 

root@BlazenNas:/# pvdisplay
File descriptor 4 (/dev/urandom) leaked on pvdisplay invocation. Parent PID 1581: bash
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               BlazenNas
  PV Size               465.52 GiB / not usable 2.33 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               0
  Allocated PE          119173
  PV UUID               XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               BlazenNas
  PV Size               74.53 GiB / not usable 3.02 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              19079
  Free PE               2
  Allocated PE          19077
  PV UUID               XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX



root@BlazenNas:/# lvdisplay
File descriptor 4 (/dev/urandom) leaked on lvdisplay invocation. Parent PID 1581: bash
  --- Logical volume ---
  LV Name                /dev/BlazenNas/root
  VG Name                BlazenNas
  LV UUID                1aPIro-uJYA-evW8-Lntp-JMvR-3f3V-TFQ0YQ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                538.42 GiB
  Current LE             137835
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Name                /dev/BlazenNas/swap_1
  VG Name                BlazenNas
  LV UUID                AdwldE-j1VV-ytHg-cgPN-DhxQ-pZvt-sCVuaW
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.62 GiB
  Current LE             415
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


root@BlazenNas:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/BlazenNas-root
                      530G  368G  136G  74% /
udev                  804M  4.0K  804M   1% /dev
tmpfs                 326M  676K  325M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  813M     0  813M   0% /run/shm
/dev/sda1             228M   24M  193M  11% /boot

When i try to do 
~$ vgreduce BlazenNas  /dev/sdb5
Physical volume "/dev/sdb5" still in use

The second drive is only 80Gig and not worth the SATA spot in the machine, when i have a Spare 500Gig i just received.

---

### Post by Catalyph on 2011-10-24
really nobody?

Well I figured it out, I had to create and add another disk to the Logical Volume and then pvmove from the 80 gig to the new disk 
then vgreduce the 80 gig from the Volume group

I think the extents are shown as taken up if you place a file system in them.

---

