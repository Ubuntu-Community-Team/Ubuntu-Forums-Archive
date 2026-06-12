---
title: "nvraid - last Partition (ntfs) unmount-able (FakeRAID/SoftRAID)"
date: 2009-08-11
forum: Hardware
---

### Post by xenonR on 2009-08-11
Hi everyone,
for the last several days i tryed to mount my last partition from an JBOD "RAID" but im sstuck here. I already read a lot of HowTo's, Tutorials, Stuff and MAN-pages but the problem persists.
No i'm trying the Inter-Brain. That's you. [IMG]http://media.ubuntuusers.de/wiki/attachments/09/28/wink.png[/IMG]

Thanks in advance
-xenonR
[B]
Problem:[/B]
Software-RAID (nvraid/nforce4) was successful detected with *dmraid* and all partitions are mounted. Except partition 5 (ntfs). Partition 5 spanns over 2 hdd's (JBOD).
It's impossible to mount that partcular partition. Also the friendly hint about "2x *chkdsk*" doesn't help at all.

**System Details:**
*uname* -a 
```
Linux SiM 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux
```[I]dmraid -r
[/I]```

/dev/sdb: nvidia, "nvidia_gfgfdfab", linear, ok, 1953525166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_gfgfdfab", linear, ok, 1953525166 sectors, data@ 0


```*fdisk* -l /dev/mapper/nvidia_gfgfdfab 
```
Platte /dev/mapper/nvidia_gfgfdfab: 2000.4 GByte, 2000409769984 Byte
255 Köpfe, 63 Sektoren/Spuren, 243202 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xffffffff

                      Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/mapper/nvidia_gfgfdfab1               1           8       64228+  83  Linux
/dev/mapper/nvidia_gfgfdfab2   *           9        2619    20972857+   7  HPFS/NTFS
/dev/mapper/nvidia_gfgfdfab3            2620        5230    20972857+  83  Linux
/dev/mapper/nvidia_gfgfdfab4            5231      243202  1911510090    5  Erweiterte
/dev/mapper/nvidia_gfgfdfab5            5231      243202  1911510058+   7  HPFS/NTFS
```*dmsetup* status /dev/mapper/nvidia_gfgfdfab 
```
0 1953525166 linear 
1953525166 1953525166 linear 
```*dmsetup* info /dev/mapper/nvidia_gfgfdfab 
```
Name:              nvidia_gfgfdfab
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        4
Event number:      0
Major, minor:      252, 0
Number of targets: 2
UUID: DMRAID-nvidia_gfgfdfab
```*mount* -r -t ntfs /dev/mapper/nvidia_gfgfdfab5 /data/ 

OR *mount* -r -t ntfs-3g /dev/mapper/nvidia_gfgfdfab5 /data/ 
```
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/mapper/nvidia_gfgfdfab5': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by xenonR on 2009-08-12
Compared first sector of nv2 (ntfs) with nv5 (ntfs). Both look like NTFS...
*dd* if=/dev/mapper/nvidia_gfgfdfab5 of=/tmp/sector bs=512 count=1
```
see Attachments
```
*dd* if=/dev/mapper/nvidia_gfgfdfab5 of=/tmp/sector bs=512 count=1 skip=1


             **Second Sector** (maybe found something)
The 2nd sector from my working partition starts with

```
0x05 0x00 N 0x00 T 0x00 L 0x00 D 0x00 R  (NTLDR)
```the not working partition starts with
```
0x07 0x00 B 0x00 O 0x00 O 0x00 T 0x00 M 0x00 G 0x00 R (BOOTMGR)
``` then (77 Byte) later on follows

```
0x05 0x00 N 0x00 T 0x00 L 0x00 D 0x00 R  (NTLDR)
```But at the moment it doesn't help at all... *sigh*
-xenonR

---

### Post by xenonR on 2009-08-13
*testdisk* reports different states/errors under Win and Linux.

Testdisk (Windows)

```
Partition table type (auto): Intel
Disk /dev/sda - 2000 GB / 1863 GiB - NVIDIA JBOD       1.81T
Partition table type: Intel

Analyse Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243202 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 8/0/1
NTFS at 5230/1/1
heads/cylinder 0 (NTFS) != 255 (HD)
sect/track 0 (NTFS) != 63 (HD)
get_geometry_from_list_part_aux head=255 nbr=10
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=10
Current partition structure:
 1 P Linux                    0   1  1     7 254 63     128457
 2 * HPFS - NTFS              8   0  1  2618 254 63   41945715 [windows]
 3 P Linux                 2619   0  1  5229 254 63   41945715
 4 E extended              5230   0  1 243201 254 63 3823020180
Warning: Incorrect number of heads/cylinder 0 (NTFS) != 255 (HD)
Warning: Incorrect number of sectors per track 0 (NTFS) != 63 (HD)
 5 L HPFS - NTFS           5230   1  1 243201 254 63 3823020117 [data]

```

Testdisk (Linux)

```
Partition table type (auto): Intel
Disk /dev/mapper/nvidia_gfgfdfab - 2000 GB / 1863 GiB
Partition table type: Intel

Analyse Disk /dev/mapper/nvidia_gfgfdfab - 2000 GB / 1863 GiB - CHS 3907050332 1 1
Geometry from i386 MBR: head=255 sector=63
BAD_RS LBA=63 1
BAD_RS LBA=128520 8
NTFS at 128520/0/1
heads/cylinder 255 (NTFS) != 1 (HD)
sect/track 63 (NTFS) != 1 (HD)
NTFS at 84020013/0/1
heads/cylinder 0 (NTFS) != 1 (HD)
sect/track 0 (NTFS) != 1 (HD)
get_geometry_from_list_part_aux head=1 nbr=10
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
 1 P Linux                         63     128519     128457

Warning: Bad ending sector (CHS and LBA don't match)
Warning: Incorrect number of heads/cylinder 255 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 63 (NTFS) != 1 (HD)
 2 * HPFS - NTFS               128520   42074234   41945715 [windows]

Warning: Bad ending sector (CHS and LBA don't match)
 3 P Linux                   42074235   84019949   41945715

Warning: Bad ending sector (CHS and LBA don't match)
 4 E extended                84019950 3907040129 3823020180

Warning: Bad ending sector (CHS and LBA don't match)
Warning: Incorrect number of heads/cylinder 0 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 0 (NTFS) != 1 (HD)
 5 L HPFS - NTFS             84020013 3907040129 3823020117 [data]

Warning: Bad ending sector (CHS and LBA don't match)

```

---

### Post by xenonR on 2009-08-14
After reviewing the disk geometry information from testdisk i belive there's the problem.

testdisk (windows) reports
```
Analyse Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243202 255 63
Geometry from i386 MBR: head=255 sector=63
```while testdisk linux reports
```
Analyse Disk /dev/mapper/nvidia_gfgfdfab - 2000 GB / 1863 GiB - CHS 3907050332 1 1
Geometry from i386 MBR: head=255 sector=63

```

So linux detects the wrong CHS values but sees the right geometry from the MBR.
Is there a way to check witch CHS value linux uses for an active partition?

-xenonR

---

