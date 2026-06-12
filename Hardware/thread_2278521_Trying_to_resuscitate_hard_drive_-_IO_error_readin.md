---
title: "Trying to resuscitate hard drive - IO error reading journal superblock"
date: 2015-05-17
forum: Hardware
---

### Post by benjitz on 2015-05-17
Hello!

A large weight fell on my laptop the other day, and ever since I've been getting read errors here and there on the hard drive while booting, and before long the OS switches to read-only. So I duly made a live cd and booted off there to try and see if I could fix it with fsck or e2fsck (trying to mark all the bad blocks to ignore them in future)

After reading a lot about the experiences I've been having, I decided it is best/safest to get a new hard drive and copy my home directory onto it, giving up the old hdd for good. However I think I may have accidentally rendered it totally unreadable by corrupting the superblock somehow when I was trying to fix things with e2fsck, as it will no longer mount when booted into the livecd.

The error I receive when mounting under ubuntu is:
```
Error mounting /dev/dm-1 at /media/ubuntu/14c2678d-44a8-465f-bb5e-4e45a4d61b1f1: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-1" "/media/ubuntu/14c2678d-44a8-465f-bb5e-4e45a4d61b1f1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu--vg-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg gives:

```
[223858.564949] ata1.00: exception Emask 0x0 SAct 0x20 SErr 0x0 action 0x0
[223858.564962] ata1.00: irq_stat 0x40000008
[223858.564971] ata1.00: failed command: READ FPDMA QUEUED
[223858.564989] ata1.00: cmd 60/08:28:00:c0:4b/00:00:0e:00:00/40 tag 5 ncq 4096 in
[223858.564989]          res 41/40:08:00:c0:4b/00:00:0e:00:00/6e Emask 0x409 (media error) <F>
[223858.564997] ata1.00: status: { DRDY ERR }
[223858.565003] ata1.00: error: { UNC }
[223858.567196] ata1.00: configured for UDMA/100
[223858.567229] sd 0:0:0:0: [sda] Unhandled sense code
[223858.567235] sd 0:0:0:0: [sda]  
[223858.567240] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[223858.567245] sd 0:0:0:0: [sda]  
[223858.567249] Sense Key : Medium Error [current] [descriptor]
[223858.567257] Descriptor sense data with sense descriptors (in hex):
[223858.567261]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[223858.567282]         0e 4b c0 00 
[223858.567292] sd 0:0:0:0: [sda]  
[223858.567299] Add. Sense: Unrecovered read error - auto reallocate failed
[223858.567305] sd 0:0:0:0: [sda] CDB: 
[223858.567308] Read(10): 28 00 0e 4b c0 00 00 00 08 00
[223858.567327] end_request: I/O error, dev sda, sector 239845376
[223858.567385] ata1: EH complete
[223858.567400] JBD2: IO error reading journal superblock
[223858.567418] EXT4-fs (dm-1): error loading journal
```

The partition mounted fine before I started fiddling with e2fsck, like an idiot.
There is a grub partition on the drive too which still mounts fine.

The file system on the OS partition (/dev/sda5) is encrypted with crypto_LUKS. I used [this]("http://www.cyberciti.biz/faq/howto-centos-rhel-fedora-debian-fsck-ext3-on-luks-volume/") method successfully so e2fsck could access it.

Would someone be able to walk me through what I would be able to do in order to mount this partition again so I can copy the data off it? If it is not possible, oops, I live and learn :( I have installed smartmontools if you need further information. Thanks in advance!

---

### Post by tgalati4 on 2015-05-17
Welcome to the forums.

Post the output of:

```
sudo smartctl -a /dev/sda
```

Not reading the journal was a symptom.  The problem, according to dmesg, was that your hard drive could not reallocate a bad sector--probably because there were too many to move around, or some other mechanical error.  

Boot off of a live session, connect to the internet and install *testdisk*.  Get some large flash drives and use *testdisk* to recover the file structure and *photorec* to recover individual files if the file structure is not readable.  You will know soon enough.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

```
sudo apt-get install testdisk
man testdisk
```

Don't reboot, because *testdisk* is in RAM.

---

### Post by benjitz on 2015-05-17
Many thanks for the swift response, tgalati4

I'll have a read of the link and look at testdisk shortly, but in the mean time, here is the output of sudo smartctl -a /dev/sda

```
ubuntu@ubuntu:/cdrom$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..55GSX
Device Model:     TOSHIBA MK2555GSXF
Serial Number:    99MEP0KFT
LU WWN Device Id: 5 000039 202808669
Firmware Version: FH205B
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 1.5 Gb/s
Local Time is:    Sun May 17 18:06:34 2015 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.
SCT capabilities: 	       (0x0039)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   099   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1010
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       6618
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1710
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       8448
 10 Spin_Retry_Count        0x0033   232   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3728
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       361
192 Power-Off_Retract_Count 0x0032   097   097   000    Old_age   Always       -       1682
193 Load_Cycle_Count        0x0032   071   071   000    Old_age   Always       -       294583
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       50 (Min/Max 4/56)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1691
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       529
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       4142
222 Loaded_Hours            0x0032   082   082   000    Old_age   Always       -       7337
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       321
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       1562

