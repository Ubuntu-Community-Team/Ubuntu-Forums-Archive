---
title: "What should I leave out when Restoring Data to Upgraded installation?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by Trent T on 2009-09-09
When my 6-year-old IDE drive (running Ubuntu 8.0.4) seized up, I managed to get it working again long enough to copy all its files to a TAR file backup on new SATA drive-2;

I installed Ubuntu 9.04 on a new SATA drive-1, mounted SATA drive-2, and restored the data from backup.  It mostly worked-- However, when I rebooted the computer, the old boot record for the Ubuntu 8.0.4 drive had supplanted the new boot record!  

I am about to try restoring the data again;
I plan to remove the OLD IDE-Ubuntu-8.0.4 boot directory from the TAR backup first.  This should allow the new boot record to remain intact.
Or am I wrong? :confused:

**Is there any other file I need to REMOVE from my old-system backup to avoid screwing up the new system when I restore the data??**

Any assistance greatly appreciated!
Trent T.

PS--
Technical details:

To Backup data, I followed directions from Heliode's excellent article, 
Howto: Backup and restore your system!, posted 5/17/05;

After becoming root, I changed directory to SATA drive-2, and typed

tar cvpf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=backup.tgz --exclude=/mnt --exclude=/sys /

# Probably should have added, --exclude=/boot  :)

To Restore data the first time around,  I became root again, 
went to SATA drive-2, and typed

tar xvpf backup.tgz -C /

Everything worked well-- I just could not reboot from SATA drive-2...


====================================================================
MY DRIVES:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040540

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18729   150440661   83  Linux
/dev/sda2           18730       19457     5847660    5  Extended
/dev/sda5           18730       19457     5847628+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3592

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003de9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

MY SYSTEM
My system:
OS:  ubuntu Linux 9.04 - Jaunty Jackalope
Motherboard: MSI MS-7366, version: 1.0 width: 32 bits
Firmware BIOS: American Megatrends Inc. version: V3.3 (03/07/2008)64KiB
CPU Intel(R) Celeron(R) CPU  E1200  @ 1.60GHz version: 6.15.13 1600MHz @200MHz
Memory DIMM SDRAM Synchronous 2 GiB width: 64 bits
Audio-Motherboard: MCP73 High Definition Audio, nVidia version: a1
Audio-add-in: SB Live! EMU10k1 by Creative Labs, V.7 33MHz
Hard Drive: Seagate ATA - ST3160815AS size: 149GiB (160GB) partitioned:dos
            capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized 
            configuration: created=2009-09-03 02:15:45 filesystem=ext3 modified=2009-09-03 03:21:47 mounted=2009-09-03 03:21:47 state=clean
            
CD/DVD Read/Write: SATA HP DVD Writer 1070d

Printer - HP Photosmart C4400

---

### Post by mikewhatever on 2009-09-12
Since you had been running 8.04 and now have 9.04, all you really need to restore is your previous home directory.

---

### Post by louieb on 2009-09-12
Since you did a fresh install of 9.04. and just want the data from the tar file. 
Have you though to un-tar it on one of the other drives - browse and copy with nautilus whatever it is you want to keep.

---

### Post by Trent T on 2009-09-23
Thanks louieb--
That's what I ended up doing--
I un-tarred the backup file to a second hard drive, and copied over things that I wanted to save.  
It seems like an inelegant solution, in some ways;
I have had to reinstall some of the software I previously had, such as LaCie lightscribe, and win4lin.  Also, Wanda the Fortune-Telling Fish no longer tells fortunes :-(, but that's a minor problem.

Over-all though, it was so much easier to archive and restore than Win XP and its predecessors..

Thanks to all who commented!!

---

