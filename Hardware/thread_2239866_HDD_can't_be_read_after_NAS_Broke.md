---
title: "HDD can't be read after NAS Broke"
date: 2014-08-16
forum: Hardware
---

### Post by chippen on 2014-08-16
Hello,

I am sorry if this is a recuring question, I have tried to find a solution but have not been able to find anything for my particular problem.
So this is the story.

I own a Netgear NAS that has been running for some time witha  3 TB HDD. Yesterday the NAS stopped working an the interface said "corrupt root". After looking into the problem I realised that most people had solved the issue by doing a factory reset and thus a refomat of the drive. But I would rather not reformat the drive as I have stuff on it. So I thought, this NAS has been nothing but trouble and it sucks.

I stuck the HDD into my desktop and booted Ubuntu in the hope of saving the content of the drive. The drive should be formated as ext3 if I am not misstaken.

I was a bit stumped to find that Ubuntu fails to read the disc. 
In BIOS the disc is registered but it shows up as around 3GB big.
GParted says Input/output error reading on /dev/sdc

lsblk (note that I have no cdrom drive):
sde      8:64   1   7.7G  0 disk 
&#9492;&#9472;sde1   8:65   1   7.7G  0 part /cdrom  

sudo fdisk -l

Disk /dev/sde: 8210 MB, 8210350080 bytes
255 heads, 63 sectors/track, 998 cylinders, total 16035840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048    16035839     8016896    b  W95 FAT32


Something is clearly wrong with it. The sizes of the different listings is not even the same.
fdisk also lists it as FAT32, this should be wrong, but I can not be sure what the NAS has acctually done with it in terms of partitions.
Does anyone have an idea?
Any help is greatly appreciated.

---

### Post by steeldriver on 2014-08-16
Hello and welcome to the forums

What model Netgear exactly? some of them are SPARC based and use a filesystem block size that may not be (easily) readable under x86 Linux

You may find that parted does a better job than fdisk

```

sudo parted -l

```

Are there any relevant error messages e.g. in the dmesg log?

---

### Post by chippen on 2014-08-16
Thank you, and sorry about the incomplete information.
It is a rndu2000 with intel atom
[http://www.netgear.be/service-provider/products/storage/residential-soho/RNDU2000.aspx#two]("http://www.netgear.be/service-provider/products/storage/residential-soho/RNDU2000.aspx#two")

The parted command does not show sde at all. (see attachment)

I can't see anything i dmesg log (but I am not sure what to look for).
The file was to big so here is a pastebin with the log
[http://pastebin.com/SawTUGan]("http://pastebin.com/SawTUGan")

---

### Post by steeldriver on 2014-08-16
Well I don't really know how to read those low-level log messages but I suspect that the repeated instances like

```

ata6.00: failed command: READ DMA
ata6.00: cmd c8/00:02:06:00:00/00:00:00:00:00/e0 tag 25 dma 1024 in

        res 51/04:02:06:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)

ata6.00: status: { DRDY ERR }

ata6.00: error: { ABRT }


```

do not bode well. You could try installing the smartmontools package and then running

```

smartctl --scan

```

as an alternative method to try to see the block device name, and then if that succeeds

```

sudo smartctl --health /dev/sdX

```

(replacing X by the appropriate letter)

---

### Post by chippen on 2014-08-16
It seems I got confused about the drives. In fact sde was the flashdrive with the ubuntu. Sorry.

In fact the broken drive is sdc
Here is output

ubuntu@ubuntu:~/Documents$ smartctl --scan
/dev/sda -d scsi # /dev/sda, SCSI device
/dev/sdb -d scsi # /dev/sdb, SCSI device
/dev/sdc -d scsi # /dev/sdc, SCSI device
/dev/sdd -d scsi # /dev/sdd, SCSI device
ubuntu@ubuntu:~/Documents$ sudo smartctl --health /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Read SMART Data failed: scsi error aborted command

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: UNKNOWN!
SMART Status, Attributes and Thresholds cannot be read.

---

### Post by steeldriver on 2014-08-16
Sorry that's all I got - hate to say it but I think that short of physical tricks (like freezing) it's probably a dead drive 

You might try attaching it to a different SCSI data port just in case the fault is on the MOBO side - but that's a faint hope, since you already know the drive didn't read in the NAS enclosure either

---

### Post by chippen on 2014-08-16
Yea, I believe you are right. 
I really appreciate your effort though!

---

