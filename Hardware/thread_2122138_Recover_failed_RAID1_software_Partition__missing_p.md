---
title: "Recover failed RAID1 software Partition / missing partition table or superblock"
date: 2013-03-04
forum: Hardware
---

### Post by callmefunkeyescobar on 2013-03-04
Hello Guys,

[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][/TD]
[TD="class: postcell, bgcolor: transparent"]i already read & tried different approaches for 2 days now but nothing seems to work. I have 2 HDDs, on each one is an partition with 200GB which i had in RAID1. Then i installed XBMC and tried to start the raid again. The Array starts, but it is missing the filesystem ( i think it was ext4), so mounting is not possible. Outputs:

```
   ubuntu@ubuntu:~$ sudo fdisk -l    
    Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
    255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
    Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xf3b92028
    
       Gerät  boot.     Anfang        Ende     Blöcke   Id  System
    /dev/sda1   *           1       97379   782196786   83  Linux
    /dev/sda2           97380      121601   194563215   fd  Linux raid autodetect
    
    Platte /dev/sdb: 1500.3 GByte, 1500301910016 Byte
    255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder
    Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0c41a682
    
       Gerät  boot.     Anfang        Ende     Blöcke   Id  System
    /dev/sdb1   *           1        9362    75194336   83  Linux
    /dev/sdb2            9362       10199     6724609    5  Erweiterte
    /dev/sdb3           10200       34421   194563215   fd  Linux raid autodetect
    /dev/sdb4           34515      182401  1187902327+  83  Linux
    /dev/sdb5            9362       10199     6724608   82  Linux Swap / Solaris
    
    Platte /dev/sde: 1977 MByte, 1977614336 Byte
    64 Köpfe, 63 Sektoren/Spur, 957 Zylinder
    Einheiten = Zylinder von 4032 × 512 = 2064384 Bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
       Gerät  boot.     Anfang        Ende     Blöcke   Id  System
    /dev/sde1               1         957     1929244+   6  FAT16



```
i need sda2 and sdb3 to be in an array again.

