---
title: "/dev/sdc1 is not created"
date: 2008-07-20
forum: Hardware
---

### Post by matc on 2008-07-20
I have a computer with 7 hard disks. 4 of them are SATA Samsung drives and 3 of them are in a mdadm RAID5.

However, when booting the system 1 of the disks never gets the ev-node for its partition created and therefore the raid marks the array as faulty...

what syslog tells me:
```
 Jul 20 16:33:05 darkbox kernel: [    9.921101] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
1841 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
1842 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Write Protect is off
1843 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
1844 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
1845 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
1846 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Write Protect is off
1847 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
1848 Jul 20 16:33:05 darkbox kernel: [    9.921101] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
1849 Jul 20 16:33:05 darkbox kernel: [    9.921101]  sdc: sdc1
1850 Jul 20 16:33:05 darkbox kernel: [   10.121201] sd 2:0:0:0: [sdc] Attached SCSI disk
1851 Jul 20 16:33:05 darkbox kernel: [   10.121201] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

What hdparm says:
```
/dev/sdc:

 Model=SAMSUNG HD501LJ                         , FwRev=CR100-11, SerialNo=S0MUJ1KP943201
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


```


What fdisk says:
```
matc@darkbox:~$ sudo fdisk -l /dev/sdc

Platte /dev/sdc: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

```


But as you can see, there's no /dev/sdc1:
```
matc@darkbox:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdb1  /dev/sdc  /dev/sdd  /dev/sdd1  /dev/sde  /dev/sde1  /dev/sde2  /dev/sde5  /dev/sde6  /dev/sde7  /dev/sdf  /dev/sdf1  /dev/sdg  /dev/sdg1
matc@darkbox:~$ 

```


I have 3 identical 500G Samsung drives, but this "effect" always happens to the same drive....

When starting cfdisk and closing it, the /dev/sdc1 entry is created...

The system uses a 2.6.25.7 kernel made with ubuntu's default .config and kernel.package.

Can anybody help me out ???

---

### Post by CooLGeeK on 2008-07-22
I had a similar problem before.
The problem started when I created a new array using disks or linux raid partitions from an old (and should have been deleted) raid array.

I discovered that an md (raid) superblock exists NOT ONLY in the raid partitions but in the disks itself.
As a result two (2) raid arrays are being created with some common components. The device nodes for those common components are always missing.

When I used the --zero-superblock option of mdadm on the disk (i.e. /dev/sdb) and left the md superblock on the raid partition (i.e. /dev/sdb1), the problem went away.

Try checking all your partitions for the existence of an md superblock by using the --examine option of mdadm.
```
sudo mdadm --examine /dev/sdb1
```
If an md superblock exists on the partition, an info will be shown to you. Otherwise, it will just say:
> mdadm: No md superblock detected on /dev/sdb1

**MAKE SURE** that you only use the --zero-superblock option on the disks or partitions which you are sure that does not belong to any raid array you are trying to create or assemble.

---

