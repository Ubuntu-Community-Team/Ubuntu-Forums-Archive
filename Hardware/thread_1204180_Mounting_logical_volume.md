---
title: "Mounting logical volume"
date: 2009-07-04
forum: Hardware
---

### Post by Mcgeesteh on 2009-07-04
Hey, I just added a new disk to a volume group as its own logical volume. The disk added fine and appears in /dev/vg01/

The problem is that it doesn't appear to be recognized elsewhere, blkid does not have it listed- while the other logical volumes are there. It's not in /dev/disk/by-uuid either. Is there something I have to do to get it added/recognized? Various outputs below. (The problematic logical volume is vg01/backup)

Thanks,
Michael.

```
$ lvdisplay
  --- Logical volume ---
  LV Name                /dev/vg01/home
  VG Name                vg01
  LV UUID                Feg94s-KpFs-DasI-s0Bc-csSA-HcQn-34vksh
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                575.71 GB
  Current LE             147383
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/vg01/backup
  VG Name                vg01
  LV UUID                fznOXi-xADA-r1Eq-olWw-oOO7-MKDu-xpNFvJ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                465.76 GB
  Current LE             119234
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
```

```
$ blkid
/dev/sda1: UUID="5e972ca7-87ef-4101-bf3c-119ebcaf0a8d" TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="ad37e795-7a95-4bfc-a37c-ef21c2f5df41" 
/dev/sda6: UUID="c339d66c-8bc8-42ad-9fd4-ae6467e9736a" TYPE="ext3" 
/dev/sda7: UUID="xBPZAi-dkuK-oAdx-opM2-K3PX-kdSo-Hbxe5x" TYPE="lvm2pv" 
/dev/sdb: UUID="85gRMg-3nHu-hpOj-PlMZ-v2gO-e2bk-Xg7Wda" TYPE="lvm2pv" 
/dev/sdc: UUID="jlAshP-E9tB-zgEC-Jnfb-pfsS-YxdJ-hY6vG3" TYPE="lvm2pv" 
/dev/sdd: UUID="kxTZwe-uvXt-h9Ri-3A8f-ET20-oOdg-rj059M" TYPE="lvm2pv" 
/dev/sde1: UUID="C43C88553C884480" TYPE="ntfs" 
/dev/mapper/vg01-home: UUID="ccc39363-fc69-45e5-ab7c-1a339f074575" SEC_TYPE="ext2" TYPE="ext3" 
```

```
$ ls /dev/disk/by-uuid
5e972ca7-87ef-4101-bf3c-119ebcaf0a8d
ad37e795-7a95-4bfc-a37c-ef21c2f5df41
c339d66c-8bc8-42ad-9fd4-ae6467e9736a
C43C88553C884480
ccc39363-fc69-45e5-ab7c-1a339f074575
```

```
$ ls /dev/vg01
backup
home
```

---

### Post by Mcgeesteh on 2009-07-04
Fixed, by running ```
mke2fs -j /dev/vg01/backup
``` ](*,)

---

