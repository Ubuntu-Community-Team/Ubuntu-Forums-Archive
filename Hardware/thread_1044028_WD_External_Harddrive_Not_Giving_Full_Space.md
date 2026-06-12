---
title: "WD External Harddrive Not Giving Full Space"
date: 2009-01-19
forum: Hardware
---

### Post by PaulTR on 2009-01-19
Hi. I just got a Ubuntu CD from a teacher of mine at the university, and have been playing with it for the last couple of days, but I have a problem that I haven't been able to quite figure out yet. When I plug in my WD 250gb external hard drive, I get two new icons on my desktop. One is Pauls HD (what the hard drive is called on normal windows machines) and the other is 208.1 GB Media. The first says it only has roughly 36 gigs of space available to it, and I've already used up that much, while the second has a large bit of files in it like root, usr, and some others, even though my internal hard drive is the one I installed Linux on. The first is formatted as vfat, and the second is ext3 (at least that's what's mentioned in preferences). Basically I just want to know how I can merge them to have the full space of the external hard drive in one disk area, while still being able to use the HD on windows machines. If you can't tell, I'm pretty lost and a complete newbie with all this :) Here's some of the output from things I've typed into the terminal after googling the problem. Not sure if any of it is relevent, but can't hurt to give it.


----------------------------------------------------------------------
paul@paul-desktop:~$ sudo fdisk -l
[sudo] password for paul:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d067d06

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4787 38451546 83 Linux
/dev/sda2 4788 4998 1694857+ 5 Extended
/dev/sda5 4788 4998 1694826 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

Device Boot Start End Blocks Id System
/dev/sdb1 1 4818 38700553+ c W95 FAT32 (LBA)
/dev/sdb2 4819 30401 205495447+ 5 Extended
/dev/sdb5 4819 30122 203254348+ 83 Linux
/dev/sdb6 30123 30401 2241036 82 Linux swap / Solaris


------------------------------------------------------------------

paul@paul-desktop:~$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
Model Number: WDC WD2500BEVT-22ZCT0
Serial Number: WD-WXE908EX2983
Firmware Revision: 11.01A11
Transport: Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
Supported: 8 7 6 5
Likely used: 8
Configuration:
Logical max current
cylinders 16383 16383
heads 16 16
sectors/track 63 63
--
CHS current addressable sectors: 16514064
LBA user addressable sectors: 268435455
LBA48 user addressable sectors: 488397168
device size with M = 1024*1024: 238475 MBytes
device size with M = 1000*1000: 250059 MBytes (250 GB)
Capabilities:
LBA, IORDY(can be disabled)
Queue depth: 32
Standby timer values: spec'd by Standard, with device specific minimum
R/W multiple sector transfer: Max = 16 Current = 0
Advanced power management level: 128
Recommended acoustic management value: 128, current value: 254
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
Cycle time: min=120ns recommended=120ns
PIO: pio0 pio1 pio2 pio3 pio4
Cycle time: no flow control=120ns IORDY flow control=120ns
Commands/features:
Enabled Supported:
* SMART feature set
Security Mode feature set
* Power Management feature set
* Write cache
* Look-ahead
* Host Protected Area feature set
* WRITE_BUFFER command
* READ_BUFFER command
* NOP cmd
* DOWNLOAD_MICROCODE
* Advanced Power Management feature set
SET_MAX security extension
* Automatic Acoustic Management feature set
* 48-bit Address feature set
* Device Configuration Overlay feature set
* Mandatory FLUSH_CACHE
* FLUSH_CACHE_EXT
* SMART error logging
* SMART self-test
* General Purpose Logging feature set
* WRITE_{DMA|MULTIPLE}_FUA_EXT
* 64-bit World wide name
* IDLE_IMMEDIATE with UNLOAD
* Segmented DOWNLOAD_MICROCODE
* SATA-I signaling speed (1.5Gb/s)
* SATA-II signaling speed (3.0Gb/s)
* Native Command Queueing (NCQ)
* Host-initiated interface power management
* Phy event counters
DMA Setup Auto-Activate optimization
Device-initiated interface power management
* Software settings preservation
* SMART Command Transport (SCT) feature set
* SCT Long Sector Access (AC1)
* SCT LBA Segment Access (AC2)
* SCT Error Recovery Control (AC3)
* SCT Features Control (AC4)
* SCT Data Tables (AC5)
unknown 206[12] (vendor specific)
unknown 206[13] (vendor specific)
Security:
Master password revision code = 65534
supported
not enabled
not locked
not frozen
not expired: security count
supported: enhanced erase
82min for SECURITY ERASE UNIT. 82min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee25771b4ea
NAA : 5
IEEE OUI : 14ee
Unique ID : 25771b4ea
Checksum: correct
-------------------------------------------------------------------------------

paul@paul-desktop:~$ sudo mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
paul@paul-desktop:~$ sudo mount /dev/sdb1 /media/disk
lspaul@paul-desktop:~$ ls /media/disk
autorun.in_2.org Over 1100 General Computer Ebooks
Books Physics 2B presentations
Default Programs Pictures
Desktop Backgrounds $RECYCLE.BIN
Firefly Season 1 Complete DvdRip Ac3 Recycled
Movies System Volume Information
Music
--------------------------------------------------------------------------------------

---

### Post by vanadium on 2009-01-19
You (or someone else) probably attempted a linux install on the removable drive: there is an ext3 and a swap partition.

You can use gparted to delete the linux partitions. Then you can delete the extended partition and resize the fat partition to occupy the entire disk.

On a side note: it is risky to have a fat partition that large. Fat is an older and quite simple file system that is easily corrupted. If you must also use the disk on Windows, you better use ntfs. A major drawback of ntfs is that only Windows can fully check and repair an ntfs volume. You should therefore use ntfs only if you have ready access to a Windows machine as well.

---

### Post by PaulTR on 2009-01-19
Ah. Yeah, I don't doubt I did that when trying to install it. What commands would I go about using to wipe the drive and set it up like that? I've already moved all the files from the HD onto my computer so I can wipe the entire thing if need be.

---

### Post by vanadium on 2009-01-19
Then your easiest bet will be to remove all partitions and create one partition occupying the entire drive.

You can use gparted for this. gparted is not by default installed in Ubuntu, so install it first using Synaptic Package manager.

Launch gparted with root permissions: Hit Alt+F2, in the dialog enter "gksudo gparted", provide your user password to acquire root privileges and gparted will be started.

You need to select the proper drive with the drop down in the right top corner. Fortunately, because you are working from within your normal system, it will not be easy to delete your root partition by mistake ;)

Before doing anything with a partition, you might need to unmount it first: right-click the partition for that.

Then, you can delete the partition. Right-click the partition for that.

Next to primary partitions, there will be an extended partition containing logical partitions. The logical partitions must be deleted before you can delete the extended partition.

Press "Apply" between every few actions to commit the changes to disk.

Once all space is freed, use the right-click menu to create a new partition. Use the right-click menu to format it. ext3 is the preferred format to use under linux.

---

### Post by PaulTR on 2009-01-19
That worked awesomely, thanks. Only one problem now. It looks like it's still broken into two sections: a 38.28 GiB /dev/sda place and a 232.88 GiB /dev/sdb place. I have the sdb one set up like you said to ext3, and I have the sda unallocated, but how do I merge them so that I have access to all the space on the drive? Or am I just missing some important detail along the way? Thanks.

---

### Post by vanadium on 2009-01-20
sda and sdb are two different drives. sda is the drive containing your system. Do not touch it.

---

