---
title: "RAID 1 clean, degraded: disk not ready at boot"
date: 2014-01-14
forum: Hardware
---

### Post by alberto.montanari on 2014-01-14
Hello everybody,
I am new in the forum, therefore please let me thank you all for the excellent service you are providing. My problem is the following.
I am using kubuntu 12.04 on RAID1 (3 RAID1 on 3 different partitions, on twin hard drives). Last week the pc (which is normally always turned on) crashed for lack of power. At the reboot (as well as at the subsequent reboots) the system told me that one of the drives is not ready yet or not available (the system also tells me the UIID of the drive). I am asked to choose between S (skip) and M (manual recovery) for a few seconds but then the systems starts normally. However, the boot log says:

The system may  have suffered a hardware fault, such as a disk drive failure.  The root  device may depend on the RAID devices being online. One or more of the  following RAID devices are degraded:
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid1 sda3[1]
      942383040 blocks [2/1] [_U]
    
md125 : active raid1 sda1[1]
      24413120 blocks [2/1] [_U]
      
md126 : active raid1 sda2[1]
      4882368 blocks [2/1] [_U]
      
unused devices: <none>
Attempting to start the RAID in degraded mode...
mdadm: CREATE group disk not found
Started the RAID in degraded mode.
fsck da util-linux 2.20.1
fsck da util-linux 2.20.1
fsck da util-linux 2.20.1
udevd[517]: specified group 'pcscd' unknown

/dev/md125: clean, 673498/1525920 files, 2913986/6103280 blocks
/dev/md127: clean, 147254/58900480 files, 48759840/235595760 blocks
/dev/md126: clean, 15396/305216 files, 557567/1220592 blocks

Furthermore, with sudo mdadm --detail /dev/md125 I get the following:

/dev/md125:
        Version : 0.90
  Creation Time : Thu Jun 17 12:40:47 2010
     Raid Level : raid1
     Array Size : 24413120 (23.28 GiB 25.00 GB)
  Used Dev Size : 24413120 (23.28 GiB 25.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 125
    Persistence : Superblock is persistent

    Update Time : Tue Jan 14 00:36:50 2014
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : e098428b:c6943cf3:33757c83:2e22019b
         Events : 0.107152

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        1        1      active sync   /dev/sda1

The missing drive, which originally was /dev/sdb, is not visible through fdisk -l and neither in gparted. I cannot see it in anyway.
Do you kindly have any suggestion to try to recover the drive?
Thank you very much in any case, ciao!  [IMG]http://forum.ubuntu-it.org/images/smilies/ciao.gif[/IMG] 
Alberto

---

### Post by alberto.montanari on 2014-01-14
I made a reboot and now I can see the lost drive. I run a sudo smartctl --all /dev/sda and got the following:

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP4NJJY
LU WWN Device Id: 5 000c50 024602509
Firmware Version: CC38
User Capacity:    1,000,204,886,016 bytes [1,00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Jan 14 16:08:19 2014 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

So I guess I have to order a brand new hard drive. Thanks to RAID I can work meanwhile.
Thanks for your attention!
Best,
Alberto

---

