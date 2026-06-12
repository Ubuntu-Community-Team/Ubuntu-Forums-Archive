---
title: "Expand LVM"
date: 2014-11-20
forum: Hardware
---

### Post by DavidBer on 2014-11-20
I am trying to expand my Ubuntu Server 14.04.1 storage.

This is a VM running on W2012 Hyper V.  It started out as 2tb and now I need more space (woo hoo!)  I shut down the VM and added space to the VM in HyperV.  Now I am stuck.

```
root@ubuntu:~# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 6442.5 GB, 6442450944000 bytes
255 heads, 63 sectors/track, 783250 cylinders, total 12582912000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/ubuntu--vg-root: 2681.9 GB, 2681947029504 bytes
255 heads, 63 sectors/track, 326061 cylinders, total 5238177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
root@ubuntu:~# 
```

```
root@ubuntu:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               2.44 TiB / not usable 1.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              639938
  Free PE               0
  Allocated PE          639938
  PV UUID               rnilZD-jbFh-ylAc-wZu5-5SnG-FONu-TJxumx
   

```

```

root@ubuntu:~# pvscan
  PV /dev/sda3   VG ubuntu-vg   lvm2 [2.44 TiB / 0    free]
  Total: 1 [2.44 TiB] / in use: 1 [2.44 TiB] / in no VG: 0 [0   ]
```

```
root@ubuntu:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                JXtxUm-9eeu-VGj7-cdil-zIpk-zqWL-1vLYpq
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-10-13 15:14:18 -0700
  LV Status              available
  # open                 1
  LV Size                2.44 TiB
  Current LE             639426
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                hE9cgx-vwty-HvXP-f0gZ-6fa6-r4l6-NWURHg
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-10-13 15:14:18 -0700
  LV Status              available
  # open                 2
  LV Size                2.00 GiB
  Current LE             512
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
```

```
root@ubuntu:~# vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.44 TiB
  PE Size               4.00 MiB
  Total PE              639938
  Alloc PE / Size       639938 / 2.44 TiB
  Free  PE / Size       0 / 0   
  VG UUID               2vxeJH-w91o-VtmB-a8kc-eBE0-gKrx-geQ1JQ
```

```
root@ubuntu:~# lvextend -L+2000g /dev/ubuntu-vg/root
  Extending logical volume root to 4.39 TiB
  Insufficient free space: 512000 extents needed, but only 0 available
```


When I try to extend, I am seeing that there is no space available.  What am I doing wrong?


Thanks.

dave

---

