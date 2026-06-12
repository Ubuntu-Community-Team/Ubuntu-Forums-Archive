---
title: "Adding Windows to Grub loader with Raid5 HD array"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by bungnati on 2009-10-30
Hey guys, I just installed 9.10 x32. It did not add my current XP instalation to the grub loader. Ive tried adding :

title WindowsXP Pro
rootnoverify (hd0,3)
makeactive
chainloader +1

This has not worked, it gives me an error of no partition. Ive tried all the partitions, 0-4 (4 is the ubuntu instalation).

Im using the intel ICH9R raid config in raid 5 (3 drives, parity).

Please help me, I can mount the drive in ubuntu but cant boot into it.

Ive tried "sudo lshw -C disk" but this lists my 3 hd's individually.

 *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-S202N
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: Hitachi HDT72505
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: V56O
       serial: VFK401R4DS77YK
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=2a4d2a4d
  *-cdrom
       description: DVD reader
       product: DVD-E818A3T
       vendor: ASUS
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk:1
       description: ATA Disk
       product: Hitachi HDT72505
       vendor: Hitachi
       physical id: 2
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: V56O
       serial: VFK401R41DP7WK
       size: 465GiB (500GB)
       configuration: ansiversion=5
  *-disk:2
       description: ATA Disk
       product: Hitachi HDP72505
       vendor: Hitachi
       physical id: 3
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: GM4O
       serial: GEB531RE053YPB
       size: 465GiB (500GB)
       configuration: ansiversion=5


Thanks 
John

---

