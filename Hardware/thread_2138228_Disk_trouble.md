---
title: "Disk trouble?"
date: 2013-04-23
forum: Hardware
---

### Post by ArminasAnarchy on 2013-04-23
Hi all!

I'm reposting since the General Help forum hasn't helped.

To summarise:

I'm getting this annoying error through GParted in PartedMagic (I booted into PartedMagic after the disk fails to boot, the PC POSTs then I get as "DISK BOOT FAILURE. INSERT SYSTEM DISC" error). The error reads:[CENTER]
_**Libparted bug found!**_
Invalid partition table -recursive partition on /dev/sdb.
[/CENTER]
 
(Options are "Cancel" and "Ignore", I've just gone for "Ignore" previously.)

Since the installation (Xubuntu Alternate, 12.04) from USB proceeds smoothly, I'm assuming this error is the source of the trouble, but I'm running out of ideas about what to do with it (and don't really understand what's wrong).

I've tried re-creating the partition table (it's not a GPG/MSDOS issue - I'm using MSDOS and in any case, Xubuntu would be the only OS), formatting the disk and starting from scratch (using the "Erase Disk" GUI in PartedMagic - which uses dd to write the whole disk to 0, also done using the "internal" thing from the Erase Disk utility), and each and everytime it fails - and that error keeps showing up in GParted. This must be getting on for the 10th time I've tried to install a working OS to this disk.  I've tried running the "grub doctor" utility too, which comes back without problems, but the disk still won't boot.

A quick note on the disk - it's passed both the short and long tests, and (as mentioned) writing to the disk seems to proceed smoothly during install. So AFAIK, the disk is working. BUT: it is ancient, and salvaged out of an even older computer. I've just had the idea that there might be an issue with the firmware - but I'm really scraping the barrel now, and have no idea if that will yield results.

Googling the error returned [this]("https://bbs.archlinux.org/viewtopic.php?id=149001") link, from the Arch wiki site. I've looked at the fdisk output (I'll post that in the next post) and the partitions seem to be there and fine.


Thanks,

AA.

To do:

Check firmware. Can it be upgraded?
Try formatting with the Windoze 7 installer and see what can install/boot.
Check IDE cables and power cables, unplug all other drives.
Suggestions?

---

### Post by ArminasAnarchy on 2013-04-23
fdisk output, as promised:

root@partedmagic:~# fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7813119     3905536   82  Linux swap
/dev/sda2         7813120    37109759    14648320   83  Linux
/dev/sda3        37109760   160835583    61862912   83  Linux

As stated, I'm not seeing any problems.

---

### Post by ArminasAnarchy on 2013-04-23
Just realised - the GParted error is referring to the PartedMagic USB (made with dd). So I'm officially not getting any bugs/error messages for the drive (/dev/sda) that's got the OS installed on it at all. Seriously clueless now!

---

### Post by tgalati4 on 2013-04-23
Once booted into a Live session, install smartmontools and get the SMART parameters from the drive:

Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

This assumes that the old disk drive is on /dev/sda.  It's an old drive, so anything is possible.

---

### Post by ArminasAnarchy on 2013-04-23
I'm on PartedMagic, the installer I have is a CLI "alternate" image - no live session option. PartedMagic responds with the following output when the 'smartctl' command is run:

smartctl 6.0 2012-10-10 r3643 [x86_64-linux-3.7.9-pmagic64] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Device Model:     ExcelStor Technology J880
Serial Number:    PFD210K2BYJK1B
LU WWN Device Id: 0 000000 000000000
Firmware Version: PF2OA21B
User Capacity:    82,348,277,760 bytes [82.3 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 T13/1532D revision 1
Local Time is:    Tue Apr 23 17:15:53 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 1828) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  31) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   119   119   024    Pre-fail  Always       -       163 (Average 171)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1821
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       2435
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1796
192 Power-Off_Retract_Count 0x0032   099   099   050    Old_age   Always       -       1826
193 Load_Cycle_Count        0x0012   099   099   050    Old_age   Always       -       1826
194 Temperature_Celsius     0x0002   189   189   000    Old_age   Always       -       29 (Min/Max 12/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       3

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2435         -
# 2  Extended offline    Completed without error       00%      2433         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

It seems to be saying there's nothing wrong with the disk? I double checked, PartedMagic is marking the harddrive in question as /dev/sda, sdb is my PartedMagic USB.

---

### Post by ArminasAnarchy on 2013-04-23
The plot thickens! The Windoze installer works, but the boatloader STILL fails to pull the files from the drive.

---

