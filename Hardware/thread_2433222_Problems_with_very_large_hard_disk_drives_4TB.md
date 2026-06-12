---
title: "Problems with very large hard disk drives: 4TB"
date: 2019-12-15
forum: Hardware
---

### Post by durward2 on 2019-12-15
My computer (home build)
        motherboard: Asus M5A78L-M, chipset: AMD RS780, BIOS: AMI 1303
        CPU: AMD FX-8320 x 8 @ 3.5GHz
        RAM: 8GB, DDR3: PC3-10600
        IDE PCI board:
                40GB: Maxtor 6L040J2
                80GB: WD800JB
        SATA on motherboard
                2.0TB: Western Digital WD20EZEX
                3.0TB: Hitachi HUA72303
        ATAPI DVD-RW
        Video: NVidia GeForce 210
                VGA: Samsung
                DVI: Samsung
        OS: Ubuntu 18.04.03 LTS, Linux 4.15.0-73


Using a JMicron SATA to USB plug and power supply
        I connected a Western Digital WD Blue WD40EZRZ SATA 6Gb/s
        I first plugged it into a Microsoft Surface Pro running Windows 10 
        (up to date as of today: 15 December 2019) and started the program 
        CrystalDisk to check the drive. It had been formatted to NTSF. I moved 
        two data files to the drive; the surface pro read the data files into 
        NotePad easily. The partition appears to be GUID


        I connected it to my Linux computer (specs above) and the Disks program
        showed it to be a 1.8TB, partitioning unknown (PMBR); the fdisk -l program
        also showed it to be a 1.8TB with unknown partitions; the graphical GParted
        would not read the drive. sfdisk would not read the disk. cfdisk would not 
        read the disk; parted would not read the disk.


Is there a problem with Ubuntu 18.04.03 and very large disk drives?
Is the problem in the USB driver in reading very large disk drives?

I also had similar problems with a new/unused 3TB HGST SATA drive (HUA723030ALA640). 
It showed as an 801GB drive with all Linux partition programs and also under Windows 10 Disk Manager.

---

### Post by TheFu on 2019-12-15
Linux has supported huge disks for longer than Windows has.  Have many 4TB and a few 8TB disks connected via SATA and USB to a 16.04.6 machine here.  No issues.  One of the 4TB disks was used in a 12.04 system. No issues.  The only trick I found was using current disk/usb controllers and ensuring the partition table is GPT.  MBR/MSDOS partition tables are limited to 2G or less.

Use **gparted** to create a fresh GPT partition table, then create 1 partition and format it with EXT4 as the file system.  Hopefully that will fix any issues.

Suspect the GPT partition table is corrupt OR the jmicron hardware doesn't support the large disk without some specific driver that is only supported via Windows.  I'd look for BIOS updates first for all the different hardware - motherboard, northbridge, southbridge.  IDE is really old. Haven't see that since around 2010-ish.

Have a *JMicron USA Technology Corp. JMS567 SATA 6Gb/s bridge* that works fine with any huge storage I've connected.

Picked up an new 8TB USB3 disk a few weeks ago. Tomorrow I'll plug it into a Core i5-750 box - that's 2010 era - and see how it sees it. No JMicron stuff in that machine, but there are these:
* ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
* VIA Labs, Inc. VL812 Hub   <--- this has caused problems previously. There's a firmware update needed, but it is only available through Windows with a USB3 port, which I don't have.

I don't have any 18.04 physical installations.

Come to think about it - Windows has a few settings that will prevent Linux from accessing disks.  Fast Startup and Hibernation.  Boot into Windows and ensure those are both disabled.  Any dual-boot how-to guide should cover the exact settings you need to check and disable. Read earlier that MSFT will re-enable them after certain patches too, so this might be a monthly check when storage isn't available inside Linux systems.

---

### Post by oldfred on 2019-12-15
It may even be an unpartitioned drive? Or from Linux it would be a very, very large floppy drive.

Some also use proprietary partitioning to work around XP;s lack of support for large drives.
And some adapters do not support gpt, or large drives.

If FAT32, change to NTFS if not FAT32 and drive at sdd, change to yours
       mount superfloppy fat formatted.
mount -t vfat /dev/sdd /media/disk/

---

### Post by vanadium on 2019-12-16
Before trying anything else, have the partition connected to a Windows system and do a file system check and repair there. Changes are high that after that, it will work as expected under Linux.

---

### Post by durward2 on 2019-12-16
I used dd to clear the beginning of the hard drive; it is supposed to remove mbr and gpt; the drive is /dev/sdf, so I typed "sudo dd if=/dev/zero of=/dev/sdf bs=512 count=20" and repeated it three or four times.
Then I used parted: "sudo parted /dev/sdf" and then "print"; the results shows: Disk /dev/sdf: 1802GB.
Parted display:
(parted) print                                                            
Model: WDC WD40 EZRZ-00GXCB0 (scsi)
Disk /dev/sdf: 1802GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1802GB  1802GB  ext4         WD4T


(parted)

---

### Post by durward2 on 2019-12-16
I connected the drive using my JMicron SATA to USB device to my Microsoft Surface Pro with Windows 10. I checked to see how Windows recognized the drive: drive E:. Then I started the command prompt running as administrator; then I did a file system check; it repaired the drive E:. Now is has an NTFS partition of size 1.8TB, not 4TB. The linux recognized the 1.8TB partition. The Disks program in Linux and GParted in Linux showed a full partition of 1.8TB; now 2.2TB are missing. Any more ideas for me to try?

---

### Post by oldfred on 2019-12-16
Post these, if sdf, now that you "fixed" it:
sudo gdisk -l /dev/sdf
sudo parted -l
sudo fdisk -lu
Each shows slightly different info.

But limit of about 2TB, is typical of MBR partitions which have a 2TiB limit. You have to use gpt.

---

### Post by TheFu on 2019-12-16
JMicron SATA to USB  is the _most likely_ issue.
[https://superuser.com/questions/1357943/wd-blue-4tb-not-recognized](https://superuser.com/questions/1357943/wd-blue-4tb-not-recognized)

```
Model: WDC WD40 EZRZ-00GXCB0 (scsi)
Disk /dev/sdf: 1802GB
Sector size (logical/physical): **512B/512B**
Partition Table: gpt
Disk Flags:

Number Start End Size File system Name Flags
1 1049kB 1802GB 1802GB ext4 WD4T
```
The sector size being reported is wrong.  4TB disks are AF.

Need to see fdisk -l show[LIST]
[/LIST]
:
```

Disk /dev/sdf: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / **4096 bytes**
I/O size (minimum/optimal): **4096 bytes / 4096 bytes**
Disklabel type: gpt
Disk identifier: 3C455EB8-zzzz-xxxx-yyyy-291F94BAAAAD

Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 7814035455 7814033408  3.7T Linux LVM

```

---

