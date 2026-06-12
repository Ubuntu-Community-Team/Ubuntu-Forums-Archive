---
title: "missing home folder - suspect hard drive?"
date: 2013-05-28
forum: Hardware
---

### Post by D0natell0 on 2013-05-28
Hi,
I'm trying to fix and analyse a system where it repeatedly struggles to boot, and /home folder has disappeared.

I ran a live CD and looking at /var/log/syslog the only errors found:

```
16:55:48 SimsClient1 kernel: [   15.315386] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
////
16:55:48 SimsClient1 kernel: [   15.604165] ACPI: Using IOAPIC for interrupt routing
16:55:48 SimsClient1 kernel: [   15.604302] Error attaching device data
16:55:48 SimsClient1 kernel: [   15.604329] Error attaching device data
```

Looks like I'll have to go to my backups.

Why would the home folder disappear? Is this disk on it's way out?
Thanks for your help.

---

### Post by ahallubuntu on 2013-05-28
Check the disk health with GSmartControl.  You can install this in a Ubuntu live CD (assuming you are connected to the internet) or use a distro like Parted Magic that includes GSmartControl (the icon to launch it on the desktop is called "Disk Health").

Look at the S.M.A.R.T. Attributes tab and see which Attributes if any are highlighted in pink - these are the ones you should be concerned about.  If there are none highlighted, then run "e2fsck" to check the partition(s) on your disk, also from a live CD.

---

### Post by D0natell0 on 2013-05-28
How long should the GSmartControl "extended self-test" take for a 30Gb drive? It's been going for ~3hours and is still showing 10% complete!
The attributes tab is greyed out.

Also is "e2fsck" safe?
Taken from this website:[en.wikipedia.org/wiki/Ext3#Defragmentation]("http://en.wikipedia.org/wiki/Ext3#Defragmentation")  " There is no online ext3 defragmentation tool that works on the  filesystem level. An offline ext2 defragmenter, e2defrag, exists but  requires that the ext3 filesystem be converted back to ext2 first. But  depending on the feature bits turned on in the filesystem, e2defrag may  destroy data; it does not know how to treat many of the newer ext3  features."

Here's the "smart" output:
```

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Indilinx Barefoot based SSDs
Device Model:     OCZ-VERTEX
Serial Number:    J85SG621BZ344T3DDC11
Firmware Version: 1.6
User Capacity:    32,017,047,552 bytes [32.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri May 24 11:22:28 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x1d) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Abort Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x00)    Error logging NOT supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   0) minutes.
Extended self-test routine
recommended polling time:      (   0) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   ---   ---   ---    Old_age   Offline      -       6
  9 Power_On_Hours          0x0000   ---   ---   ---    Old_age   Offline      -       2532
 12 Power_Cycle_Count       0x0000   ---   ---   ---    Old_age   Offline      -       618
184 Initial_Bad_Block_Count 0x0000   ---   ---   ---    Old_age   Offline      -       10
195 Program_Failure_Blk_Ct  0x0000   ---   ---   ---    Old_age   Offline      -       0
196 Erase_Failure_Blk_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       0
197 Read_Failure_Blk_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       0
198 Read_Sectors_Tot_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       2290894141
199 Write_Sectors_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       3359684033
200 Read_Commands_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       52247928
201 Write_Commands_Tot_Ct   0x0000   ---   ---   ---    Old_age   Offline      -       45144422
202 Error_Bits_Flash_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       6739530
203 Corr_Read_Errors_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       6331106
204 Bad_Block_Full_Flag     0x0000   ---   ---   ---    Old_age   Offline      -       0
205 Max_PE_Count_Spec       0x0000   ---   ---   ---    Old_age   Offline      -       5000
206 Min_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       362
207 Max_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       947
208 Average_Erase_Count     0x0000   ---   ---   ---    Old_age   Offline      -       679
209 Remaining_Lifetime_Perc 0x0000   ---   ---   ---    Old_age   Offline      -       87
211 SATA_Error_Ct_CRC       0x0000   ---   ---   ---    Old_age   Offline      -       0
212 SATA_Error_Ct_Handshake 0x0000   ---   ---   ---    Old_age   Offline      -       0
213 Indilinx_Internal       0x0000   ---   ---   ---    Old_age   Offline      -       0

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]
Device does not support Selective Self Tests/Logging

```

---

### Post by ahallubuntu on 2013-05-28
I'm not too experienced with S.M.A.R.T. and SSDs, so I can't comment on your use of it.  But, it sounds like the extended test is stuck.  On a 30GB hard drive, it would take less than an hour.

The fact that "Initial_Bad_Block_Count" has a raw value of 10 (I can guess that means 10 bad blocks?) seems to indicate some sort of issue with your SSD, though.

e2fsck is a tool to correct file system problems, not defrag.  It is "safe" if you run it properly.

---

### Post by D0natell0 on 2013-05-29
Ok, so I tried the following on each partition:

```
sudo e2fsck -p /dev/sda1
```

That reported 'clean'. However, I then tried running testdisk ([TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")), and this extract looks troubling:

```
recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/31, s_mnt_count=0/32, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048241
recover_EXT2: part_size 8385928
     Linux                 3204   0  1  3725 254 61    8385928
     ext3 blocksize=4096 Large file Sparse superblock Backup superblock, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=7/32, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048241
recover_EXT2: part_size 8385928
     Linux                 3436   0  1  3957 254 61    8385928
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB
This partition ends after the disk limits. (start=55199340, size=8385928, end=63585267, disk end=62533296)
     Linux Swap            3726   1  1  3891 254 40    2666704
     SWAP2 version 1, pagesize=4096, 1365 MB / 1302 MiB
Disk /dev/sda - 32 GB / 29 GiB - CHS 3892 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (32 GB / 29 GiB) seems too small! (< 32 GB / 30 GiB)
The following partition can't be recovered:
     Linux                 3436   0  1  3957 254 61    8385928
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

```

What does it mean "The harddisk (32 GB / 29 GiB) seems too small!"
Do I need to run the suggested command "e2fsck -b 98304 -B 4096 device"?
Thanks in advance.

---

### Post by D0natell0 on 2013-06-14
bump

---

