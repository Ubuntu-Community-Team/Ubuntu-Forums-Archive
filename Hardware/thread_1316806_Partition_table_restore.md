---
title: "Partition table restore"
date: 2009-11-06
forum: Hardware
---

### Post by MrIch on 2009-11-06
In order to find a lost ntfs partition I started testdisk

```

Partition table type (auto): Intel
Disk /dev/sda - 1000 GB / 931 GiB - ATA ST31000333AS
Partition table type: Intel

Analyse Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
NTFS at 70608/1/1
Info: size boot_sector 819202473, partition 819202482
get_geometry_from_list_part_aux head=255 nbr=10
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=240 nbr=2
get_geometry_from_list_part_aux head=255 nbr=10
Current partition structure:
Invalid NTFS or EXFAT boot
 1 * HPFS - NTFS              0  32 33  6374  59 21  102400000
 1 * HPFS - NTFS              0  32 33  6374  59 21  102400000
 2 P Linux                 6375   0  1  6436 254 63     996030
 3 E extended              6437   0  1 121600 254 63 1850109660
 5 L Linux                 6437   1  1 44681 254 63  614405862
   X extended             70608   0  1 121600 254 63  819202545
 6 L HPFS - NTFS          70608   1  1 121600 254 63  819202482 [UC_Backup]

```

Unfortunatly testdisk removed the extended partiton on all my linux partition (/dev/sda2 ext3 boot, /dev/sda5 luks)

I'd like to recreate the partition table based on the above output. But I did not manage to get a partition table which is 100% the same. What is the meaning of "32 33"? What is the meaning of "59 21" or "254 63".

Fdisk does not seem to have more options than starting / ending cylinder.

---

