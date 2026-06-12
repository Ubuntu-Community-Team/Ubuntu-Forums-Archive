---
title: "Accessing the new Seagate 3TB external drive"
date: 2010-07-22
forum: Hardware
---

### Post by pwyll72 on 2010-07-22
Hi Everyone,

So I recently bought one of the new Seagate 3TB external hard drives. (FreeAgent GoFlex Desk, part number STAC3000100) 

Accessing it has been a puzzle.

My understanding is that a normal MBR can only handle partition sizes up to 2.2TB. For larger partitions, what I see is people recommending GPT (GUID Partition Table, [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) ) instead.

One thing that's not clear to me is whether the 2.2TB limit still applies when sectors are 4Kb rather than the normal 512 bytes. At any rate, this thing came formatted with one single NTFS partition, which appears to have a 4K sector size and no GPT, just vanilla MBR.

NTFS is fine with me, as I still boot into my windows partition sometimes and like to be able to access my data from either OS. The way Seagate formatted this, it:

[B]It *is* visible and usable, to my desktop's 32-bit Windows XP install.
It *is* visible, but won't automount, on my desktop's Ubuntu 9.10 (Karmic) x64 install. I'm hesitant to try mounting it manually.
It  *is* visible, and *will* automount, on my laptop's Ubuntu 10.04 (Lucid) x64 install.[/B]

parted (and GParted) seem very confused by the drive.
fdisk seems to understand it OK, as does 10.04's newer version of Palimpsest. (The System->Administration->Disk Utility app.)

