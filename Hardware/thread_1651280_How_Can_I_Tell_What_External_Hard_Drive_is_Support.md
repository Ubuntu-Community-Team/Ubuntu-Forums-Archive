---
title: "How Can I Tell What External Hard Drive is Supported by Ubuntu"
date: 2010-12-22
forum: Hardware
---

### Post by Mindswap1 on 2010-12-22
Hi Guys! I was planning on purchasing a Western Digital - Western Digital My Passport Essential 500GB External USB 2.0 Hard Drive. However I fear that if I do it will not be recognized by Ubuntu. I do not have Windows Installed on my computer, and I would like to keep it that way. So I can I tell that the external hard drive will be supported by Ubuntu or not.

---

### Post by odinb on 2010-12-22
USB drives are normally formatted in FAT or FAT32 for flash drives, and NTFS for bigger drives. This drive you are looking at is most likely formatted in NTFS. Linux will read and write to all of these filesystems.

But if you intend to use it on Linux only, I would recommend to format it to ext4 by using GParted.

To install:
sudo apt-get install gparted

To use:
sudo gparted

Good luck!

---

### Post by efflandt on 2010-12-22
I have a couple of WD Passport 500 GB drives and they work fine for Linux.  I have one set up to boot Linux for my company laptop, because its internal drive already had 4 partitions and I did not want to tamper with that.  The other one I use to test a new Ubuntu version to resolve any potential issues before installing on my internal drive.  So they work fine with any Linux file system.

For example my old desktop PC from 2004 apparently does not like partitions on MB boundaries that became the default in 10.04, so I have to align to cylinder boundaries for its "/" partition for it to boot.  Although, once it boots, it has no trouble auto mounting partitions with any alignment.

But one thing that is still a mystery is why my new desktop PC cannot boot from a partition at the far end of a 500 GB USB drive, when it has no trouble booting Ubuntu at the far end of its 1 TB internal drive (that 500 GB USB drive boots fine on 2 different laptops from 2006).  But the desktop boots fine from the 1st partition on another 500 GB Passport.

If you are going to install Ubuntu on a USB drive, you have to make sure that you install grub to the mbr of the USB drive and not your internal drive.  In Maverick (10.10) you can select where to install grub at the bottom of the manual partitioning screen during install.

---

### Post by odinb on 2010-12-22
> **efflandt said:**
> 
But one thing that is still a mystery is why my new desktop PC cannot boot from a partition at the far end of a 500 GB USB drive, when it has no trouble booting Ubuntu at the far end of its 1 TB internal drive (that 500 GB USB drive boots fine on 2 different laptops from 2006).  But the desktop boots fine from the 1st partition on another 500 GB Passport.

This is likely because of a limitation of Windows/DOS. It cannot boot from anything else than the first partition on a drive.

Linux/GRUB does not have this limitation however...

Read more here: [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)

---

### Post by zigzag77 on 2010-12-23
I have a My Passport Essential with USB 3.0 and have problems with it.  It does not run with a Delock USB 3.0 Express Card in fast USB 3.0  mode. I don't know if it's a problem of the Delock or the WD. I get disk I/O errors with Ubuntu and Windows with USB 3.0. The disk performs well on USB 2.0 ports. The Delock performs well with other USB 2.0 disks.  

A serious shortcoming of the My Passport Essential with USB 3.0 is that it does not support SMART. So I can not really be sure that the USB 3.0 disk is healthy.

The 500 GB WD Elements SE (part number WDBABV5000ABK-00) support SMART, so you can regularly check the disk  health status.

(The WD Elements case is not as slim as the My Passport Essential, but you can stack several WD Elements SE.)

Maybe only the new USB 3.0 variant does not suport SMART. The My Passport Essentials with only an old USB 2.0 interfaces might support SMART.

---

### Post by zigzag77 on 2010-12-24
The original question was: How Can I Tell What External Hard Drive is Supported by Ubuntu?

Answer: You have to test it. Nearly all external USB drives should work if you just want to store data. But some users want more than that.

