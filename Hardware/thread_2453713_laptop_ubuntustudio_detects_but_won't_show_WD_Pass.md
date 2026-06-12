---
title: "laptop ubuntustudio detects but won't show WD Passport external drive"
date: 2020-11-16
forum: Hardware
---

### Post by Dirk_Ouellette on 2020-11-16
lsusb
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b39a Chicony Electronics Co., Ltd Integrated Camera
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 138a:0017 Validity Sensors, Inc. VFS 5011 fingerprint sensor
Bus 002 Device 006: ID 1397:0509 BJohannaEHRINGER International GmbH UMC404HD 192k
Bus 002 Device 008: ID 1058:259f Western Digital Technologies, Inc. My Passport Ultra (WD10JMVW)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsusb
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b39a Chicony Electronics Co., Ltd Integrated Camera
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 138a:0017 Validity Sensors, Inc. VFS 5011 fingerprint sensor
Bus 002 Device 006: ID 1397:0509 BEHRINGER International GmbH UMC404HD 192k
Bus 002 Device 008: ID 1058:259f Western Digital Technologies, Inc. My Passport Ultra (WD10JMVW)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dirk@ThinkPad-T440s:~$ sudo fdisk -l
[sudo] password for dirk: 
Disk /dev/loop0: 30.96 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.37 MiB, 58052608 bytes, 113384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 169.31 MiB, 177528832 bytes, 346736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 256.18 GiB, 275064201216 bytes, 537234768 sectors
Disk model: Crucial_CT275MX3
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe97295bb

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2       1052670 537233407 536180738 255.7G  5 Extended
/dev/sda5       1052672 537233407 536180736 255.7G 83 Linux

---

### Post by Dirk_Ouellette on 2020-11-18
SOLVED, after about an hour, it suddenly showed up! And has shown up every time I turn the machine on. Oh well, happy days!

---