```
    ubuntu@ubuntu:~$ sudo mdadm -E -s
    ARRAY /dev/md0 level=raid1 num-devices=1 UUID=5c001a6c:9e51fa30:e368bf24:bd0fce41
    ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ed6394c7:53941634:e368bf24:bd0fce41



```
the raid with 1 device is from when i tried to make an array with 1 Disk to recover data (which didnt work out). i havent deleted the array yet because i dont know what will happen. i hope i didnt made it worse by that.
then i tried this guide: [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

```
   ubuntu@ubuntu:~$ sudo fsck.ext4 -v /dev/sdb3    e2fsck 1.41.11 (14-Mar-2010)
    fsck.ext4: Superblock ungültig versuche es mit Backup-Blöcken...
    fsck.ext4: Bad magic number in super-block beim Versuch, /dev/sdb3 zu öffnen
    
    SuperBlock ist unlesbar bzw. beschreibt kein gültiges ext2
    Dateisystem.  Wenn Gerät gültig ist und ein ext2
    Dateisystem (kein swap oder ufs usw.) enthält,  dann ist der SuperBlock
    beschädigt, und sie könnten e2fsck mit einem anderen SuperBlock:
        e2fsck -b 8193 <Gerät>




    ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sdb3
    mke2fs 1.41.11 (14-Mar-2010)
    Dateisystem-Label=
    OS-Typ: Linux
    Blockgröße=4096 (log=2)
    Fragmentgröße=4096 (log=2)
    Stride=0 blocks, Stripe width=0 blocks
    12165120 Inodes, 48640803 Blöcke
    2432040 Blöcke (5.00%) reserviert für den Superuser
    Erster Datenblock=0
    Maximale Dateisystem-Blöcke=0
    1485 Blockgruppen
    32768 Blöcke pro Gruppe, 32768 Fragmente pro Gruppe
    8192 Inodes pro Gruppe
    Superblock-Sicherungskopien gespeichert in den Blöcken: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872


    ubuntu@ubuntu:~$ sudo e2fsck -b 11239424 /dev/sdb3
    e2fsck 1.41.11 (14-Mar-2010)
    e2fsck: Das Argument ist ungültig beim Versuch, /dev/sdb3 zu öffnen
    
    SuperBlock ist unlesbar bzw. beschreibt kein gültiges ext2
    Dateisystem.  Wenn Gerät gültig ist und ein ext2
    Dateisystem (kein swap oder ufs usw.) enthält,  dann ist der SuperBlock
    beschädigt, und sie könnten e2fsck mit einem anderen SuperBlock:
        e2fsck -b 8193 <Gerät>
    
    ubuntu@ubuntu:~$ sudo e2fsck -b 20480000 /dev/sdb3
    e2fsck 1.41.11 (14-Mar-2010)
    SuperBlock has an ungültig Journal (Inode 8).
    Bereinige<j>? ja
    
    *** ext3 journal has been deleted - filesystem is now ext2 only ***
    
    Die Dateisystem Größe ( laut SuperBlock) ist 48827559 Blocks
    Die physikalische Größe von Gerät ist 48640803 Blocks
    Entweder der SuperBlock oder die Partionstabelle ist beschädigt!
    Abbrechen<j>? ja
```


I really have no idea if it is the partition table or the superblocks. at first i think i should delete the array with the one device, how do i do that without breaking anything (than it is now :D )? and after that - what should i do next?
thanks in advance guys!
[HR][/HR]EDIT: i just found this [https://bbs.archlinux.org/viewtopic.php?id=136766](https://bbs.archlinux.org/viewtopic.php?id=136766)
i think i also messed something up when creating the array. but when i do sudo e2fsck -cc /dev/md0 it gives me the following error again:

```
    ubuntu@ubuntu:~$ sudo e2fsck -cc /dev/md0    e2fsck 1.41.11 (14-Mar-2010)
    e2fsck: Superblock ungültig versuche es mit Backup-Blöcken...
    e2fsck: Bad magic number in super-block beim Versuch, /dev/md0 zu öffnen
    
    SuperBlock ist unlesbar bzw. beschreibt kein gültiges ext2
    Dateisystem.  Wenn Gerät gültig ist und ein ext2
    Dateisystem (kein swap oder ufs usw.) enthält,  dann ist der SuperBlock
    beschädigt, und sie könnten e2fsck mit einem anderen SuperBlock:
        e2fsck -b 8193 <Gerät>
```

do i have to run resize2fs so the physical and the size of the fs do match again? (i didnt run this command yet)? or is it enough to recreate the array? If you need my outputs to be completely in english let me know, i will try to post them again[/TD]
[/TR]
[/TABLE]

---

### Post by SaturnusDJ on 2013-03-04
What is the output of the following command for the two disks?
```
mdadm --examine /dev/sd*
```

You can probably remove the 1-disk-array from /etc/mdadm/mdadm.conf, but instead, don't remove it yet, just comment it out for now.

---

### Post by callmefunkeyescobar on 2013-03-04
Hey saturnus thanks for your reply,

for sda2 it is: 

```
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ed6394c7:53941634:e368bf24:bd0fce41 (local to host ubuntu)
  Creation Time : Mon Mar  4 02:00:07 2013
     Raid Level : raid1
  Used Dev Size : 194563136 (185.55 GiB 199.23 GB)
     Array Size : 194563136 (185.55 GiB 199.23 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Mar  4 15:41:21 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 389d156f - correct
         Events : 48


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       19        1      active sync   /dev/sdb3


```

for sdb3 it is:

```
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ed6394c7:53941634:e368bf24:bd0fce41 (local to host ubuntu)
  Creation Time : Mon Mar  4 02:00:07 2013
     Raid Level : raid1
  Used Dev Size : 194563136 (185.55 GiB 199.23 GB)
     Array Size : 194563136 (185.55 GiB 199.23 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Mar  4 15:41:21 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 389d1582 - correct
         Events : 48


      Number   Major   Minor   RaidDevice State
this     1       8       19        1      active sync   /dev/sdb3

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       19        1      active sync   /dev/sdb3


```


Testdisk analysis of /dev/md0 brought the following:

```

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/md0 - 199 GB / 185 GiB - CHS 48640784 2 4

The harddisk (199 GB / 185 GiB) seems too small! (< 4393 GB / 4091 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                   18   0  1 48640802   1  4  389126280 [MIRROR]
   HFS                  13680350   1  1 232578758   0  2 1751187262 [^F^E^D^B^A
   Linux                24154473   0  1 72795257   1  4  389126280 [MIRROR]
   Linux                24154533   0  1 72795317   1  4  389126280 [MIRROR]
   Linux                24154601   0  1 72795385   1  4  389126280 [MIRROR]
   Linux                24154674   0  1 72795458   1  4  389126280 [MIRROR]
   Linux                24154742   0  1 72795526   1  4  389126280 [MIRROR]
   Linux                24154815   0  1 72795599   1  4  389126280 [MIRROR]
   Linux                24154895   0  1 72795679   1  4  389126280 [MIRROR]
   Linux                24154964   0  1 72795748   1  4  389126280 [MIRROR]

[ Continue ]
EXT4 Large file Sparse superblock, 199 GB / 185 GiB
```
i will let a deeper search run now. the funny thing is that testdisk shows the name of my old RAID-partition ("MIRROR"). Or does that in that case just means that it is mirrored?

i dont know why it says "The harddisk (199 GB / 185 GiB) seems too small! (< 4393 GB / 4091 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection..."
could that maybe be a GRUB-problem? I had to reinstall GRUB because it was also destroyed while reinstalling

---

### Post by SaturnusDJ on 2013-03-04
I had a better look at the first post. You were working with e2fsck on /dev/sdb3. What about /dev/sda2? And did you create an array after this?

Can you run ```
fdisk -l
``` again to see if it's changed?

---

### Post by callmefunkeyescobar on 2013-03-04
sure, here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3b92028

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       97379   782196786   83  Linux
/dev/sda2           97380      121601   194563215   fd  Linux raid autodetect

Platte /dev/sdb: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c41a682

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        9362    75194336   83  Linux
/dev/sdb2            9362       10199     6724609    5  Erweiterte
/dev/sdb3           10200       34421   194563215   fd  Linux raid autodetect
/dev/sdb4           34515      182401  1187902327+  83  Linux
/dev/sdb5            9362       10199     6724608   82  Linux Swap / Solaris

Platte /dev/sde: 1977 MByte, 1977614336 Byte
64 Köpfe, 63 Sektoren/Spur, 957 Zylinder
Einheiten = Zylinder von 4032 × 512 = 2064384 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sde1               1         957     1929244+   6  FAT16

Platte /dev/md0: 199.2 GByte, 199232651264 Byte
2 Köpfe, 4 Sektoren/Spur, 48640784 Zylinder
Einheiten = Zylinder von 8 × 512 = 4096 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Festplatte /dev/md0 enthält keine gültige Partitionstabelle


```be

before i did create a new array with only /dev/sdb3 and then added /dev/sda2. then the array with the 1 device was gone and i was able to start the new array. after that i runned testdisk because mounting still failed. now the deepscan is running (~90%). i did run e2fsck on both devices and on both it did find a superblock backup, but i wasnt able to rebuild it (see error in the further post). should i try to restore the superblocks with testdisk after its finished?

---

### Post by callmefunkeyescobar on 2013-03-04
okay, the deepersearch just finished, same result as before:
```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/md0 - 199 GB / 185 GiB - CHS 48640784 2 4

The harddisk (199 GB / 185 GiB) seems too small! (< 4393 GB / 4091 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                   18   0  1 48640802   1  4  389126280 [MIRROR]
   HFS                  13680350   1  1 232578758   0  2 1751187262 [^F^E^D^B^A
   Linux                24154473   0  1 72795257   1  4  389126280 [MIRROR]
   Linux                24154533   0  1 72795317   1  4  389126280 [MIRROR]
   Linux                24154601   0  1 72795385   1  4  389126280 [MIRROR]
   Linux                24154674   0  1 72795458   1  4  389126280 [MIRROR]
   Linux                24154742   0  1 72795526   1  4  389126280 [MIRROR]
   Linux                24154815   0  1 72795599   1  4  389126280 [MIRROR]
   Linux                24154895   0  1 72795679   1  4  389126280 [MIRROR]
   Linux                24154964   0  1 72795748   1  4  389126280 [MIRROR]

[ Continue ]
EXT4 Large file Sparse superblock, 199 GB / 185 GiB


```

should i try to rebuild any of them?

---

### Post by SaturnusDJ on 2013-03-04
Maybe it is in use by mdadm or mount.

If so, the choices are treating the md device, or stopping the array and treat a single disk.

Do you have a back-up or image?

---

### Post by callmefunkeyescobar on 2013-03-04
i made an dd-image of the corrupted disk before i started, but i dont have any backups. unfortunately i cant mount the dd-image via loop because then it says > unknown filesystem type 'linux_raid_member'. when i use the type option of mount and put in "ext4" or "autofs" it brings up the error that its either a wrong fs type, option or missing superblock. but i can run testdisk on the dd-imagefile, would that help?

---

### Post by SaturnusDJ on 2013-03-04
You said you think it is ext4. Did you try to mount as ext2/3 already? The e2fsck command says it is ext2 now.

---

### Post by callmefunkeyescobar on 2013-03-04
yeah, i tried to mount it with type ext2 - ext3 - ext4. I ran testdisk on the dd-file and it says "Partition sector doesnt have the endmark 0xAA55". I selected Intel instead of None. But maybe i think wrong here, it is an image of an partition so it isnt partitioned right? 
i read somewhere that a resize could help (because of the error "[COLOR=#000000][FONT=Ubuntu Mono]The harddisk (199 GB / 185 GiB) seems too small! "[/FONT][/COLOR]) but i am afraid that this will destroy everyting

---

### Post by callmefunkeyescobar on 2013-03-04
Thank god i got everything back (at least i hope so, testdisk was listing all my files and is copying them atm).
So here is what i did:

1. i made an DD-Image of one of the RAID1-Partitions (in this case /dev/sdb2).

2. i downloaded and ran testdisk on the IMAGE, NOT the partition itself. ```
sudo ./testdisk_static /path/to/dd-image
```

3. hit enter, selected "none" at partition table type

4. selected analysis and let it run, after that hit enter

5. selected "deeper search" and stopped it by pressing enter as soon as an ext-4 entry showed up

6. selected one of the ext4 entries and pushed "p" for listing files (note: if it says "filesystem damaged" you maybe have to let the deeper search run through and test every entry)

7. selected the folders on  the next page and copied it to another HDD

8. YEAH! made my day. Thanks alot for your help [COLOR=#000000]SaturnusDJ!  Without your support i would have stopped and just started renaming 200GB of files without correct filenames. would have took me ages. Good night guys![/COLOR]

---

### Post by SaturnusDJ on 2013-03-05
Nice job, congratulations!

---

