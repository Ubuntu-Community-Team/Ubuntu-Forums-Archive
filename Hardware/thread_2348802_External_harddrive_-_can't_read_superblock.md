---
title: "External harddrive - can't read superblock"
date: 2017-01-07
forum: Hardware
---

### Post by horsebox2 on 2017-01-07
My external harddrive broke (it wouldn't turn on anymore, so I don't think the actual harddrive is broken, its just an electrical issue) and the harddrive on my desktop computer died. So I opened up the external harddrive and put it into the desktop PC. I need to backup everything thats on it first so I'm on a Live CD, I can't seem to mount the drive though. Running lshw, heres what it says:

```
ubuntu@ubuntu:~$ sudo lshw -class disk -short
H/W path         Device      Class       Description
====================================================
/0/5/0.0.0       /dev/cdrom  disk        DVDRWBD DH-6E2S
/0/5/0.0.0/0     /dev/cdrom  disk        
/0/6/0.0.0       /dev/sda    disk        4142MB ST_M13FQBL
/0/7/0.0.0       /dev/sdb    disk        SCSI Disk
/0/7/0.0.1       /dev/sdc    disk        SCSI Disk
/0/7/0.0.2       /dev/sdd    disk        SCSI Disk
/0/7/0.0.3       /dev/sde    disk        SCSI Disk


```

The 2TB device at /dev/sda is the harddrive. If I try to mount it, heres what it says:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt/backup
mount: /dev/sda: can't read superblock
```

Running sudo fdisk -l, nothing shows up. I tried fsck and heres what happened:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?

```

Heres what parted says:
```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: /dev/sda: unrecognised disk label 

```

Since lshw can detect the drive and its size, I assume the harddrive isn't broken. But I don't know why fdisk -l lists nothing. So the only info I have about the drive right now is lshw:
```
/0/6/0.0.0       /dev/sda    disk        4142MB ST_M13FQBL
```

I tried starting gparted, and an error message came up saying: 
> LibParted Bug Found: Input/output error during read on /dev/sda

Does this mean the drive is broken? Is there anything I can do to diagnose, and possibly fix it?

---

### Post by oldfred on 2017-01-07
You do not mount nor run chkdsk on a drive like sda, but on the partition(s) on the drive.

And parted is showing label error.
Was drive MBR or gpt partitioned?
What format were partition(s)?

 Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by horsebox2 on 2017-01-07
> **oldfred said:**
> You do not mount nor run chkdsk on a drive like sda, but on the partition(s) on the drive.

And parted is showing label error.
Was drive MBR or gpt partitioned?
What format were partition(s)?

 Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

This was a 2TB external harddrive, I didn't partition it or format it or anything. Since it was an external harddrive, it would usually be mounted via USB, now its hooked up through SATA. If partition wizard is a Windows tool, I can't use it since I can only run this PC on a live linux CD. Running hdparm on the drive, I get this info:

```
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       ST_M13FQBL                              
    Serial Number:      QNR_BFW 
    Firmware Revision:  1117F393
Standards:
    Used: ATA/ATAPI-6 T13 1410D revision 2 
    Supported: 6 5 4 
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:    8089950
    LBA48  user addressable sectors:    8089950
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:        3950 MBytes
    device size with M = 1000*1000:        4142 MBytes (4 GB)
    cache/buffer size  = 2048 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Recommended acoustic management value: 254, current value: 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
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
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
Integrity word not set (found 0x0000, expected 0x76a5)


```

---

### Post by oldfred on 2017-01-07
Almost all tools expect a partition table. So you can only mount sda1, not sda.
But some like you have formatted a drive, not a partition and default tools do not work as they want to see a partition table.

You in effect converted drive to one large floppy drive, that does not have partition table.

What format was it, FAT32, NTFS, or ext4?

If FAT32 you can try this, if sda:
 mount superfloppy fat formatted.
mount -t vfat /dev/sda /media/disk/

---

### Post by horsebox2 on 2017-01-07
Its a Buffalo HD-LBU2, I think its NTFS. Trying to mount with vfat gave the same error about the super block. But trying to mount with -t ntfs, I got this message:
> Error reading bootsector: Input/output error
Failed to mount '/dev/sda': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.



So I take it that means its NTFS. So I tried ntfsfix, and heres what happened:
> ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda
Mounting volume... Error reading bootsector: Input/output error
FAILED
Attempting to correct errors... Error reading bootsector: Input/output error
FAILED
Failed to startup volume: Input/output error
Error reading bootsector: Input/output error
Volume is corrupt. You should run chkdsk.



I wonder can I install chkdsk on WINE. I have no other way to access this drive through Windows.

---

### Post by oldfred on 2017-01-07
Well if ntfsfix ran, you may need Windows.
It cannot do much to fix NTFS as that is Windows. So it turns on the chkdsk flag so when you boot into Windows it will run chkdsk. Some third party Windows repair disks may be able to run chkdsk.

Best not to use a Windows format in Linux unless also dual booting. NTFS need regular maintenance like chkdsk and defrag. Plus when it starts to get full like over 70% it gets slow.

Using google your error seems common but posts are 3 or 4 years old. How old is drive? And one mentions Buffalo was out of business, so warrantee not being honored. 
 EASEUS Partition Master - Windows .exe
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html) 
   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

### Post by horsebox2 on 2017-01-07
I have thousands of files on there, so I wanna recover the data from the drive if possible. It'd be a massive shame to lose all that. I suppose I'll have to try some of these bootable USB methods. For recovering the data though, I came across a tool called ddrescue. It copies the data from the device to another device, attempting to recover the good sectors of data.

---

