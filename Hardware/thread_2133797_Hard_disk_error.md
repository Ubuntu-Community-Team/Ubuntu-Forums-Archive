---
title: "Hard disk error"
date: 2013-04-09
forum: Hardware
---

### Post by dread22 on 2013-04-09
Hi,

I have 5 disks on my system, one old 320GB PATA drive with Ubuntu installed and 4x 2TB disks set up as RAID+LVM. Something is dieing and I'm not sure which it is.

I'm getting these errors in dmesg
```

[99780.832028] ata4: lost interrupt (Status 0x50)
[99780.832048] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[99780.832055] ata4.00: failed command: READ DMA EXT
[99780.832063] ata4.00: cmd 25/00:00:00:32:11/00:02:de:00:00/e0 tag 0 dma 262144 in
[99780.832065]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[99780.832070] ata4.00: status: { DRDY }
[99780.832080] ata4: soft resetting link
[99781.316516] ata4.00: configured for UDMA/33
[99782.037385] ata4.01: configured for UDMA/133
[99782.037392] ata4.00: device reported invalid CHS sector 0
[99782.037398] ata4: EH complete
[99829.856027] ata4: lost interrupt (Status 0x50)
[99829.856043] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[99829.856048] ata4.00: failed command: READ DMA EXT
[99829.856053] ata4.00: cmd 25/00:e8:18:b8:65/00:01:e0:00:00/e0 tag 0 dma 249856 in
[99829.856054]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[99829.856056] ata4.00: status: { DRDY }
[99829.856064] ata4: soft resetting link
[99830.708327] ata4.00: configured for UDMA/33
[99831.101370] ata4.01: configured for UDMA/133
[99831.101376] ata4.00: device reported invalid CHS sector 0
[99831.101384] ata4: EH complete
[101326.816045] ata4: lost interrupt (Status 0x50)
[101326.816065] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[101326.816072] ata4.00: failed command: READ DMA EXT
[101326.816080] ata4.00: cmd 25/00:00:00:70:68/00:02:6c:00:00/e0 tag 0 dma 262144 in
[101326.816083]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[101326.816087] ata4.00: status: { DRDY }
[101326.816105] ata4: soft resetting link
[101327.664308] ata4.00: configured for UDMA/33
[101328.056891] ata4.01: configured for UDMA/133
[101328.056898] ata4.00: device reported invalid CHS sector 0
[101328.056905] ata4: EH complete

```

I've posted my SMART logs below for all 5 disks.
Results of 'smartctl -a /dev/sd*' (in order)

