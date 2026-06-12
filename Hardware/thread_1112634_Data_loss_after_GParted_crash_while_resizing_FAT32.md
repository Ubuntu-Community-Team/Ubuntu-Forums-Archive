---
title: "Data loss after GParted crash while resizing FAT32 Partition"
date: 2009-03-31
forum: Hardware
---

### Post by partition on 2009-03-31
Since GParted couldn't end the resize correctly:

-folders and files are no longer visible. 
-instead there are 512  FSCK0*.REC files each sized 16 kB and dated Mon 31 Dez 1979.
-the amout of used space is still correct.
-unmounting the partition with GParted has no effect. (GParted hangs, no tests can be performed) -> This partition is no longer accessible by GParted. 

I tried to recover with TestDisk, no success, no change.
( [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) )

I would highly appreciate some advice how to possibly restore the contents of that partition.

The following details were logged by gparted:
(error message in line 17)

Thanx
Andreas



GParted 0.3.8

Libparted 1.8.9

/dev/sda2 (ext3, 390.63 GB) von /dev/sda lÃ¶schen  00:00:00    ( SUCCESS )
     	
/dev/sda2 kalibrieren  00:00:00    ( SUCCESS )
     	
Pfad: /dev/sda2
Anfang: 1134317520
Ende: 1953520064
GrÃ¶Ã&#376;e: 819202545 (390.63 GB)
Partition lÃ¶schen  00:00:00    ( SUCCESS )

========================================

/dev/sda1 von 540.88 GB auf 512.56 GB verkleinern  00:07:35    ( ERROR )
     	
/dev/sda1 kalibrieren  00:00:00    ( SUCCESS )
     	
Pfad: /dev/sda1
Anfang: 63
Ende: 1134317519
GrÃ¶Ã&#376;e: 1134317457 (540.88 GB)
Neue GrÃ¶Ã&#376;e und Position von /dev/sda1 berechnen  00:00:00    ( SUCCESS )
     	
Angeforderter Anfang: 63
Angefordertes Ende: 1074925214
Angeforderte GrÃ¶Ã&#376;e: 1074925152 (512.56 GB)
Neuer Anfang: 63
Neues Ende: 1074925214
Neue GrÃ¶Ã&#376;e: 1074925152 (512.56 GB)
Dateisystem auf /dev/sda1 auf Fehler Ã¼berprÃ¼fen und (falls mÃ¶glich) diese beheben  00:00:47    ( SUCCESS )
     	
dosfsck -a -w -v /dev/sda1
     	
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
16384 bytes per cluster
54 reserved sectors
First FAT starts at byte 27648 (sector 54)
2 FATs, 32 bit entries
141755392 bytes per FAT (= 276866 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 283538432 (sector 553786)
35430114 data clusters (580486987776 bytes)
63 sectors/track, 255 heads
63 hidden sectors
1134317457 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sda1: 19326 files, 24690070/35430114 clusters
Dateisystem verkleinern  00:02:52    ( SUCCESS )
     	
libparted wird verwendet
Partition von 540.88 GB auf 512.56 GB verkleinern  00:00:00    ( SUCCESS )
     	
Alter Anfang: 63
Altes Ende: 1134317519
Alte GrÃ¶Ã&#376;e: 1134317457 (540.88 GB)
Neuer Anfang: 63
Neues Ende: 1074925214
Neue GrÃ¶Ã&#376;e: 1074925152 (512.56 GB)
Dateisystem auf /dev/sda1 auf Fehler Ã¼berprÃ¼fen und (falls mÃ¶glich) diese beheben  00:03:47    ( SUCCESS )
     	
dosfsck -a -w -v /dev/sda1

---