I've read that Seagate had figured some format hack such that it was usable on 32-bit XP, but for whatever reason it doesn't seem to be a vanilla NTFS format. Does anyone know if this drive uses Advanced Format ( [http://en.wikipedia.org/wiki/Advanced_Format](http://en.wikipedia.org/wiki/Advanced_Format) ), or is just a standard NTFS format using a 4K sector size?

I'd like to know exactly what's going on with the drive so I can safely format it if needed. [B]I'd like to know how to make:

1. (best option) A single NTFS partition, aligned at 4K sector boundaries, usable by 32-bit windows, 9.10 x64, and 10.04 x64, that does not use GPT.
2. (acceptable) two NTFS partitions, usable by 32-bit windows, 9.10 x64, and 10.04 x64. (again, not using GPT)
I'd also like to avoid upgrading my desktop to 10.04 if possible.[/B] 

One thing I *don't* need to able to do with this drive is boot from it (from either XP or ubuntu) so that at least is one less thing to figure out.

Does anyone have more detail on this drive and the exact partitioning scheme used? **Has anyone else tried to format it? (as NTFS, or even Ext3/Ext4?)**

Any help greatly appreciated! Thanks.

---

### Post by pwyll72 on 2010-08-07
Any ideas? I've posted on Seagate's forums and heard nothing; I even tried submitting a support request there but their html is broken. I've just posted at storagereview's forums as well.

---

### Post by dino99 on 2010-08-07
you should not have issue with linux or w7/vista, only xp need 512's sector but Seagate directly translate from 4k

use the latest partedmagic: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by pwyll72 on 2010-08-08
Thanks for the link to partedmagic, unlike ubuntu the version of hdparm that it comes with can read the drive. For those interested, here are the outputs of fdisk, parted, and hdparm:
[B]
First, results under Ubuntu 9.10 x64 (my default OS)[/B]

*sudo fdisk -l*

```
Note: sector size is 4096 (not 512)

WARNING: The size of this disk is 3.0 TB (3000592977920 bytes).
DOS partition table format can not be used on drives for volumes
larger than (17592186040320 bytes) for 4096-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Disk /dev/sdg: 3000.6 GB, 3000592977920 bytes
1 heads, 7 sectors/track, 104652377 cylinders
Units = cylinders of 7 * 4096 = 28672 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               2   104652001  2930256000    7  HPFS/NTFS
```*sudo parted -l:* No output for this drive!

*palimpsest:* Can see the drive, but can't do anything with it.

*sudo hdparm -I /dev/sdg (or /dev/sdg1):*
```
HDIO_DRIVE_CMD(identify) failed: Invalid exchange
```*Mounting:* canNOT mount the drive from within GUI. Haven't tried using the command line.


**Next, results using an Ubuntu 10.04 LiveCD:**

*sudo fdisk -l:*

```
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
1 heads, 7 sectors/track, 104652377 cylinders
Units = cylinders of 7 * 4096 = 28672 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2   104652001  2930256000    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
```*sudo parted -l:*

```
Model: Seagate FA GoFlex Desk (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      28.7kB  3001GB  3001GB  primary
```*palimpsest:* can see the drive just fine, along with plenty of drive info. Claims the partitioning scheme is MBR (not GPT AFAIK)
[I]
sudo hdparm -I /dev/sdc (or /dev/sdc1):[/I]

```
/dev/sdc:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
```*Mounting:* CAN mount the drive from the GUI.

**hdparm from within partedmagic 5.2 LiveCD:**

*hdparm -I /dev/sdg*
```
/dev/sdg:
SG_IO: bad/missing sense data, sb[]:  72 00 00 00 00 00 00 0a 09 0c 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

ATA device, with non-removable media
        Model Number:       ST33000651AS                            
        Serial Number:      9XK00PE7
        Firmware Revision:  CC95    
        Transport:          Serial
Standards:
        Used: unknown (minor revision code 0x0029) 
        Supported: 8 7 6 5 
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors: 5860533168
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:     2861588 MBytes
        device size with M = 1000*1000:     3000592 MBytes (3000 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: 7200
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Recommended acoustic management value: 128, current value: 128
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
                Write-Read-Verify feature set
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Phy event counters
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12] (vendor specific)
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        488min for SECURITY ERASE UNIT. 488min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c50020701f84
        NAA             : 5
        IEEE OUI        : 000c50
        Unique ID       : 020701f84
Checksum: correct
```Hopefully this will shed more light on how to properly format the drive... but note that hdparm thinks the sector size is 512!                                                  

Does this help? I'm especially curious about the claim of an unaligned  partition, since Seagate claims it's formatted for optimal use with XP  as well.

---

### Post by linux18 on 2010-08-08
just like normal people and cats:

[IMG]http://imgs.xkcd.com/comics/cat_proximity.png[/IMG]



geeks and really big hard drives have the same effect.

I saw the tittle and said " THATS A BIG HARD DRIVE!"

---

### Post by pwyll72 on 2010-08-13
OK, here's what I got from sending a dump of the first 1mb of the drive to, and doing some extra analysis in XP for, a very helpful member of the storagereview forums:

> Well this is interesting... The drive under Windows does show up as a  native USB device with 4K sector size. However, it also has a 512-byte  MBR in the first 1/4 of sector 0. According to the MBR, the first  partition is NTFS and starts at sector 7 (?!) and ends at 732564000 =  2794GB when interpreted as 4K sectors.

It's a pretty simple kludge really, the MBR is *supposed*  to be the first sector on a 512-byte disk but they've just shoehorned  the same 512 bytes into a 4K sector and left the remaining 1536 empty,  counting on the OS not to care that it's a 4K disk when it really should  be a 512-byte disk.

So it's not the NTFS format that's been kludged, it's the partition  table. For all intents and purposes it's a 4K drive, but uses a 512-byte  MBR when it should be using GPT. Windows seems to just read the first  512-bytes to get the partition table and interpret it in 4K mode (which  it really shouldn't). I can understand why older partitioning tools  would be confused by it...

As for getting it accessible under Ubuntu 9.10, I'm not sure if there's a  safe way to do this, as I'm not 100% sure where the problem lies. It  could either be because it doesn't understand the MBR kludge, or that it  doesn't understand 4K sector drives. The hdparm output you gave seems  to point to the latter, though I cant figure out what the info shown by  fdisk is meant to represent (the "Blocks" value seems to be 1KB but the  "Start" and "End" values make no sense whether interpreted as 512-byte,  1KB, or 4KB).

Is there any data currently on the drive? If there's no (important) data  on it I'd try mounting it manually under Ubuntu anyway just to see what  happens. I'm not familiar enough with *nix to know exactly what path it  uses to determine partition layouts for mounting I'm afraid. The proper  way to do this would be to use GPT, but as XP (32-bit) doesn't support  that, it won't help you.And, here's the results of trying to mount:

Ubuntu 9.10 x64: (my current main OS)
```
sudo mount -t ntfs-3g /dev/sdg1 /mnt
``````
Failed to read last sector (732563999): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdg1': Invalid argument
The device '/dev/sdg1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
``````
sudo mount -V

``````
mount from util-linux-ng 2.16 (with libblkid and selinux support)
```Ubuntu 10.04 x64: (boot from LiveCD)

```
sudo mount -t ntfs-3g /dev/sdc1 /mnt
```(works)

```
sudo mount -V
``````
mount from util-linux-ng 2.17.2 (with libblkid and selinux support)
```Does this mean I have to upgrade in order to be able to read/write this drive? Or is there some way to just get away with updating my version of **mount**?

---

### Post by srs5694 on 2010-08-23
First, the 2 TiB limit on MBR partitions is based on the 32-bit nature of the pointers, which refer to sectors. Specifically, 2^32 * 512(-byte sectors) = 2 TiB. If you increase the sector size to 4096 bytes, that raises the MBR's limit to 16 TiB.

Second, I don't own one of these drives, but I did speak with a Seagate engineer (not a tech support drone, an actual engineer) about them the other day. He told me that these drives have ordinary 512-byte physical sectors, but that to work around the MBR limits, they implemented a USB interface that translates the 512-byte physical sectors into 4096-byte logical sectors. This is essentially the opposite of what Western Digital has done with its "Advanced Format" drives, which have 4096-byte physical sectors but 512-byte logical sectors. Thus, you don't need to worry about sector alignment with the Seagate 3 TB drives, and you can use MBR on them.

It sounds, though, as if the conversion that the USB interface is doing might not be working correctly in Linux. If Linux sees the disk as having 512-byte logical sectors where Windows sees it as having 4096-byte logical sectors, then there's no way you'll get the two OSes to agree about how partitions are laid out. It's conceivable that a kernel upgrade or some sort of special driver options would get Linux to see the disk's 4096-byte logical sector size; however, I don't know this for a fact, and I can't offer any more specific advice on how to get Linux to see the disk as having a 4096-byte sector.

Some Linux disk utilities, including at least some versions of libparted (and hence GNU Parted, GParted, and several other tools) have problems with disks that have anything but 512-byte sectors. This is a bug/limitation in libparted specifically. I've seen this personally with magneto-optical (MO) disks with 2048-byte sectors. If this bug has been fixed, then upgrading the relevant tools can fix it. If not, you'll need to use another partitioning tool, such as fdisk (for MBR) or gdisk (for GPT).

If the disk is a standard SATA model inside its enclosure, then you might be able to get it to work by swapping it into a different enclosure and using a USB interface that doesn't do the 512-to-4096 byte translation. This should theoretically make the disk look like a 3 TB drive with 512-byte physical and logical sectors. (Note that this is my own speculation here; I didn't discuss your problem with the Seagate engineer, since I hadn't read this post before I talked with him.) If you do this, you'll really have to switch from MBR to GPT for defining your partitions, but you won't need to do anything else unusual. XP doesn't understand GPT, though, so you won't be able to use the disk with XP. (There is [a third-party GPT driver for Windows XP,](http://www.mediafour.com/products/gptmounter/) but its Web page specifies that it's useful on disks "smaller than 2TB," so I doubt if it would be useful for accessing a 3 TB disk.)

---

