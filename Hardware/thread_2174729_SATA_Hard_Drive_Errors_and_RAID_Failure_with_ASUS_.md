---
title: "SATA Hard Drive Errors and RAID Failure with ASUS Motherboard"
date: 2013-09-15
forum: Hardware
---

### Post by martini3 on 2013-09-15
PROBLEM
I am getting SATA Errors which is causing my RAID6 Array to fail (degrade).

This started happening after I recently replaced my (MSI) motherboard with an ASUS M5A97 R2.0 motherboard.

Is there any way to fix or work around this bug?

CONFIGURATION
Ubuntu 12.04.3 LTS Server.  Using six Seagate 3TB drives (ST3000DM001) set up as a 5 drive RAID 6 (and 1 cold spare).
The drives have 4 primary partitions (bios_grub, two raid, and swap).  There are two RAID6 arrays, md0 is 1G for /boot
and md1 is 2.7T cut up via LVM for the system and data storage.

BACKGROUND
This was working fine for a couple of years.  Because of a motherboard failure I changed to an ASUS motherboard.
After installing the new motherboard, I get the errors below and my RAID array goes into State : clean, degraded.
I have tried removing and adding (via re-add and add) /dev/sde3 into md1 and it always fails in a few seconds.
Using the cold spare to replace the drive resulted in the same errors.  I have also tried changing the SATA cables
and SATA port.  It seems that I have the same issue in both port 5 and port 6. Is there a difference in the controller
between ports 1-4 and ports 5-6?

Searching the web for these errors show lots of people having this issue with various linux distros and laying the blame
on everything from faulty SATA cables to NVIDIA drivers.  The most promising thing I turned up was a Red Hat bug report
Bug 611350 ([FONT=verdana]https://bugzilla.redhat.com/show_bug.cgi?id=611350[/FONT]) from 2010.  The exact error was seen by many with
Fedora 13.  Some reported success with adding "[FONT=courier new]pcie_aspm=off[/FONT]" to the boot options, and the bug was closed with the release
of Fedora 15 which solved the issue for the user. This seems to suggest that there is a bug fix that could be applied to Ubuntu.


ERROR MESSAGES

[FONT=courier new]    kernel:  ata5.00: exception Emask 0x10 SAct 0x1 SErr 0x400000 action 0x6 frozen[/FONT]
[FONT=courier new]    kernel:  ata5.00: irq_stat 0x08000000, interface fatal error[/FONT]
[FONT=courier new]    kernel:  ata5: SError: { Handshk }[/FONT]
[FONT=courier new]    kernel:  ata5.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=courier new]    kernel:  ata5.00: cmd 61/10:00:e0:58:bc/00:00:01:00:00/40 tag 0 ncq 8192 out[/FONT]
[FONT=courier new]    kernel:           res 40/00:00:e0:58:bc/00:00:01:00:00/40 Emask 0x10 (ATA bus error)[/FONT]
[FONT=courier new]    kernel:  ata5.00: status: { DRDY }[/FONT]
[FONT=courier new]    kernel:  ata5: hard resetting link[/FONT]
[FONT=courier new]    kernel:  ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]



[FONT=courier new]   # mdadm --detail /dev/md1[/FONT]
[FONT=courier new]   /dev/md1:[/FONT]
[FONT=courier new]           Version : 1.2[/FONT]
[FONT=courier new]     Creation Time : Thu Mar 21 14:31:23 2013[/FONT]
[FONT=courier new]        Raid Level : raid6[/FONT]
[FONT=courier new]        Array Size : 8757904896 (8352.19 GiB 8968.09 GB)[/FONT]
[FONT=courier new]     Used Dev Size : 2919301632 (2784.06 GiB 2989.36 GB)[/FONT]
[FONT=courier new]      Raid Devices : 5[/FONT]
[FONT=courier new]     Total Devices : 5[/FONT]
[FONT=courier new]       Persistence : Superblock is persistent[/FONT]

[FONT=courier new]       Update Time : Sun Sep 15 21:24:53 2013[/FONT]
[FONT=courier new]             State : clean, degraded[/FONT]
[FONT=courier new]    Active Devices : 4[/FONT]
[FONT=courier new]   Working Devices : 4[/FONT]
[FONT=courier new]    Failed Devices : 1[/FONT]
[FONT=courier new]     Spare Devices : 0[/FONT]

[FONT=courier new]            Layout : left-symmetric[/FONT]
[FONT=courier new]        Chunk Size : 512K[/FONT]

[FONT=courier new]              Name : cathal:1[/FONT]
[FONT=courier new]              UUID : 00588a3b:ddb88169:aea236fa:a1bcf53d[/FONT]
[FONT=courier new]            Events : 50236[/FONT]

[FONT=courier new]       Number   Major   Minor   RaidDevice State[/FONT]
[FONT=courier new]          0       8        3        0      active sync   /dev/sda3[/FONT]
[FONT=courier new]          1       8       19        1      active sync   /dev/sdb3[/FONT]
[FONT=courier new]          2       8       35        2      active sync   /dev/sdc3[/FONT]
[FONT=courier new]          3       0        0        3      removed[/FONT]
[FONT=courier new]          4       8       51        4      active sync   /dev/sdd3[/FONT]

[FONT=courier new]          5       8       67        -      faulty spare   /dev/sde3
[/FONT]


HARDWARE
AUSU M5A97 R2.0
BIOS 1903 07-11-2013 (old 1503 01-16-2013)
AMD SB950 SATA Controller - 6x SATA 6GB/s
Realtek 8111F - 1 GigE LAN
AMD FX-6350 6 Core Processor
six Seagate 3TB drives (ST3000DM001)

---

### Post by martini3 on 2013-09-16
I tried booting with the option: [COLOR=#000000][FONT=courier new]pcie_aspm=off
[/FONT][/COLOR]This did not solve the problem, I still got the same errors.

---

### Post by SaturnusDJ on 2013-09-17
The 6 ports are on the same controller... However, looking at the motherboard, there is a space between 1-4 and 5-6.

[http://en.wikipedia.org/wiki/AMD_900_chipset_series#Southbridge_issues_.28SB9x0.29](http://en.wikipedia.org/wiki/AMD_900_chipset_series#Southbridge_issues_.28SB9x0.29)
Play with some settings in the BIOS. Maybe the BIOS has a hidden menu with advanced settings.

Not easy to say something about this. It's a pain if motherboard are the problem.

---

### Post by martini3 on 2013-09-19
I resolved this by going into the BIOS and turning off many features that I wasn't using. I turned off firewire, com port, AMD Cool'n'Quiet, ... I'm not sure which thing I turned off did the trick, but the system is stable for 12 hours now.  I also turned on IOMMU.

---

