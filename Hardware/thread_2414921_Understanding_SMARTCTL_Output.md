---
title: "Understanding SMARTCTL Output"
date: 2019-03-17
forum: Hardware
---

### Post by kowalski215 on 2019-03-17
Hi everyone,
Hope to be posting in the right section of this forum. Yesterday, Windows failed to boot up on my laptop. It displayed an error which I had already seen on a different PC - and found out that time it was disk-related.
This time, I wanted to find out something more with Ubuntu (after a long time not using it) - mint in this case, but doesn't really matter.
I tested the disk with smartctl and I wanted to ask you some information about the output. I'm not really able to go through the whole output and errors.
Do you think the hard drive needs replacement? Is there some error I should worry about? Thank you in advance for your help

```
mint@mint:~/Desktop$ sudo smartctl -a /dev/sdasmartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model:     TOSHIBA MQ01ABD075
Serial Number:    24ITP757T
LU WWN Device Id: 5 000039 552f84ec7
Firmware Version: AX0R2J
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Mar 17 14:01:01 2019 UTC
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
recommended polling time: 	 ( 191) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1714
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       24209
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   069   069   000    Old_age   Always       -       12752
 10 Spin_Retry_Count        0x0033   253   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       6810
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       3184
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       204
193 Load_Cycle_Count        0x0032   080   080   000    Old_age   Always       -       203260
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       25 (Min/Max 11/44)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       416
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   072   072   000    Old_age   Always       -       11331
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       276
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0


SMART Error Log Version: 1
ATA Error Count: 30657 (device log contains only the most recent five errors)
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


Error 30657 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 08 09 76 40  Error: UNC at LBA = 0x00760908 = 7735560


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 05 08 08 09 76 40 00      00:03:57.992  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:57.991  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:54.192  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:54.191  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:50.358  READ FPDMA QUEUED


Error 30656 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 08 09 76 40  Error: UNC at LBA = 0x00760908 = 7735560


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 05 08 08 09 76 40 00      00:03:54.192  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:54.191  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:50.358  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:50.357  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:46.558  READ FPDMA QUEUED


Error 30655 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 08 09 76 40  Error: UNC at LBA = 0x00760908 = 7735560


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 05 08 08 09 76 40 00      00:03:50.358  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:50.357  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:46.558  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:46.557  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:42.757  READ FPDMA QUEUED


Error 30654 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 08 09 76 40  Error: UNC at LBA = 0x00760908 = 7735560


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 05 08 08 09 76 40 00      00:03:46.558  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:46.557  READ LOG EXT
  60 05 08 08 09 76 40 00      00:03:42.757  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:42.756  READ LOG EXT
  60 05 38 08 09 76 40 00      00:03:38.943  READ FPDMA QUEUED


Error 30653 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 08 09 76 40  Error: UNC at LBA = 0x00760908 = 7735560


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 05 08 08 09 76 40 00      00:03:42.757  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      00:03:42.756  READ LOG EXT
  60 05 38 08 09 76 40 00      00:03:38.943  READ FPDMA QUEUED
  60 10 30 c2 a4 2e 40 00      00:03:38.913  READ FPDMA QUEUED
  61 08 28 60 09 e0 40 00      00:03:38.913  WRITE FPDMA QUEUED


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




mint@mint:~/Desktop$ sudo smartctl -q errorsonly -a /dev/sda
ATA Error Count: 30657 (device log contains only the most recent five errors)
Error 30657 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
Error 30656 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
Error 30655 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
Error 30654 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)
Error 30653 occurred at disk power-on lifetime: 12750 hours (531 days + 6 hours)



```

---

### Post by TheFu on 2019-03-17
The stuff I look at is:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0 
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       3184
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       416
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
```

196 - is fine.
197 is bad.  Replace, immediately. [https://kb.acronis.com/content/9133](https://kb.acronis.com/content/9133)

I would replace the disk immediately.  Might use this disk for sneakernet needs going forward.  I wouldn't use it for any data or even backup data.

---

### Post by kowalski215 on 2019-03-17
Thank you for your quick reply! Just to know, isn't there a way to re-allocate those sectors? Maybe with some software.. Or is that critical as you described? Thank you again

---

