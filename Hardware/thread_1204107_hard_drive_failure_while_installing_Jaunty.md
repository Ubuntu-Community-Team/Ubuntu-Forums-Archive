---
title: "hard drive failure while installing Jaunty"
date: 2009-07-04
forum: Hardware
---

### Post by carverj on 2009-07-04
So managed to boot Jaunty live and run smartmontools:
```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD502HI
Serial Number:    S1VZJ9AS300208
Firmware Version: 1AG01113
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Sat Jul  4 10:22:11 2009 UTC

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection: 		 (6326) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 106) minutes.
Conveyance self-test routine
recommended polling time: 	 (  12) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   097   097   051    Pre-fail  Always       -       10520
  3 Spin_Up_Time            0x0007   093   093   011    Pre-fail  Always       -       3020
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       174
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       572
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       173
 13 Read_Soft_Error_Rate    0x000e   097   097   000    Old_age   Always       -       10369
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       10369
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   073   060   000    Old_age   Always       -       27 (Lifetime Min/Max 27/28)
194 Temperature_Celsius     0x0022   074   059   000    Old_age   Always       -       26 (Lifetime Min/Max 26/28)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       218
196 Reallocated_Event_Count 0x0032   099   099   000    Old_age   Always       -       46
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       44
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       736

SMART Error Log Version: 1
ATA Error Count: 312 (device log contains only the most recent five errors)
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

Error 312 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:20:17.040  READ DMA
  ef 03 46 01 4f c2 a0 00      00:20:17.040  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:20:17.040  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:20:17.040  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:20:17.040  SMART RETURN STATUS

Error 311 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:00:05.700  READ DMA
  ef 03 46 01 4f c2 a0 00      00:00:05.700  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:00:05.700  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:00:05.700  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:00:05.700  SMART RETURN STATUS

Error 310 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:04:27.870  READ DMA
  ef 03 46 01 4f c2 a0 00      00:04:27.870  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:04:27.870  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:04:27.870  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:04:27.870  SMART RETURN STATUS

Error 309 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:00:05.620  READ DMA
  ef 03 46 01 4f c2 a0 00      00:00:05.620  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:00:05.620  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:00:05.620  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:00:05.620  SMART RETURN STATUS

Error 308 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:01:01.450  READ DMA
  ef 03 46 01 4f c2 a0 00      00:01:01.450  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:01:01.450  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:01:01.450  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:01:01.450  SMART RETURN STATUS

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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
Does this mean a faulty disk? I cannot decipher it!
Thanks.

---

### Post by carverj on 2009-07-04
I have received an answer:
[http://ubuntuforums.org/showthread.php?t=1203198](http://ubuntuforums.org/showthread.php?t=1203198)

---

