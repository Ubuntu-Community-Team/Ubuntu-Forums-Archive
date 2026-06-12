---
title: "ata1.00: SET of native returned 318767124, expected 321672960"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by havenonick on 2007-04-28
hello,

i'm using ubuntu 7.04 with latest update.
botting without the splash screen i'm getting this message:
```
ata1.00: SET of native returned 318767124, expected 321672960
```
first thought something is wrong with my hdd, but then i tried 2 further hard disks (and i have the same problem with them, except that the numbers are different), can't imagine that all of them are damaged.

having a look at /var/log/dmesg showed me something which is probably more helpful:
```
[    3.304000]      current size : 321670847 sectors (164695 MB)
[    3.304000]      native  size : 321672960 sectors (164696 MB)
[    3.304000] ata1.00: SET of native returned 318767124, expected 321672960
[    3.312000] ata1.00: Native size increased to 321672960 sectors
[    3.312000] ata1.00: ATA-7: ExcelStor Technology J8160S, P22OA50U, max UDMA/133
[    3.312000] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.320000] ata1.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[    3.320000] ata1.00: configured for UDMA/133
```

so it seems to be something wrong with my sector sizes / partitions? i created my partitions using the gparted live cd (ubuntu installer always crashed on partitioning), my partition layout is as follows:

/ boot 100mb primary ext3

rest of hdd is an extend partition, with the following partitions inside:
1000mb unused
20000 mb ext3 /
20000 mb ext3 not mounted
and some more mb as ext3 not mounted

when i created this layout using gparted i never formatted the partitions, i declared them all as unused / no filesystem. /boot and / got their filesystems declared by the ubuntu installer.

somebody knows how to fix this message? at one of the 3 hdds i tried fsck once exited with code 3, i'm not yet sure if in this case really sth. is wrong with the hdd or the partition layout, so though my system is running fine i'd like to fix this problem.

my relevant system components:
mainboard: gigabyte ga m61p-s3 (nforce 430 chipset)
hdd: ExcelStor Excelstor J8160SR  (however i also have this problem with a seagate hdd, even with 2 of them, same model)

i've attached my complete dmesg log.


thanks for your help!

---

