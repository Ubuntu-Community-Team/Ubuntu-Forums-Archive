---
title: "How to fix read errors on hard drive"
date: 2009-02-17
forum: Hardware
---

### Post by rjoshi on 2009-02-17
I ran a GSmartControl tool on my laptop running Ubuntu  to find out hard drive related error.
"Short offline" test completed 100% but extended offline completed only 30% with first LBA errorat 16289067.

Is there any way to correct these issues?


Below is detail output from GSmartcontrol tool:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     IBM/Hitachi Travelstar 60GH and 40GN family
Device Model:     IC25N030ATCS04-0
Serial Number:    CSL305DAGR0NGA
Firmware Version: CA3OA71A
User Capacity:    30,005,821,440 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 3
Local Time is:    Tue Feb 17 20:07:51 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 119)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 ( 645) seconds.
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
recommended polling time: 	 (  37) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   097   097   062    Pre-fail  Always       -       393216
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   135   135   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   097   097   000    Old_age   Always       -       5659
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   057   057   000    Old_age   Always       -       19223
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       4844
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       573
193 Load_Cycle_Count        0x0012   037   037   000    Old_age   Always       -       634751
194 Temperature_Celsius     0x0002   127   127   000    Old_age   Always       -       43 (Lifetime Min/Max 10/63)
196 Reallocated_Event_Count 0x0032   096   096   000    Old_age   Always       -       288
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       35
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       1

SMART Error Log Version: 1
ATA Error Count: 1963 (device log contains only the most recent five errors)
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

Error 1963 occurred at disk power-on lifetime: 17193 hours (716 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 2d 2b 8d f8 e0  Error: UNC 45 sectors at LBA = 0x00f88d2b = 16289067

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 30 28 8d f8 e0 00      00:28:35.700  READ DMA
  c8 00 38 20 8d f8 e0 00      00:28:31.300  READ DMA
  c8 00 40 18 8d f8 e0 00      00:28:26.900  READ DMA
  c8 00 40 d8 8c f8 e0 00      00:28:26.900  READ DMA
  c8 00 18 c0 8c f8 e0 00      00:28:26.900  READ DMA

Error 1962 occurred at disk power-on lifetime: 17193 hours (716 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 2d 2b 8d f8 e0  Error: UNC 45 sectors at LBA = 0x00f88d2b = 16289067

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 38 20 8d f8 e0 00      00:28:31.300  READ DMA
  c8 00 40 18 8d f8 e0 00      00:28:26.900  READ DMA
  c8 00 40 d8 8c f8 e0 00      00:28:26.900  READ DMA
  c8 00 18 c0 8c f8 e0 00      00:28:26.900  READ DMA
  c8 00 18 50 8a f8 e0 00      00:28:26.900  READ DMA

Error 1961 occurred at disk power-on lifetime: 17193 hours (716 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 2d 2b 8d f8 e0  Error: UNC 45 sectors at LBA = 0x00f88d2b = 16289067

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 18 8d f8 e0 00      00:28:26.900  READ DMA
  c8 00 40 d8 8c f8 e0 00      00:28:26.900  READ DMA
  c8 00 18 c0 8c f8 e0 00      00:28:26.900  READ DMA
  c8 00 18 50 8a f8 e0 00      00:28:26.900  READ DMA
  c8 00 10 c0 89 f8 e0 00      00:28:26.900  READ DMA

Error 1960 occurred at disk power-on lifetime: 16097 hours (670 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 37 d2 b5 e1  Error: UNC 8 sectors at LBA = 0x01b5d237 = 28693047

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 18 27 d2 b5 e1 00      00:19:11.500  READ DMA
  f8 00 00 00 00 00 e0 00      00:19:11.500  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:19:11.500  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:19:11.500  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:19:11.500  READ NATIVE MAX ADDRESS

Error 1959 occurred at disk power-on lifetime: 16097 hours (670 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 37 d2 b5 e1  Error: UNC 8 sectors at LBA = 0x01b5d237 = 28693047

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 18 27 d2 b5 e1 00      00:19:07.000  READ DMA
  f8 00 00 00 00 00 e0 00      00:19:07.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:19:07.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:19:07.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:19:07.000  READ NATIVE MAX ADDRESS

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       70%     19223         16289067
# 2  Extended offline    Completed: read failure       70%     19223         16289068
# 3  Short offline       Completed without error       00%     19223         -

Device does not support Selective Self Tests/Logging

---

