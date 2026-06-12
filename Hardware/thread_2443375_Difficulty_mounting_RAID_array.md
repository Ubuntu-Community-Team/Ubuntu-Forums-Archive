---
title: "Difficulty mounting RAID array"
date: 2020-05-14
forum: Hardware
---

### Post by jamiegordon on 2020-05-14
Hello,My previous Ubuntu server suffered a catastrophic failure. The root volume was unrecoverable damaged. The server had 1 volume group and a 1 physical and logical volumes for the root/swap and a Raid 5 array (3 disks and a standby). I install a new drive, installed Ubuntu. I then mounted the Raid 5 drives. The RAID volumes were immediately recognized and I see the RAID and it’s clean. I’m having trouble mounting the RAID array, getting the following error:


```
jgordon@XXXX:~$ sudo mount /dev/gilbert-vg/data /data
mount: /data: wrong fs type, bad option, bad superblock on /dev/mapper/gilbert--vg-data, missing codepage or helper program, or other error.

```

Any suggestions would be greatly appreciated. [-o<




Here’s the config: 


```
jgordon@lumpy:~$ sudo mdadm --detail /dev/md127 
/dev/md127:
           Version : 1.2
     Creation Time : Tue May  2 18:28:26 2017
        Raid Level : raid5
        Array Size : 7813771264 (7451.79 GiB 8001.30 GB)
     Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
      Raid Devices : 3
     Total Devices : 4
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Tue May 12 23:17:21 2020
             State : clean 
    Active Devices : 3
   Working Devices : 4
    Failed Devices : 0
     Spare Devices : 1


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : lumpy:1  (local to host lumpy)
              UUID : 50e86e37:8b1ce2b2:642aeb2a:d052e622
            Events : 17857


    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       49        1      active sync   /dev/sdd1
       3       8       33        2      active sync   /dev/sdc1


       4       8       17        -      spare   /dev/sdb1

```
```

jgordon@XXXX:~$ fdisk -l /dev/sd*
Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 860 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe2b16d0e


Device     Boot Start       End   Sectors   Size Id Type
/dev/sda2        4096 976771071 976766976 465.8G 83 Linux




Disk /dev/sda2: 465.78 GiB, 500104691712 bytes, 976766976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sdb: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFRX-68W
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4147FCB1-0C88-468B-B115-A10211924D7E


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7814035455 7814033408  3.7T Linux RAID




Disk /dev/sdb1: 3.65 TiB, 4000785104896 bytes, 7814033408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdc: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFRX-68W
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 39568C39-0EA5-42B2-928A-0DDE77A2E5A4


Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux RAID




Disk /dev/sdc1: 3.65 TiB, 4000785104896 bytes, 7814033408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdd: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFRX-68W
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 17C58906-E12F-42D2-808A-0D68F577769D


Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 7814035455 7814033408  3.7T Linux RAID




Disk /dev/sdd1: 3.65 TiB, 4000785104896 bytes, 7814033408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sde: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFRX-68W
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 165BA422-4C57-47CB-97A5-908BD25E9EC6


Device     Start        End    Sectors  Size Type
/dev/sde1   2048 7814035455 7814033408  3.7T Linux RAID




Disk /dev/sde1: 3.65 TiB, 4000785104896 bytes, 7814033408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


jgordon@XXXX:~$ sudo lvs
  LV   VG         Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  data gilbert-vg -wi-a----- <7.28t                                          

```



```
jgordon@XXXX:~$ sudo vgdisplay 
  --- Volume group ---
  VG Name               gilbert-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  25
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <7.28 TiB
  PE Size               4.00 MiB
  Total PE              1907658
  Alloc PE / Size       1907456 / <7.28 TiB
  Free  PE / Size       202 / 808.00 MiB
  VG UUID               JvECcR-LMw4-VMou-cfNx-Y6O8-6qJ4-p9nrfM



```


```
jgordon@XXXX:~$ sudo lsblk /dev/sd*
NAME                   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                      8:0    0 465.8G  0 disk  
&#9492;&#9472;sda2                   8:2    0 465.8G  0 part  /
sda2                     8:2    0 465.8G  0 part  /
sdb                      8:16   0   3.7T  0 disk  
&#9492;&#9472;sdb1                   8:17   0   3.7T  0 part  
  &#9492;&#9472;md127                9:127  0   7.3T  0 raid5 
    &#9492;&#9472;gilbert--vg-data 253:0    0   7.3T  0 lvm   
sdb1                     8:17   0   3.7T  0 part  
&#9492;&#9472;md127                  9:127  0   7.3T  0 raid5 
  &#9492;&#9472;gilbert--vg-data   253:0    0   7.3T  0 lvm   
sdc                      8:32   0   3.7T  0 disk  
&#9492;&#9472;sdc1                   8:33   0   3.7T  0 part  
  &#9492;&#9472;md127                9:127  0   7.3T  0 raid5 
    &#9492;&#9472;gilbert--vg-data 253:0    0   7.3T  0 lvm   
sdc1                     8:33   0   3.7T  0 part  
&#9492;&#9472;md127                  9:127  0   7.3T  0 raid5 
  &#9492;&#9472;gilbert--vg-data   253:0    0   7.3T  0 lvm   
sdd                      8:48   0   3.7T  0 disk  
&#9492;&#9472;sdd1                   8:49   0   3.7T  0 part  
  &#9492;&#9472;md127                9:127  0   7.3T  0 raid5 
    &#9492;&#9472;gilbert--vg-data 253:0    0   7.3T  0 lvm   
sdd1                     8:49   0   3.7T  0 part  
&#9492;&#9472;md127                  9:127  0   7.3T  0 raid5 
  &#9492;&#9472;gilbert--vg-data   253:0    0   7.3T  0 lvm   
sde                      8:64   0   3.7T  0 disk  
&#9492;&#9472;sde1                   8:65   0   3.7T  0 part  
  &#9492;&#9472;md127                9:127  0   7.3T  0 raid5 
    &#9492;&#9472;gilbert--vg-data 253:0    0   7.3T  0 lvm   
sde1                     8:65   0   3.7T  0 part  
&#9492;&#9472;md127                  9:127  0   7.3T  0 raid5 
  &#9492;&#9472;gilbert--vg-data   253:0    0   7.3T  0 lvm   

```

---

