---
title: "what's going on with my hdd?"
date: 2008-09-01
forum: Hardware
---

### Post by DouglasAWh on 2008-09-01
Can someone interpret the following for me?

```

whitdoug@mainDesktop:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3160023A
Serial Number:    3LJ2SJSZ
Firmware Version: 8.01
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Mon Sep  1 19:38:09 2008 CDT
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
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   060   055   006    Pre-fail  Always       -       64219276
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       5
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       4949689596
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       26133
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       503
194 Temperature_Celsius     0x0022   044   050   000    Old_age   Always       -       44
195 Hardware_ECC_Recovered  0x001a   060   055   000    Old_age   Always       -       64219276
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   196   000    Old_age   Always       -       19
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 23 (device log contains only the most recent five errors)
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

Error 23 occurred at disk power-on lifetime: 25923 hours (1080 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 36 01 3e e0  Error: ICRC, ABRT 1 sectors at LBA = 0x003e0136 = 4063542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 68 cf 00 3e e0 00      00:00:45.080  READ DMA
  c8 00 40 ff 8f 3d e0 00      00:00:45.080  READ DMA
  c8 00 60 df 87 3d e0 00      00:00:45.076  READ DMA
  c8 00 38 4f 40 3d e0 00      00:00:45.075  READ DMA
  c8 00 08 37 f4 3c e0 00      00:00:45.075  READ DMA

Error 22 occurred at disk power-on lifetime: 25837 hours (1076 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 d6 e6 b5 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00b5e6d6 = 11921110

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 cf e6 b5 e0 00      13:50:09.808  READ DMA
  ca 00 08 5f 39 01 e0 00      13:36:58.898  WRITE DMA
  ca 00 08 ff 00 d4 e0 00      13:36:53.806  WRITE DMA
  ca 00 08 5f 00 d4 e0 00      13:36:53.806  WRITE DMA
  ca 00 08 57 39 01 e0 00      14:04:24.764  WRITE DMA

Error 21 occurred at disk power-on lifetime: 25824 hours (1076 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 e6 a7 76 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0076a7e6 = 7776230

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 10 d7 a7 76 e0 00      01:23:32.470  READ DMA
  ca 00 08 9f 8a 00 e0 00      01:24:06.540  WRITE DMA
  ca 00 60 3f 8a 00 e0 00      01:24:03.498  WRITE DMA
  ca 00 08 37 8a 00 e0 00      01:24:03.497  WRITE DMA
  ca 00 60 d7 89 00 e0 00      01:23:58.309  WRITE DMA

Error 20 occurred at disk power-on lifetime: 25824 hours (1076 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 d6 25 4b e0  Error: ICRC, ABRT 1 sectors at LBA = 0x004b25d6 = 4924886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 cf 25 4b e0 00      01:14:35.486  READ DMA EXT
  25 00 08 27 d0 4b e0 00      01:14:35.486  READ DMA EXT
  25 00 08 bf 2b 4b e0 00      01:14:35.480  READ DMA EXT
  25 00 08 8f 2d 4b e0 00      01:14:35.479  READ DMA EXT
  25 00 08 bf c8 4b e0 00      01:14:35.469  READ DMA EXT

Error 19 occurred at disk power-on lifetime: 25824 hours (1076 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 c6 c2 4b e0  Error: ICRC, ABRT 1 sectors at LBA = 0x004bc2c6 = 4965062

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 af c2 4b e0 00      01:14:31.613  READ DMA EXT
  25 00 08 a7 c2 4b e0 00      01:14:31.593  READ DMA EXT
  25 00 08 9f ac 4b e0 00      01:14:31.585  READ DMA EXT
  c8 00 20 ff 60 d5 e1 00      01:14:31.584  READ DMA
  c8 00 08 f7 60 d5 e1 00      01:14:31.583  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     26132         -

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

I tried running a test with 

```

sudo smartctl --test=long /dev/sdb

```

and it spat out

```

Testing has begun.
Please wait 111 minutes for test to complete.
Test will complete after Mon Sep 1 19:22:36 2008

Use smartctl -X to abort test.

```

however, I got no returns when using 

```

ps -A|grep smart

```

I think that command should have returned smartd.  So, did the test run or not?  Is there any way to know?

---

### Post by cariboo on 2008-09-01
Are you having problems with your hard drive,go here:

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

Download Seatools for dos cdrom iso

Jim

---

