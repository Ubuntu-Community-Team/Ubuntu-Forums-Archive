---
title: "Unrecognized SSD"
date: 2018-10-17
forum: Hardware
---

### Post by bznm on 2018-10-17
Hi,
I've just bought SSD PNY CS900.. however it isn't recognized by Ubuntu. On Windows it just works.
In the bios I've already selected AHCI mode.

What should I do?

sudo fdisk -l
```
Disk /dev/loop0: 82,4 MiB, 86441984 bytes, 168832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 198,5 MiB, 208130048 bytes, 406504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 226,5 MiB, 237469696 bytes, 463808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 226,5 MiB, 237490176 bytes, 463848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 199,7 MiB, 209416192 bytes, 409016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 87,9 MiB, 92119040 bytes, 179920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 87 MiB, 91160576 bytes, 178048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 87,9 MiB, 92164096 bytes, 180008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000ee900

Dispositivo Avvio     Start       Fine    Settori   Size Id Tipo
/dev/sda1                63   31250062   31250000  14,9G 83 Linux
/dev/sda2          31250430  600270847  569020418 271,3G  f W95 Esteso (LBA)
/dev/sda3   *     642584576  787331071  144746496    69G  7 HPFS/NTFS/exFAT
/dev/sda4         787331072 1953524431 1166193360 556,1G 83 Linux
/dev/sda5          31250432   78125055   46874624  22,4G 83 Linux
/dev/sda6          78127104  156250111   78123008  37,3G 83 Linux
/dev/sda7         156252160  185964543   29712384  14,2G  6 FAT16
/dev/sda8         185968503  187928369    1959867   957M 82 Linux swap / Solaris
/dev/sda9         187928433  443924144  255995712 122,1G 83 Linux
/dev/sda10        443924208  487628799   43704592  20,9G  7 HPFS/NTFS/exFAT
/dev/sda11        487630848  600270847  112640000  53,7G 83 Linux

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 8 does not start on physical sector boundary.
Partition 9 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/sdd: 931,5 GiB, 1000202043392 bytes, 1953519616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008768a

Dispositivo Avvio      Start       Fine    Settori   Size Id Tipo
/dev/sdd1               2048    6371327    6369280     3G  7 HPFS/NTFS/exFAT
/dev/sdd2            6371328 1591349247 1584977920 755,8G  5 Esteso
/dev/sdd3         1591349248 1953519615  362170368 172,7G  7 HPFS/NTFS/exFAT
/dev/sdd5            6373376  294240255  287866880 137,3G 83 Linux
/dev/sdd6         1416906752 1591349247  174442496  83,2G  7 HPFS/NTFS/exFAT
/dev/sdd7   *      294242304 1416904703 1122662400 535,3G 83 Linux

Partition table entries are not in disk order.


Disk /dev/sdc: 29 GiB, 31104958464 bytes, 60751872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Dispositivo Avvio Start     Fine  Settori Size Id Tipo
/dev/sdc1          8192 60751871 60743680  29G  c W95 FAT32 (LBA)


Disk /dev/loop8: 226,5 MiB, 237481984 bytes, 463832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 199,8 MiB, 209457152 bytes, 409096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

As you can see /dev/sdb (the SSD) is just missing!

sudo parted -l

```
Modello: ATA ST1000DM003-1ER1 (scsi)
Disco /dev/sda: 1000GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: msdos
Flag del disco: 

Numero  Inizio  Fine    Dimensione  Tipo      File system     Flag
 1      32,3kB  16,0GB  16,0GB      primary   ext4
 2      16,0GB  307GB   291GB       extended                  lba
 5      16,0GB  40,0GB  24,0GB      logical   ext4
 6      40,0GB  80,0GB  40,0GB      logical   ext3
 7      80,0GB  95,2GB  15,2GB      logical
 8      95,2GB  96,2GB  1003MB      logical   linux-swap(v1)
 9      96,2GB  227GB   131GB       logical   ext4
10      227GB   250GB   22,4GB      logical   ntfs
11      250GB   307GB   57,7GB      logical   ext4
 3      329GB   403GB   74,1GB      primary   ntfs            avvio
 4      403GB   1000GB  597GB       primary   ext4


Avviso: Errore nell'eseguire fsync o nel chiudere /dev/sdb1: Errore di
input/output
Riprova/Retry/Ignora/Ignore? R                                            
parted: token non valido: R
Riprova/Retry/Ignora/Ignore? Retry                                        
Avviso: Errore nell'eseguire fsync o nel chiudere /dev/sdb1: Errore di input/output
Riprova/Retry/Ignora/Ignore? Ignore                                       
Errore: /dev/sdb: etichetta del disco non riconosciuta
Avviso: Errore nell'eseguire fsync o nel chiudere /dev/sdb: Errore di input/output
Riprova/Retry/Ignora/Ignore? Ignore                                       
Modello: ATA PNY CS900 120GB (scsi)
Disco /dev/sdb: 120GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: unknown
Flag del disco: 

Modello: Generic Mass-Storage (scsi)
Disco /dev/sdc: 31,1GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos
Flag del disco: 

Numero  Inizio  Fine    Dimensione  Tipo     File system  Flag
 1      4194kB  31,1GB  31,1GB      primary  fat32        lba


Modello: WD Ext HDD 1021 (scsi)
Disco /dev/sdd: 1000GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos
Flag del disco: 

Numero  Inizio  Fine    Dimensione  Tipo      File system  Flag
 1      1049kB  3262MB  3261MB      primary   ntfs
 2      3262MB  815GB   812GB       extended
 5      3263MB  151GB   147GB       logical   ext4
 7      151GB   725GB   575GB       logical   ext4         avvio
 6      725GB   815GB   89,3GB      logical   ntfs
 3      815GB   1000GB  185GB       primary   ntfs

```

This one is somewhat more informative about sdb!

I've searched a lot but didn't found the solution!
Thanks for the help

---

### Post by Autodave on 2018-10-17
I am assuming that you formatted this in Windows?  To what was it formatted?  NTFS?  How many partitions did you put on it?

---

### Post by bznm on 2018-10-17
Yes, formatted on windows. MBR table, one NTFS partition. Tried also with GPT but didn't work.

---

### Post by oldfred on 2018-10-17
Have you updated UEFI and firmware for SSD?
Many systems need both.

Separately you have a newer 4K drive as sda, but the old XP style partitioning which was from before 4K drives.
Since Windows 7, first partition starts at sector 2048 like your sdc, XP used 63. 
       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

