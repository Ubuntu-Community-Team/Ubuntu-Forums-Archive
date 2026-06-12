---
title: "Is my hard drive dieing? Device Fault; Error: ABRT at LBA = 0x00000000 = 0"
date: 2016-04-08
forum: Hardware
---

### Post by charlie0440 on 2016-04-08
I had neglected my server for a very long, just leaving it running without monitoring it. Installed webmin last night and saw one of my drives had [COLOR=#000000][FONT=Courier New]Errors Logged: 65357

[/FONT][/COLOR]Ran a test on the drive:
[COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR]```

smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-25-generic] (local build)Copyright (C) 2002-14, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WCC1T1134740
LU WWN Device Id: 5 0014ee 25df214a5
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Apr  7 22:25:01 2016 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (40500) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 406) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x70bd)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   170   021    Pre-fail  Always       -       6166
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       698
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4345
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       697
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       13
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       684
194 Temperature_Celsius     0x0022   113   104   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
ATA Error Count: 65357 (device log contains only the most recent five errors)
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


Error 65357 occurred at disk power-on lifetime: 4 hours (0 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 01 00 00 00 40 00      02:52:46.536  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:45.523  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:44.510  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:43.497  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:42.484  READ SECTOR(S)


Error 65356 occurred at disk power-on lifetime: 4 hours (0 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 01 00 00 00 40 00      02:52:45.523  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:44.510  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:43.497  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:42.484  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:41.471  READ SECTOR(S)


Error 65355 occurred at disk power-on lifetime: 4 hours (0 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 01 00 00 00 40 00      02:52:44.510  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:43.497  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:42.484  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:41.471  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:40.458  READ SECTOR(S)


Error 65354 occurred at disk power-on lifetime: 4 hours (0 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 01 00 00 00 40 00      02:52:43.497  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:42.484  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:41.471  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:40.458  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:39.445  READ SECTOR(S)


Error 65353 occurred at disk power-on lifetime: 4 hours (0 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 01 00 00 00 40 00      02:52:42.484  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:41.471  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:40.458  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:39.445  READ SECTOR(S)
  20 00 01 00 00 00 40 00      02:52:38.432  READ SECTOR(S)


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4345         -


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

```[COLOR=#000000][FONT=Courier New] 

It seemed to have passed, but it has these errors and I don't know what they mean:

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Courier New]04 61 01 00 00 00 40  Device Fault; Error: ABRT at LBA = 0x00000000 = 0[/FONT][/COLOR]
```

1) Can these be ignored or do I need to replace the drive asap?
2) The drive is still in warranty should I return it to WD?

Any help appreciated.

---

### Post by Alex_Metivier on 2016-04-08
There is a possibility that the drives are going bad. Is the server still running normally?

---

### Post by charlie0440 on 2016-04-08
yes, but note this is a storage drive, the OS is on a SSD.

---

### Post by weatherman2 on 2016-04-08
Run the Extended S.M.A.R.T. test.  There are no bad Attributes yet (that I can see at quick glance - no bad sectors for example).  It's possible the recorded errors were due to an unexpected event like a power failure or something.  You can do this with GSmartControl or (if you don't have a Gui) Smartmontools and the smartctl command.

It should go without saying that you would be backing up this drive regularly anyway, though, right?  Unless you don't care about possibly losing the contents...

---

