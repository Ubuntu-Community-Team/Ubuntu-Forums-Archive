---
title: "Setting up a DAT tape drive"
date: 2018-08-18
forum: Hardware
---

### Post by gumbo64 on 2018-08-18
Hello everyone,

I am facing the unfortunate situation where I have to get an old dds4 DAT up and running in order to (partially) recover some data i lost-

The machine upon which the DAT was (and still is) installed is a big NAS/Server (wih an Athlon XP processor and 3 Gigs of RAM) which was partially dismantled through the years to reuse some parts.
Besides the DAT (and Adaptec SCSI board) it has two SATA boards, one of which is seen by the system as "Storage" and the other one as SATA RAID. After so many years i don't remember if two of the four disks where configured as a RAID array. 
Anyway, I managed to get the machine up and running and everything seems to works fine (more or less). Actually I did not connect any disk to the SATA RAID board, but this is irrelevant to the topic.

I installed a very light Ubuntu derivative distro upon it (bodhi) due to the old hardware, and since everything seems to run fine, I think I'll keep using the machine as NAS/Storage/Back-Up solution.

One issue I noticed, is that all devices (hard disks, USB drives etc.) are recognized as SCSI devices, which is odd. 
This has no impact on the system functionality, but I think it's worth mentioning as the primary reason why the machine was setup is to recover data out of the DAT tapes, which is indeed a SCSI device, and oddly enough the only one which the system don't seem to recognize. 
I even tried reinstalling the system after the disconnecting the SCSI board but all devices are still recognized as SCSI, and installing Xubuntu and Lubuntu instead of Bodhi with same results. 
Anyway, the problem is not the IDE/SATA/removable USB drives being recognized as SCSI (they work just fine anyway), but the DAT tape not being recognized at all.

The SCSI board is correcty recognized by the system:

```

john@NAS:~$ lspci
00:00.0 Host bridge: NVIDIA Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: NVIDIA Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: NVIDIA Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: NVIDIA Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: NVIDIA Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: NVIDIA Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: NVIDIA Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: NVIDIA Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:02.1 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:02.2 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: NVIDIA Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: NVIDIA Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: NVIDIA Corporation nForce2 AGP (rev c1)
01:07.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:08.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
[COLOR=#ff0000]01:0a.0 SCSI storage controller: Adaptec AIC-7870P/7881U [AHA-2940U/UW/D/S76] (rev 01)[/COLOR]
02:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)

``` 

However the DAT unit is not listed among the SCSI devices (the rest of the drives are among them though even though they are not scsi obviously)

```

john@NAS:~$ lsscsi
[1:0:1:0] cd/dvd TSSTcorp CD/DVDW SH-W162C TS10 /dev/sr0
[2:0:0:0] disk ATA WDC WD80EB-28CGH 4G24 /dev/sda
[3:0:0:0] disk Generic USB SD Reader 1.00 /dev/sdb
[3:0:0:1] disk Generic USB CF Reader 1.01 /dev/sdc
[3:0:0:2] disk Generic USB SM Reader 1.02 /dev/sdd
[3:0:0:3] disk Generic USB MS Reader 1.03 /dev/sde
[4:0:0:0] disk Kingston DataTraveler 3.0 /dev/sdf         

```

dmesg basically offers same results...

[https://paste.ubuntu.com/p/YSn5J8f9TV/](https://paste.ubuntu.com/p/YSn5J8f9TV/)

Hope someone may help in setting up the tape drive and recover my data.

---

