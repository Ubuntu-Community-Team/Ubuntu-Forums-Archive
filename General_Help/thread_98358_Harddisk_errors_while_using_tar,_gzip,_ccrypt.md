---
title: "Harddisk errors while using tar, gzip, ccrypt"
date: 2005-12-03
forum: General Help
---

### Post by snowmotion on 2005-12-03
I have a lot of email in Maildir folders.  I've been trying to tar them all up, gzip them, and then encrypt them for storage on a DVD disk.

The problem I kept running into is that I had so many individual files (> 45,000) that something started choking.

I got input/output errors.  Sometimes during the tar step.  Most of the time during the ccrypt step.  "DriveReady SeekComplete Error" errors started showing up in my /var/log/messages.

I then looked throught Ubuntu forums and tried this command to further isolate what might be happening:

> smartctl -a /dev/hda5

The results:

```

smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK6026GAX
Serial Number:    55K60640T
Firmware Version: PA202D
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Dec  3 03:42:40 2005 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 239) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  47) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1397
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       313
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       4
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       388
 10 Spin_Retry_Count        0x0033   106   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       2
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       10596
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       47 (Lifetime Min/Max 23/61)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       130
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       294
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       227
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 113 (device log contains only the most recent five errors)
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

Error 113 occurred at disk power-on lifetime: 373 hours (15 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 63 f2 da f4 e3  Error: UNC 99 sectors at LBA = 0x03f4daf2 = 66378482

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 68 ed da f4 e3 00      03:55:34.377  READ DMA
  c8 00 70 e5 da f4 e3 00      03:55:27.744  READ DMA
  c8 00 78 dd da f4 e3 00      03:55:21.111  READ DMA
  c8 00 80 d5 da f4 e3 00      03:55:14.477  READ DMA
  c8 00 88 cd da f4 e3 00      03:55:07.844  READ DMA

Error 112 occurred at disk power-on lifetime: 373 hours (15 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 63 f2 da f4 e3  Error: UNC 99 sectors at LBA = 0x03f4daf2 = 66378482

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 70 e5 da f4 e3 00      03:55:27.744  READ DMA
  c8 00 78 dd da f4 e3 00      03:55:21.111  READ DMA
  c8 00 80 d5 da f4 e3 00      03:55:14.477  READ DMA
  c8 00 88 cd da f4 e3 00      03:55:07.844  READ DMA
  c8 00 90 c5 da f4 e3 00      03:55:01.221  READ DMA

Error 111 occurred at disk power-on lifetime: 373 hours (15 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 63 f2 da f4 e3  Error: UNC 99 sectors at LBA = 0x03f4daf2 = 66378482

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 78 dd da f4 e3 00      03:55:21.111  READ DMA
  c8 00 80 d5 da f4 e3 00      03:55:14.477  READ DMA
  c8 00 88 cd da f4 e3 00      03:55:07.844  READ DMA
  c8 00 90 c5 da f4 e3 00      03:55:01.221  READ DMA
  c8 00 98 bd da f4 e3 00      03:54:54.588  READ DMA

Error 110 occurred at disk power-on lifetime: 373 hours (15 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 63 f2 da f4 e3  Error: UNC 99 sectors at LBA = 0x03f4daf2 = 66378482

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 d5 da f4 e3 00      03:55:14.477  READ DMA
  c8 00 88 cd da f4 e3 00      03:55:07.844  READ DMA
  c8 00 90 c5 da f4 e3 00      03:55:01.221  READ DMA
  c8 00 98 bd da f4 e3 00      03:54:54.588  READ DMA
  c8 00 a0 b5 da f4 e3 00      03:54:47.954  READ DMA

Error 109 occurred at disk power-on lifetime: 373 hours (15 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 63 f2 da f4 e3  Error: UNC 99 sectors at LBA = 0x03f4daf2 = 66378482

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 88 cd da f4 e3 00      03:55:07.844  READ DMA
  c8 00 90 c5 da f4 e3 00      03:55:01.221  READ DMA
  c8 00 98 bd da f4 e3 00      03:54:54.588  READ DMA
  c8 00 a0 b5 da f4 e3 00      03:54:47.954  READ DMA
  c8 00 a8 ad da f4 e3 00      03:54:41.321  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       376         -
# 2  Short offline       Completed without error       00%         0         -

Device does not support Selective Self Tests/Logging

```

My questions:

1) Is there a limit to how many files I can tar up, gzip, and then ccrypt?

2) Given the results of the smartctl test, is there anything I can do about the errors that showed up?

Thanks so much!

Snowmotion

---