The best compatibilty check in my opinion is to check, whether the drive appears correctly in **System** --> **Administration** --> **Disk Utility** --> "**View SMART data** and run self tests".

The external USB drive should support hdparm commands for drive health checks.

Most USB drives give an error message:
```
# hdparm -I /dev/sdc

/dev/sdc:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
```This is what we might want: 
```
# hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  active/idle

# hdparm -y /dev/sdb
/dev/sdb:
 issuing standby command

# hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  standby

```To get detailed drive information:
```
# [B]hdparm -I /dev/sdb
[/B] 
/dev/sdb:

ATA device, with non-removable media
    Model Number:       WDC WD3200BMVS-11F9S0                   
    Serial Number:      WD-WXE908KR9999
    Firmware Revision:  01.01A11
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    **LBA48  user addressable sectors:  625142448**
    **Logical/Physical Sector size:           512 bytes**
    device size with M = 1024*1024:      305245 MBytes
    device size with M = 1000*1000:      320072 MBytes (**320 GB**)
    **cache/buffer size  = 8192 KBytes**
    Nominal Media **Rotation Rate: 5400**
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 0
    **Advanced power management level: 128**
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
      ** *    SMART feature set**
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
[B]       *    SMART error logging
       *    SMART self-test
[/B]       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (**1.5Gb/s**)
       ***    Native Command Queueing (NCQ)**
       *    Host-initiated interface power management
       *    Phy event counters
            DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
**       *    SMART Command Transport (SCT) feature set**
       *    SCT Long Sector Access (AC1)
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    106min for SECURITY ERASE UNIT. **106min for ENHANCED SECURITY ERASE UNIT**.
Logical Unit WWN Device Identifier: 50014ee299999647
    NAA        : 5
    IEEE OUI    : 0099ee
    Unique ID    : 259999947
Checksum: correct

```

---

### Post by groovomata on 2010-12-29
> **odinb said:**
> USB drives are normally formatted in FAT or FAT32 for flash drives, and NTFS for bigger drives. This drive you are looking at is most likely formatted in NTFS. Linux will read and write to all of these filesystems.

But if you intend to use it on Linux only, I would recommend to format it to ext4 by using GParted.

To install:
sudo apt-get install gparted

To use:
sudo gparted

Good luck!
Hello, I have a LaCie external hard drive and I'd like to format it, but gparted is asking that I create a partition table and I don't know what type is compatible with ext4. It lists several partition table types including: 
msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, and loop.

Which should I choose to be compatible for ext4?

---

### Post by srs5694 on 2010-12-30
The partition table is a data structure that defines the start and end points for partitions; within a partition, no matter how it's defined, you can store any filesystem you like. Thus, any partition table type can hold an ext4 filesystem.

The question you should be asking is: "Which partition table type should I choose for best compatibility, reliability, and features in the OS(es) I use?" Since you don't say what OS(es) you use, there's no way to answer simply and with certainty. Three partition table types are common on desktop PCs, though:


[list]
[*]**APM** -- The Apple Partition Map (APM; referred to as "mac" in the list you presented) was used on 680x0- and PowerPC-based Macintoshes. If you've got such a system, APM is probably the best choice, particularly if you want to dual-boot between Linux and any version of Mac OS.
[*]**MBR** -- The Master Boot Record (MBR) partition type (referred to as "msdos" in your list) was, and remains, the dominant partition table type on commodity x86 PCs. It's the only table type understood by DOS and older versions of Windows, and so is the best choice if you want to use such an OS.
[*]**GPT** -- The GUID Partition Table (GPT) is the successor to MBR. It's used on computers that use the new Extensible Firmware Interface (EFI) firmware, including Intel-based Macs and some PCs. Windows can't boot from GPT on BIOS-based computers, but Windows Vista and later can read GPT disks. GPT has several minor and one or two major advantages over MBR, so I personally prefer and recommend it whenever you don't need MBR (or APM) for backwards compatibility.
[/list]


For an external disk, which will probably not be a boot disk, any of these will work fine for Linux, but as just suggested, I'd favor GPT for a Linux-only disk. If you need to read the disk in another OS, you may need to use something else.

---