```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue EIDE
Device Model:     WDC WD3200AAJB-00TYA0
Serial Number:    WD-WCAPZ3095612
LU WWN Device Id: 5 0014ee 155aebf4f
Firmware Version: 00.02C01
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr  9 20:55:20 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 8760) seconds.
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
recommended polling time: 	 ( 111) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.
SCT capabilities: 	       (0x203f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   193   150   021    Pre-fail  Always       -       3333
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       942
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   047   047   000    Old_age   Always       -       39086
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       916
192 Power-Off_Retract_Count 0x0032   198   198   000    Old_age   Always       -       1543
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2167
194 Temperature_Celsius     0x0022   111   091   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   195   000    Old_age   Always       -       346
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 6 (device log contains only the most recent five errors)
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

Error 6 occurred at disk power-on lifetime: 33 hours (1 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 37 d0 ee d6 e1  Error: UNC 55 sectors at LBA = 0x01d6eed0 = 30863056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 a7 ee d6 01 08      07:31:49.057  READ DMA
  27 00 00 00 00 00 00 08      07:31:49.041  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 0a      07:31:49.033  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 0a      07:31:49.033  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      07:31:49.033  READ NATIVE MAX ADDRESS EXT

Error 5 occurred at disk power-on lifetime: 33 hours (1 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 37 d0 ee d6 e1  Error: UNC 55 sectors at LBA = 0x01d6eed0 = 30863056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 a7 ee d6 01 08      07:31:47.099  READ DMA
  27 00 00 00 00 00 00 08      07:31:47.083  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 0a      07:31:47.075  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 0a      07:31:47.075  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      07:31:47.075  READ NATIVE MAX ADDRESS EXT

Error 4 occurred at disk power-on lifetime: 33 hours (1 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 37 d0 ee d6 e1  Error: UNC 55 sectors at LBA = 0x01d6eed0 = 30863056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 a7 ee d6 01 08      07:31:45.145  READ DMA
  27 00 00 00 00 00 00 08      07:31:45.130  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 0a      07:31:45.122  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 0a      07:31:45.122  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      07:31:45.122  READ NATIVE MAX ADDRESS EXT

Error 3 occurred at disk power-on lifetime: 33 hours (1 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 37 d0 ee d6 e1  Error: UNC 55 sectors at LBA = 0x01d6eed0 = 30863056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 a7 ee d6 01 08      07:31:43.203  READ DMA
  27 00 00 00 00 00 00 08      07:31:43.188  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 0a      07:31:43.180  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 0a      07:31:43.180  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      07:31:43.180  READ NATIVE MAX ADDRESS EXT

Error 2 occurred at disk power-on lifetime: 33 hours (1 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 37 d0 ee d6 e1  Error: UNC 55 sectors at LBA = 0x01d6eed0 = 30863056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 a7 ee d6 01 08      07:31:41.257  READ DMA
  27 00 00 00 00 00 00 08      07:31:41.242  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 0a      07:31:41.234  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 0a      07:31:41.234  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      07:31:41.234  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     38828         -
# 2  Extended offline    Completed without error       00%     37285         -
# 3  Extended offline    Completed without error       00%     34211         -
# 4  Conveyance offline  Completed without error       00%     34163         -
# 5  Short offline       Completed without error       00%     34139         -
# 6  Extended offline    Completed without error       00%     34044         -
# 7  Conveyance offline  Completed without error       00%     33995         -
# 8  Short offline       Completed without error       00%     33971         -
# 9  Extended offline    Completed without error       00%     33877         -
#10  Conveyance offline  Completed without error       00%     33827         -
#11  Short offline       Completed without error       00%     33803         -
#12  Extended offline    Completed without error       00%     33709         -
#13  Conveyance offline  Completed without error       00%     33660         -
#14  Short offline       Completed without error       00%     33636         -
#15  Extended offline    Completed without error       00%     33541         -
#16  Conveyance offline  Completed without error       00%     33492         -
#17  Short offline       Completed without error       00%     33468         -
#18  Extended offline    Completed without error       00%     33374         -
#19  Conveyance offline  Completed without error       00%     33324         -
#20  Short offline       Completed without error       00%     33300         -
#21  Extended offline    Completed without error       00%     33206         -

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

```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST2000DM001-9YN164
Serial Number:    S2409FT6
LU WWN Device Id: 5 000c50 04aae5da8
Firmware Version: CC4C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Apr  9 20:55:24 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  600) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 251) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3085)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       77398024
  3 Spin_Up_Time            0x0003   096   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       49
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       58382398
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7810
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       49
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   044   045    Old_age   Always   In_the_past 39 (0 18 40 22)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       30
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       63
194 Temperature_Celsius     0x0022   039   056   000    Old_age   Always       -       39 (0 19 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       100506529701501
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       18783409625
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       780412835426

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7555         -
# 2  Extended offline    Completed without error       00%      6010         -
# 3  Extended offline    Completed without error       00%      2933         -
# 4  Conveyance offline  Completed without error       00%      2882         -
# 5  Short offline       Completed without error       00%      2858         -
# 6  Extended offline    Completed without error       00%      2766         -
# 7  Conveyance offline  Completed without error       00%      2714         -
# 8  Short offline       Completed without error       00%      2690         -
# 9  Extended offline    Completed without error       00%      2598         -
#10  Conveyance offline  Completed without error       00%      2546         -
#11  Short offline       Completed without error       00%      2522         -
#12  Extended offline    Completed without error       00%      2430         -
#13  Conveyance offline  Completed without error       00%      2378         -
#14  Short offline       Completed without error       00%      2354         -
#15  Extended offline    Completed without error       00%      2262         -
#16  Conveyance offline  Completed without error       00%      2210         -
#17  Short offline       Completed without error       00%      2186         -
#18  Extended offline    Completed without error       00%      2094         -
#19  Conveyance offline  Completed without error       00%      2042         -
#20  Short offline       Completed without error       00%      2018         -
#21  Extended offline    Completed without error       00%      1926         -

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


```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WCAZA9080050
LU WWN Device Id: 5 0014ee 25b860048
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr  9 20:55:27 2013 EST
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
data collection: 		(38100) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   213   164   021    Pre-fail  Always       -       4316
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       78
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       13093
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       76
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       113
193 Load_Cycle_Count        0x0032   122   122   000    Old_age   Always       -       234737
194 Temperature_Celsius     0x0022   114   089   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     12841         -
# 2  Extended offline    Completed without error       00%     11299         -
# 3  Extended offline    Completed without error       00%      8226         -
# 4  Conveyance offline  Completed without error       00%      8173         -
# 5  Short offline       Completed without error       00%      8149         -
# 6  Extended offline    Completed without error       00%      8059         -
# 7  Conveyance offline  Completed without error       00%      8005         -
# 8  Short offline       Completed without error       00%      7981         -
# 9  Extended offline    Completed without error       00%      7892         -
#10  Conveyance offline  Completed without error       00%      7837         -
#11  Short offline       Completed without error       00%      7813         -
#12  Extended offline    Completed without error       00%      7724         -
#13  Conveyance offline  Completed without error       00%      7670         -
#14  Short offline       Completed without error       00%      7646         -
#15  Extended offline    Completed without error       00%      7556         -
#16  Conveyance offline  Completed without error       00%      7502         -
#17  Short offline       Completed without error       00%      7478         -
#18  Extended offline    Completed without error       00%      7389         -
#19  Conveyance offline  Completed without error       00%      7334         -
#20  Short offline       Completed without error       00%      7310         -
#21  Extended offline    Completed without error       00%      7220         -

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


```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST2000DM001-9YN164
Serial Number:    S2409CQY
LU WWN Device Id: 5 000c50 04aaf9d18
Firmware Version: CC4C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Apr  9 20:55:31 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  41)	The self-test routine was interrupted
					by the host with a hard or soft reset.
