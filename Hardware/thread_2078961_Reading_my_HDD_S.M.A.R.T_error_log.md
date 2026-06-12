---
title: "Reading my HDD S.M.A.R.T error log"
date: 2012-11-01
forum: Hardware
---

### Post by sadeghi on 2012-11-01
Hello

My hard disk has became very slow. Sometimes when I'm open so many tabs in FF or Chrome it starts to read/write until I should manually force restart the laptop. I'm not sure if it's something with my OS configuration or HDD but because my laptop is rather old I made a S.M.A.R.T test on it but I can not understand the error log. I appreciate if anybody can tell me if this log is OK and my disk is healthy or not.

Output for the command "sudo smartctl -a /dev/sda":

```
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-17-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD (80 GB and above)
Device Model:     TOSHIBA MK1234GSX
Serial Number:    Y6FNT6XGT
Firmware Version: AH001D
User Capacity:    120.034.123.776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Nov  1 06:21:45 2012 CET
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
data collection: 		(  435) seconds.
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
recommended polling time: 	 (  86) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   100   100   000    Old_age   Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1747
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       7029
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   059   059   000    Old_age   Always       -       16733
 10 Spin_Retry_Count        0x0032   239   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5715
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       469
193 Load_Cycle_Count        0x0032   087   087   000    Old_age   Always       -       137322
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       45 (Min/Max 11/55)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       225
222 Loaded_Hours            0x0032   063   063   000    Old_age   Always       -       14996
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       386
240 Head_Flying_Hours       0x0000   100   100   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 199 (device log contains only the most recent five errors)
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

Error 199 occurred at disk power-on lifetime: 16601 hours (691 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 e8 9b 8b e0  Error: ICRC, ABRT 1 sectors at LBA = 0x008b9be8 = 9149416

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 70 08 01 e2 00      03:51:37.137  READ DMA
  c8 00 48 b8 e0 4c e1 00      03:51:37.119  READ DMA
  c8 00 d8 90 d1 52 e0 00      03:51:37.109  READ DMA
  c8 00 00 30 f8 3d e0 00      03:51:37.099  READ DMA
  c8 00 10 d0 15 31 e0 00      03:51:37.099  READ DMA

Error 198 occurred at disk power-on lifetime: 16577 hours (690 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 48 9b 4b e1  Error: ICRC, ABRT 1 sectors at LBA = 0x014b9b48 = 21732168

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 04 07 e0 00      02:39:20.096  READ DMA
  c8 00 08 a8 04 07 e0 00      02:39:20.095  READ DMA
  c8 00 58 48 04 07 e0 00      02:39:20.077  READ DMA
  c8 00 10 90 24 90 e2 00      02:39:20.076  READ DMA
  c8 00 10 70 24 90 e2 00      02:39:20.076  READ DMA

Error 197 occurred at disk power-on lifetime: 16565 hours (690 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 d2 34 0b e2  Error: ICRC, ABRT 1 sectors at LBA = 0x020b34d2 = 34288850

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 70 90 32 0b e2 00      02:58:53.636  READ DMA
  c8 00 30 58 32 0b e2 00      02:58:53.636  READ DMA
  c8 00 50 00 32 0b e2 00      02:58:53.632  READ DMA
  c8 00 50 20 fd 0a e2 00      02:58:53.630  READ DMA
  c8 00 88 70 fc 0a e2 00      02:58:53.614  READ DMA

Error 196 occurred at disk power-on lifetime: 16509 hours (687 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 38 bf ec ed  Error: ICRC, ABRT 1 sectors at LBA = 0x0decbf38 = 233619256

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c0 e3 06 e0 00      00:13:40.741  READ DMA
  c8 00 18 d8 89 e2 ed 00      00:13:40.720  READ DMA
  c8 00 40 4a 38 2a e5 00      00:13:40.706  READ DMA
  c8 00 28 f8 70 96 e4 00      00:13:40.704  READ DMA
  c8 00 08 98 70 96 e4 00      00:13:40.688  READ DMA

Error 195 occurred at disk power-on lifetime: 16442 hours (685 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 92 cb 7a e0  Error: ICRC, ABRT 1 sectors at LBA = 0x007acb92 = 8047506

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 90 c9 7a e0 00      05:07:50.417  READ DMA
  c8 00 18 70 c6 7a e0 00      05:07:50.416  READ DMA
  c8 00 08 90 c6 7a e0 00      05:07:50.416  READ DMA
  c8 00 10 a8 c6 7a e0 00      05:07:50.416  READ DMA
  c8 00 60 d0 c6 7a e0 00      05:07:50.410  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     16733         -
# 2  Short offline       Completed without error       00%     15138         -
# 3  Short offline       Completed without error       00%     14567         -
# 4  Short offline       Completed without error       00%     10974         -
# 5  Short offline       Interrupted (host reset)      60%      8890         -
# 6  Short offline       Interrupted (host reset)      40%      5820         -
# 7  Short offline       Completed without error       00%      1439         -
# 8  Short offline       Completed without error       00%         1         -
# 9  Short offline       Completed without error       00%         0         -

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

Thanks

---

### Post by ibjsb4 on 2012-11-01
Maybe its not your HDD, maybe you are using swap.  Check your "system monitor" or in terminal enter:

top

---

### Post by sadeghi on 2012-11-01
> **ibjsb4 said:**
> Maybe its not your HDD, maybe you are using swap.  Check your "system monitor" or in terminal enter:

top

I have no swap partition on my drive. And the problem is when my drive starts to heavily read/write It's so busy that I can not run any command. I need to undrestand the smart log to confirm the health of my drive.

---

