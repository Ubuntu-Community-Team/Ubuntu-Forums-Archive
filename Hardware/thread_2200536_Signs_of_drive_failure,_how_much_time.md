---
title: "Signs of drive failure, how much time"
date: 2014-01-19
forum: Hardware
---

### Post by RideTheSpiral on 2014-01-19
I came here for the exact same reason so instead of posting another thread, perhaps someone could take a look at my smart output as well? I tried to do an extended test and it failed

```
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-15-lowlatency] (local build)Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD5000BEVT-24A0RT0
Serial Number:    WD-WXL1A80J0600
LU WWN Device Id: 5 0014ee 655c4bd62
Firmware Version: 01.01A02
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Jan 19 15:31:50 2014 MST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(12780) seconds.
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
recommended polling time: 	 ( 149) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7037)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   189   051    Pre-fail  Always       -       7655
  3 Spin_Up_Time            0x0027   186   181   021    Pre-fail  Always       -       1658
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4958
  5 Reallocated_Sector_Ct   0x0033   149   149   140    Pre-fail  Always       -       561
  7 Seek_Error_Rate         0x002e   198   193   000    Old_age   Always       -       61
  9 Power_On_Hours          0x0032   078   078   000    Old_age   Always       -       16539
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3853
192 Power-Off_Retract_Count 0x0032   198   198   000    Old_age   Always       -       2019
193 Load_Cycle_Count        0x0032   178   178   000    Old_age   Always       -       66583
194 Temperature_Celsius     0x0022   105   070   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   193   001   000    Old_age   Always       -       7
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       3


SMART Error Log Version: 1
Warning: ATA error count 38449 inconsistent with error log pointer 5


ATA Error Count: 38449 (device log contains only the most recent five errors)
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


Error 38449 occurred at disk power-on lifetime: 16524 hours (688 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 02 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 00      00:50:27.349  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.347  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:50:27.347  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 00      00:50:27.346  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.345  IDENTIFY DEVICE


Error 38448 occurred at disk power-on lifetime: 16524 hours (688 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00      00:50:27.347  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 00      00:50:27.346  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.345  IDENTIFY DEVICE
  c8 00 08 50 20 84 ed 00      00:50:27.344  READ DMA
  ef 10 02 00 00 00 a0 00      00:50:27.344  SET FEATURES [Enable SATA feature]


Error 38447 occurred at disk power-on lifetime: 16524 hours (688 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 02 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 00      00:50:27.346  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.345  IDENTIFY DEVICE
  c8 00 08 50 20 84 ed 00      00:50:27.344  READ DMA
  ef 10 02 00 00 00 a0 00      00:50:27.344  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.343  IDENTIFY DEVICE


Error 38446 occurred at disk power-on lifetime: 16524 hours (688 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 08 50 20 84 ed  Device Fault; Error: ABRT 8 sectors at LBA = 0x0d842050 = 226762832


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 50 20 84 ed 00      00:50:27.344  READ DMA
  ef 10 02 00 00 00 a0 00      00:50:27.344  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.343  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:50:27.342  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 00      00:50:27.342  SET FEATURES [Enable SATA feature]


Error 38445 occurred at disk power-on lifetime: 16524 hours (688 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 02 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 00      00:50:27.344  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.343  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:50:27.342  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 00      00:50:27.342  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 00      00:50:27.340  IDENTIFY DEVICE


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     16539         1235492
# 2  Extended offline    Completed: read failure       90%     16528         1235492
# 3  Conveyance offline  Completed without error       00%     16528         -
# 4  Short offline       Completed: read failure       60%     16525         976439398
# 5  Conveyance offline  Aborted by host               80%     16525         -
# 6  Extended offline    Completed: read failure       90%     16524         1235492
# 7  Extended offline    Aborted by host               10%      9560         -
# 8  Extended offline    Completed: read failure       90%      7703         1235492
# 9  Extended offline    Completed: read failure       90%      7703         1235492
#10  Conveyance offline  Completed without error       00%      7703         -


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

### Post by tgalati4 on 2014-01-19
@RideTheSpiral, hijacking a thread is considered bad form.  Reseat the cables on the drive or switch SATA ports.  It's possible that your drive's controller or the motherboard SATA controller has gone bad.

To the OP, your disk looks fine.  Run a long test:

```
sudo smartctl -t long /dev/sda
```

Wait the suggested amount of time (several minutes to an hour).

```
sudo smartctl -a /dev/sda
```

To see the results.

Most consumer disk drives are rated to 50,000 hours.  Server drives 100K.

---

### Post by QIII on 2014-01-19
Moved to its own thread.

There is no need to hijack another's thread.  There is plenty of room.

@ tgalati4 -- Did you mean for your response to also be for the OP?  If so, would you be so kind as to answer there again?

---