Total time to complete Offline 
data collection: 		(  617) seconds.
Offline data collection
capabilities: 			 (0x73) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 248) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3085)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       182139544
  3 Spin_Up_Time            0x0003   098   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1307
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       4343434933
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       7959
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       53
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   095   095   000    Old_age   Always       -       5
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   044   045    Old_age   Always   In_the_past 41 (0 8 41 41)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1286
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       5027
194 Temperature_Celsius     0x0022   041   056   000    Old_age   Always       -       41 (0 19 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       56
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       56
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       267181325557219
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4517793325247
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       13780152140761

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      00%      7959         -
# 2  Extended offline    Interrupted (host reset)      00%      7959         -
# 3  Short offline       Completed without error       00%      7959         -
# 4  Extended offline    Interrupted (host reset)      00%      7720         -
# 5  Extended offline    Interrupted (host reset)      00%      7702         -
# 6  Extended offline    Interrupted (host reset)      00%      7699         -
# 7  Extended offline    Interrupted (host reset)      00%      6155         -
# 8  Extended offline    Completed without error       00%      3083         -
# 9  Conveyance offline  Completed without error       00%      3031         -
#10  Short offline       Completed without error       00%      3007         -
#11  Extended offline    Completed without error       00%      2916         -
#12  Conveyance offline  Completed without error       00%      2863         -
#13  Short offline       Completed without error       00%      2839         -
#14  Extended offline    Completed without error       00%      2747         -
#15  Conveyance offline  Completed without error       00%      2695         -
#16  Short offline       Completed without error       00%      2671         -
#17  Extended offline    Completed without error       00%      2579         -
#18  Conveyance offline  Completed without error       00%      2527         -
#19  Short offline       Completed without error       00%      2503         -
#20  Extended offline    Completed without error       00%      2412         -
#21  Conveyance offline  Completed without error       00%      2359         -

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

```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WCAZA9327281
LU WWN Device Id: 5 0014ee 2b0dca839
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr  9 20:55:34 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(38160) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   214   166   021    Pre-fail  Always       -       4266
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       82
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       13093
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       80
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       120
193 Load_Cycle_Count        0x0032   121   121   000    Old_age   Always       -       237514
194 Temperature_Celsius     0x0022   116   091   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       6

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     13093         2955376944
# 2  Short offline       Completed: read failure       90%     12836         2955376961
# 3  Extended offline    Completed: read failure       90%     12833         2955376960
# 4  Extended offline    Completed: read failure       90%     11292         2955376952
# 5  Extended offline    Completed without error       00%      8226         -
# 6  Conveyance offline  Completed without error       00%      8172         -
# 7  Short offline       Completed without error       00%      8148         -
# 8  Extended offline    Completed: read failure       90%      8052         2955376964
# 9  Conveyance offline  Completed without error       00%      8004         -
#10  Short offline       Completed without error       00%      7980         -
#11  Extended offline    Completed: read failure       20%      7889         2955376960
#12  Conveyance offline  Completed: read failure       90%      7837         3117281336
#13  Short offline       Completed without error       00%      7813         -
#14  Extended offline    Completed without error       00%      7723         -
#15  Conveyance offline  Completed without error       00%      7669         -
#16  Short offline       Completed without error       00%      7645         -
#17  Extended offline    Completed: read failure       20%      7554         3117281336
#18  Conveyance offline  Completed without error       00%      7501         -
#19  Short offline       Completed without error       00%      7477         -
#20  Extended offline    Completed without error       00%      7388         -
#21  Conveyance offline  Completed without error       00%      7334         -
4 of 8 failed self-tests are outdated by newer successful extended offline self-test # 5

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

Help appriciated in finding the problem as I'm not sure what I'm looking at (or if multiple disks are failing). RAID seems to be holding up though.

---

### Post by ahallubuntu on 2013-04-09
~

---

### Post by dread22 on 2013-04-10
Cheers. Failed & removed sdd from the RAID and haven't been getting any errors since and have had a significant speed up over my LAN. I'll be replacing those two disks as soon as I get the chance.

---

