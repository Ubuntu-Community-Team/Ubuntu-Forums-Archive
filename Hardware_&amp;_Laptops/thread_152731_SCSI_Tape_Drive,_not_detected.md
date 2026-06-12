---
title: "SCSI Tape Drive, not detected?"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by Swab on 2006-03-30
I'm setting up a server which has a Mylex AcceleRaid 170 SCSI controller.  During install, after the base system was installed and the machine rebooted, the boot failed complaining it could not find the hard drive array.   Anyway fixed that by adding the DAC960 module to initrd.img

So now the hard drive array is working, but I can't see any device for the tape drive and I have no /proc/scsi folder.   Anyone have any ideas?

---

### Post by Swab on 2006-03-30
OK, so I loaded scsi_md, sg, and st ... I now have a /proc/scsi/scsi file, but it lists no attached devices... dmesg picks up all the SCSI devices, but does not show the tape drive (id 3) as online as shown below:

```

[4294669.954000] DAC960: ***** DAC960 RAID Driver Version 2.5.47 of 14 November 2002 *****
[4294669.954000] DAC960: Copyright 1998-2001 by Leonard N. Zubkoff <lnz@dandelion.com>
[4294669.956000] DAC960#0: Configuring Mylex AcceleRAID 170 PCI RAID Controller
[4294669.956000] DAC960#0:   Firmware Version: 7.00-03, Channels: 1, Memory Size: 32MB
[4294669.956000] DAC960#0:   PCI Bus: 3, Device: 1, Function: 0, I/O Address: Unassigned
[4294669.956000] DAC960#0:   PCI Address: 0xFC000000 mapped at 0xF8802000, IRQ Channel: 24
[4294669.956000] DAC960#0:   Controller Queue Depth: 512, Maximum Blocks per Command: 2048
[4294669.956000] DAC960#0:   Driver Queue Depth: 511, Scatter/Gather Limit: 128 of 257 Segments
[4294669.964000] DAC960#0:   Physical Devices:
[4294669.964000] DAC960#0:     0:2  Vendor: QUANTUM   Model: ATLAS10K3_18_WLS  Revision: 020W
[4294669.964000] DAC960#0:          Wide Synchronous at 40 MB/sec
[4294669.964000] DAC960#0:          Serial Number: 342207047442
[4294669.964000] DAC960#0:          Disk Status: Online, 35880960 blocks
[4294669.964000] DAC960#0:     0:3  Vendor: HP        Model: C1537A            Revision: L708
[4294669.964000] DAC960#0:          Synchronous at 10 MB/sec
[4294669.964000] DAC960#0:     0:4  Vendor: QUANTUM   Model: ATLAS10K3_18_WLS  Revision: 020W
[4294669.964000] DAC960#0:          Wide Synchronous at 40 MB/sec
[4294669.964000] DAC960#0:          Serial Number: 342206345821
[4294669.964000] DAC960#0:          Disk Status: Online, 35880960 blocks
[4294669.964000] DAC960#0:     0:7  Vendor: MYLEX     Model: AcceleRAID 170    Revision: 0700
[4294669.964000] DAC960#0:          Wide Synchronous at 160 MB/sec
[4294669.964000] DAC960#0:          Serial Number:
[4294669.964000] DAC960#0:     0:8  Vendor: QUANTUM   Model: ATLAS10K3_18_WLS  Revision: 020W
[4294669.964000] DAC960#0:          Wide Synchronous at 40 MB/sec
[4294669.964000] DAC960#0:          Serial Number: 342214847174
[4294669.964000] DAC960#0:          Disk Status: Online, 35880960 blocks
[4294669.964000] DAC960#0:   Logical Drives:
[4294669.964000] DAC960#0:     /dev/rd/c0d0: RAID-5, Online, 71761920 blocks
[4294669.964000] DAC960#0:                   Logical Device Initialized, BIOS Geometry: 255/63
[4294669.964000] DAC960#0:                   Stripe Size: 64KB, Segment Size: 8KB
[4294669.964000] DAC960#0:                   Read Cache Disabled, Write Cache Disabled
[4294679.965000] DAC960#0: Physical Device 0:3 Found
[4294679.965000] DAC960#0: Physical Device 0:2 Found
[4294679.966000] DAC960#0: Physical Device 0:4 Found
[4294679.966000] DAC960#0: Physical Device 0:8 Found
[4294679.966000] DAC960#0: Physical Device 0:2 Online
[4294679.966000] DAC960#0: Physical Device 0:4 Online
[4294679.966000] DAC960#0: Physical Device 0:8 Online
[4294679.966000] DAC960#0: Logical Drive 0 (/dev/rd/c0d0) Found
[4294679.966000] DAC960#0: Logical Drive 0 (/dev/rd/c0d0) Online
```


The tape drive was functioning correctly in Windows 2003.

---

### Post by rich257 on 2006-03-30
This thread [http://www.ubuntuforums.org/showthread.php?t=56902](http://www.ubuntuforums.org/showthread.php?t=56902) might help

---

### Post by Swab on 2006-03-30
[QUOTE=rich257]This thread [http://www.ubuntuforums.org/showthread.php?t=56902](http://www.ubuntuforums.org/showthread.php?t=56902) might help[/QUOTE]

Thanks for the reply.. I have seen that thread... but my problem is that there are no devices listed in /proc/scsi/scsi

---

### Post by RayVad on 2008-02-26
Same problem here.
And i can mount  /dev/rd/c0d0 to /media/raid/
Why isn't lsscsi showing those devices?
I have another scsi controller in it and that one is been showed in lsscsi.

Problem is also that i need to use the tape drive on it. I see the information of the drive in dmesg, but it doesn also show up.

Anyone has solved this problem?

Ray

---