SMART Error Log Version: 1
ATA Error Count: 10361 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 10361 occurred at disk power-on lifetime: 8447 hours (351 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 62 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 60 00 c0 4b 40 08   2d+18:28:35.398  READ FPDMA QUEUED
  60 08 58 08 e1 07 40 08   2d+18:28:35.395  READ FPDMA QUEUED
  60 08 50 10 e1 07 40 08   2d+18:28:35.395  READ FPDMA QUEUED
  60 08 48 78 c0 07 40 08   2d+18:28:35.392  READ FPDMA QUEUED
  60 08 40 70 c0 07 40 08   2d+18:28:35.392  READ FPDMA QUEUED

Error 10360 occurred at disk power-on lifetime: 8445 hours (351 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 2a 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 28 00 c0 4b 40 08   2d+15:48:12.022  READ FPDMA QUEUED
  60 08 20 08 e1 07 40 08   2d+15:48:12.011  READ FPDMA QUEUED
  60 08 18 10 e1 07 40 08   2d+15:48:12.011  READ FPDMA QUEUED
  60 08 10 78 c0 07 40 08   2d+15:48:12.008  READ FPDMA QUEUED
  60 08 08 70 c0 07 40 08   2d+15:48:12.007  READ FPDMA QUEUED

Error 10359 occurred at disk power-on lifetime: 8445 hours (351 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 82 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 80 00 c0 4b 40 08   2d+15:47:50.487  READ FPDMA QUEUED
  60 08 78 08 e1 07 40 08   2d+15:47:50.480  READ FPDMA QUEUED
  60 08 70 10 e1 07 40 08   2d+15:47:50.480  READ FPDMA QUEUED
  60 08 68 78 c0 07 40 08   2d+15:47:50.479  READ FPDMA QUEUED
  60 08 60 70 c0 07 40 08   2d+15:47:50.479  READ FPDMA QUEUED

Error 10358 occurred at disk power-on lifetime: 8444 hours (351 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3a 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 00 c0 4b 40 08   2d+15:10:18.906  READ FPDMA QUEUED
  60 08 30 08 e1 07 40 08   2d+15:10:18.898  READ FPDMA QUEUED
  60 08 28 10 e1 07 40 08   2d+15:10:18.898  READ FPDMA QUEUED
  60 08 20 78 c0 07 40 08   2d+15:10:18.895  READ FPDMA QUEUED
  60 08 18 70 c0 07 40 08   2d+15:10:18.895  READ FPDMA QUEUED

Error 10357 occurred at disk power-on lifetime: 8444 hours (351 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 32 f8 5f a4 6c  Error: UNC at LBA = 0x0ca45ff8 = 212099064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 30 f8 5f a4 40 08   2d+15:10:06.777  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00   2d+15:10:06.777  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00   2d+15:10:06.777  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00   2d+15:10:06.776  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   2d+15:10:06.776  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      8360         -

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

```

---

### Post by benjitz on 2015-05-17
Many thanks for the swift response, tgalati4

I'll have a read of the link and look at testdisk shortly, but in the mean time, here is the output of sudo smartctl -a /dev/sda

```
ubuntu@ubuntu:/cdrom$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..55GSX
Device Model:     TOSHIBA MK2555GSXF
Serial Number:    99MEP0KFT
LU WWN Device Id: 5 000039 202808669
Firmware Version: FH205B
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 1.5 Gb/s
Local Time is:    Sun May 17 18:06:34 2015 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.
SCT capabilities: 	       (0x0039)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   099   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1010
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       6618
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1710
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       8448
 10 Spin_Retry_Count        0x0033   232   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3728
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       361
192 Power-Off_Retract_Count 0x0032   097   097   000    Old_age   Always       -       1682
193 Load_Cycle_Count        0x0032   071   071   000    Old_age   Always       -       294583
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       50 (Min/Max 4/56)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1691
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       529
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       4142
222 Loaded_Hours            0x0032   082   082   000    Old_age   Always       -       7337
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       321
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       1562

SMART Error Log Version: 1
ATA Error Count: 10361 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 10361 occurred at disk power-on lifetime: 8447 hours (351 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 62 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 60 00 c0 4b 40 08   2d+18:28:35.398  READ FPDMA QUEUED
  60 08 58 08 e1 07 40 08   2d+18:28:35.395  READ FPDMA QUEUED
  60 08 50 10 e1 07 40 08   2d+18:28:35.395  READ FPDMA QUEUED
  60 08 48 78 c0 07 40 08   2d+18:28:35.392  READ FPDMA QUEUED
  60 08 40 70 c0 07 40 08   2d+18:28:35.392  READ FPDMA QUEUED

Error 10360 occurred at disk power-on lifetime: 8445 hours (351 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 2a 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 28 00 c0 4b 40 08   2d+15:48:12.022  READ FPDMA QUEUED
  60 08 20 08 e1 07 40 08   2d+15:48:12.011  READ FPDMA QUEUED
  60 08 18 10 e1 07 40 08   2d+15:48:12.011  READ FPDMA QUEUED
  60 08 10 78 c0 07 40 08   2d+15:48:12.008  READ FPDMA QUEUED
  60 08 08 70 c0 07 40 08   2d+15:48:12.007  READ FPDMA QUEUED

Error 10359 occurred at disk power-on lifetime: 8445 hours (351 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 82 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 80 00 c0 4b 40 08   2d+15:47:50.487  READ FPDMA QUEUED
  60 08 78 08 e1 07 40 08   2d+15:47:50.480  READ FPDMA QUEUED
  60 08 70 10 e1 07 40 08   2d+15:47:50.480  READ FPDMA QUEUED
  60 08 68 78 c0 07 40 08   2d+15:47:50.479  READ FPDMA QUEUED
  60 08 60 70 c0 07 40 08   2d+15:47:50.479  READ FPDMA QUEUED

Error 10358 occurred at disk power-on lifetime: 8444 hours (351 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3a 00 c0 4b 6e  Error: UNC at LBA = 0x0e4bc000 = 239845376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 00 c0 4b 40 08   2d+15:10:18.906  READ FPDMA QUEUED
  60 08 30 08 e1 07 40 08   2d+15:10:18.898  READ FPDMA QUEUED
  60 08 28 10 e1 07 40 08   2d+15:10:18.898  READ FPDMA QUEUED
  60 08 20 78 c0 07 40 08   2d+15:10:18.895  READ FPDMA QUEUED
  60 08 18 70 c0 07 40 08   2d+15:10:18.895  READ FPDMA QUEUED

Error 10357 occurred at disk power-on lifetime: 8444 hours (351 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 32 f8 5f a4 6c  Error: UNC at LBA = 0x0ca45ff8 = 212099064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 30 f8 5f a4 40 08   2d+15:10:06.777  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00   2d+15:10:06.777  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00   2d+15:10:06.777  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00   2d+15:10:06.776  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   2d+15:10:06.776  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      8360         -

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

```

---

### Post by Bashing-om on 2015-05-17
benjitz; Hello;

I am that bearer of sad news:
> 
5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1710

1710 sectors have been 'reallocated' ;
AND
> 
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       529

there are still 529 sectors that the controller thinks are bad, but can not reallocate as there are no additional spare sectors to spare off too.
I think that drive is toast. May I suggest that you image that drive immediately, and re-claim your data from the clone.
That drive is not all that old, it is a slim possibility that you might be a be to zero out that drive and repurpose it as a 'data disk' . But I would never ever fully trust it . 

[INDENT][INDENT]it is a fact 
[INDENT][INDENT][INDENT]hard drives will fail
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by benjitz on 2015-05-17
It seems according to the DataRecovery link that the best method is to make an image of the partition on known error-free media asap, before working on it, which makes sense. Unfortunately I do not have this yet, having just ordered a 1TB hard drive today. What I guess need to know is whether the faulty partition has to be mounted in order to make the image? (As I can't do this.)

---

### Post by benjitz on 2015-05-17
Ah, thanks Bashing-om, didn't see your post - Yes I figured it probably was, and have stopped trying to save it as a working os drive and just trying to save what I can of my home directory if possible :/

---

### Post by Bashing-om on 2015-05-17
benjitz; Well;

> **benjitz said:**
> Ah, thanks Bashing-om, didn't see your post - Yes I figured it probably was, and have stopped trying to save it as a working os drive and just trying to save what I can of my home directory if possible :/

In the case of only saving files in /home; consider:

Boot up a liveDVD(USB) and activate the file manager;
open 2 windows and drag and drop the files from the install /home directory to a USB drive.


[INDENT][INDENT]the GUI
[INDENT][INDENT][INDENT]can be a wonderful thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by benjitz on 2015-05-17
Bashing-om - yes, but I can't mount the faulty partition, see my original post. But presumably I will be able to make an image of it onto a USB drive once I receive it without needing to mount it? (I have ordered one today, I do not have any other media big enough right now).

---

### Post by Bashing-om on 2015-05-17
benjitz; Ooooppps;



> **benjitz said:**
> Bashing-om - yes, but I can't mount the faulty partition, see my original post. But presumably I will be able to make an image of it onto a USB drive once I receive it without needing to mount it? (I have ordered one today, I do not have any other media big enough right now).
Quite right !  read and heed. My apologies for my failure .
As we are dealing with LVM in an encrypted environment and I have no experience in this realm; I can not offer any additional advisement.

A hard fall, head crashes into platter;
then all we have left is a total disaster

[INDENT][INDENT][INDENT][INDENT]maybe, throw lots of money at it .
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2015-05-17
The drive has problems and *testdisk* may be able to recover the partition enough to mount it.  You don't need to mount it to image it.  If the operating system detects it then just use the *dd* command.

```
sudo fdisk -l
```

Incidently, you can can quickly copy a drive using the *cp* command:

```
sudo cp /dev/sda /dev/sde
```

This assumes that your second drive is equal to or greater in size.

There are a lot of lessons learned here.  First, don't drop weights on your laptop.

---

### Post by benjitz on 2015-05-18
Bashing-om: no worries, thanks for your florid yet clear style of support!
tgalati: I've had variable success with testdisk so far, without actually trying to write to the disk/fix/alter anything. Yesterday I even got to access the partition's filesystem, and i was able to (very slowly) navigate the directory tree, though when I tried to copy a file to my mobile phone sd card (just to test whether I'd be able to use this method at all to get my data off) testdisk would say it was successful, but the file would not appear on the phone. Some filenames' text appears red and others white (against a black background), I'm not sure what this signifies. Neither coloured file would copy.
Today testdisk can't seem to access the partition again (though it lists it). I think it's best to stop fiddling and wait for my new hdd to arrive (eta: wednesday), and copy everything using the methods you suggest before proceeding any further. I have a feeling it will take a long time (maybe days) to copy everything over as it will keep failing to read in places. Incidentally I didn't drop anything onto the laptop, a loaded shelf fell down from the wall by it. I didn't see any of the contents hit the laptop (it's possible, but the entire contents was on the floor when I saw what had happened) but it hit the floor by the table the laptop was on so hard the vibration probably had an impact. I was initially fairly hopeful for the drive as I could originally occasionally still boot off it, and figured I just needed to mark all the damaged parts of it as unusable, because this was one-off damage, rather than old-age related where things start to gradually get worse and worse. But as I seem to get inconsistent results whilst trying the same methods to access it (as above) I feel it is far better to bite the bullet and replace it.

---

