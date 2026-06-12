---
title: "Partition on 3ware RAID"
date: 2010-01-26
forum: Hardware
---

### Post by talon99 on 2010-01-26
[FONT=Times New Roman][SIZE=3]I'm having a problem partitioning a raid array attached to a 3ware 9650 card.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have a recent install of Ubuntu Server 9.10 and the card appears to be working OK. I have 4 - 1.5TB Seagate Barracuda disks configured using raid 5[/SIZE][/FONT]
 
```
 
uname -a
Linux mediastore 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
 
lspci | grep 3w
01:00.0 RAID bus controller: 3ware Inc 9650SE SATA-II RAID PCIe (rev 01)
 
sudo tw_cli /c10 show
 
Unit  UnitType  Status         %RCmpl  %V/I/M  Stripe  Size(GB)  Cache  AVrfy
------------------------------------------------------------------------------
u0    RAID-5    OK             -       -       64K     4190.92   OFF    OFF
 
Port   Status           Unit   Size        Blocks        Serial
---------------------------------------------------------------
p0     OK               u0     1.36 TB     2930277168    9VS20WVJ
p1     OK               u0     1.36 TB     2930277168    9VS21G9R
p2     OK               u0     1.36 TB     2930275055    9VS20VFZ
p3     OK               u0     1.36 TB     2930275055    9VS1XY1D

```
 
[FONT=Times New Roman][SIZE=3]I partitioned with cfdisk to have 1 partition of size 4499960.21MB but it only created a 102 GB partition.[/SIZE][/FONT]
 
```
 
sudo parted /dev/sdb print
Model: AMCC 9650SE-4LP DISK (scsi)
Disk /dev/sdb: 4500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End    Size   Type     File system  Flags
1            32.3kB  102GB  102GB  primary

```
 
[FONT=Times New Roman][SIZE=3]Is there something I’m missing about using Hardware RAID ?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Thanks,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Peter[/SIZE][/FONT]

---

### Post by talon99 on 2010-01-27
Problem solved.
 
needed to change from a msdos to a gpt Partition Table.
 
```
 
#sudo parted /dev/sdb print
Model: AMCC 9650SE-4LP DISK (scsi)
Disk /dev/sdb: 4500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  4500GB  4500GB  xfs          primary

```
 
 
Found answer here:
 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

