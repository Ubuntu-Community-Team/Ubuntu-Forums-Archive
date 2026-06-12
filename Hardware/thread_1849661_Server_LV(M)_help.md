---
title: "Server LV(M) help"
date: 2011-09-24
forum: Hardware
---

### Post by janthes on 2011-09-24
Hi guys,

I have a server that I'm fiddling around with trying to create a striped LVM and I've hit a wall.

I have 4 drives that I want to pool into one volume. As of now, I have three pooled into a VG (VG 'StripedLVM') with the fourth drive (VG 'netshare') to be added to the pool after I move the data over. 

My headache is in trying to create an LV. I want the LV to span across VG StripedLVM.

```

janthes@soma:~$ sudo lvcreate -i 3 -I4 -l 100%FREE -n LANShare StripedLVM
  Rounding size (591398 extents) up to stripe boundary size (591399 extents)
  Insufficient free extents (591398) in volume group StripedLVM: 591399 required

```

Googling around on "Insufficient free extents in volume group" I come across tldp/CentOS documentation which tells me to:

```
janthes@soma:~$ sudo vgs -o +vg_free_count,vg_extent_count
  VG         #PV #LV #SN Attr   VSize VFree Free   #Ext  
  StripedLVM   3   0   0 wz--n- 2.26t 2.26t 591398 591398
  netshare     1   1   0 wz--n- 1.82t    0       0 476931

janthes@soma:~$ sudo lvcreate -i 3 -I4 -l591398 -n LANShare StripedLVM
  Rounding size (591398 extents) up to stripe boundary size (591399 extents)
  Insufficient free extents (591398) in volume group StripedLVM: 591399 required
james@soma:~$

```

...wtf?! Now I've thrown in the towel and I'm asking for help. Something seemingly simple is quite deceptive :/

Some extra info:

```

janthes@soma:~$ uname -a
Linux soma 2.6.32-33-server #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011 x86_64 GNU/Linux
janthes@soma:~$ sudo vgdisplay 
  --- Volume group ---
  VG Name               netshare
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               1.82 TiB
  PE Size               4.00 MiB
  Total PE              476931
  Alloc PE / Size       476931 / 1.82 TiB
  Free  PE / Size       0 / 0   
  VG UUID               [REDACTED]
   
  --- Volume group ---
  VG Name               StripedLVM
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               2.26 TiB
  PE Size               4.00 MiB
  Total PE              591398
  Alloc PE / Size       0 / 0   
  Free  PE / Size       591398 / 2.26 TiB
  VG UUID               [REDACTED]

janthes@soma:~$ sudo pvdisplay 
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               netshare
  PV Size               1.82 TiB / not usable 2.56 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               [REDACTED]
   
  --- Physical volume ---
  PV Name               /dev/sde1
  VG Name               StripedLVM
  PV Size               1.82 TiB / not usable 1.05 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              476932
  Free PE               476932
  Allocated PE          0
  PV UUID               [REDACTED]
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               StripedLVM
  PV Size               298.09 GiB / not usable 2.81 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              76310
  Free PE               76310
  Allocated PE          0
  PV UUID               [REDACTED]
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               StripedLVM
  PV Size               149.05 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              38156
  Free PE               38156
  Allocated PE          0
  PV UUID               [REDACTED]
   
janthes@soma:~$
```

Thanks guys!!

---

### Post by janthes on 2011-09-28
*bump*

Please advise.

---

