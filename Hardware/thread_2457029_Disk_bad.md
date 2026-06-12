---
title: "Disk bad?"
date: 2021-01-24
forum: Hardware
---

### Post by michael351 on 2021-01-24
I have a Western Digital 2TB system drive which I recently 'cloned' using dd.
Before the clone, there were no reallocated sectors and only one pending sector. And it has been this way for more than a year.

During the transfer, however, the original disk reported transfer errors, but continued. After the copy completed, I checked the disk and 28 sectors were re-allocated with 8 unrecoverable.
The disk is 'old', but is working fine. I have it cloned (which works great) so I want to keep using this disk until it fails. My data files are all backed up of course.

Question: In your experience is failure imminent? 
Over the last few days, the pending count has remained the same. I'm just surprised that dd triggered a bunch of disk errors to occur (or were discovered?)

```
smartctl 7.1 2020-04-05 r5049 [x86_64-linux-4.18.0-240.10.1.el8_3.x86_64] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Re
Device Model:     WDC WD2000FYYZ-01UL1B0
Serial Number:    WD-WMC1P0155372
LU WWN Device Id: 5 0014ee 0039b2d16
Firmware Version: 01.01K01
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Jan 24 11:15:04 2021 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM level is:     128 (minimum power consumption without standby)
Rd look-ahead is: Enabled
Write cache is:   Enabled
DSN feature is:   Unavailable
ATA Security is:  Disabled, frozen [SEC2]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (24540) seconds.
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
recommended polling time:      ( 267) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x70bd)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   197   123   051    -    35
  3 Spin_Up_Time            POS--K   171   168   021    -    6408
  4 Start_Stop_Count        -O--CK   100   100   000    -    681
  5 Reallocated_Sector_Ct   PO--CK   200   200   140    -    28
  7 Seek_Error_Rate         -OSR-K   100   253   000    -    0
  9 Power_On_Hours          -O--CK   095   095   000    -    4285
 10 Spin_Retry_Count        -O--CK   100   100   000    -    0
 11 Calibration_Retry_Count -O--CK   100   100   000    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    161
183 Runtime_Bad_Block       -O--CK   100   100   000    -    0
192 Power-Off_Retract_Count -O--CK   200   200   000    -    48
193 Load_Cycle_Count        -O--CK   200   200   000    -    632
194 Temperature_Celsius     -O---K   124   104   000    -    26
196 Reallocated_Event_Count -O--CK   174   174   000    -    26
197 Current_Pending_Sector  -O--CK   200   200   000    -    28
198 Offline_Uncorrectable   ----CK   200   200   000    -    8
199 UDMA_CRC_Error_Count    -O--CK   200   200   000    -    0
200 Multi_Zone_Error_Rate   ---R--   200   199   000    -    26
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O      5  Comprehensive SMART error log
0x03       GPL     R/O      6  Ext. Comprehensive SMART error log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x08       GPL     R/O      2  Power Conditions log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x24       GPL     R/O      1  Current Device Internal Status Data log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa0-0xa7  GPL,SL  VS      16  Device vendor specific log
0xa8-0xb7  GPL,SL  VS       1  Device vendor specific log
0xbd       GPL,SL  VS       1  Device vendor specific log
0xc0       GPL,SL  VS       1  Device vendor specific log
0xc1       GPL     VS      24  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (6 sectors)
Device Error Count: 46 (device log contains only the most recent 24 errors)
    CR     = Command Register
    FEATR  = Features Register
    COUNT  = Count (was: Sector Count) Register
    LBA_48 = Upper bytes of LBA High/Mid/Low Registers ]  ATA-8
    LH     = LBA High (was: Cylinder High) Register    ]   LBA
    LM     = LBA Mid (was: Cylinder Low) Register      ] Register
    LL     = LBA Low (was: Sector Number) Register     ]
    DV     = Device (was: Device/Head) Register
    DC     = Device Control Register
    ER     = Error register
    ST     = Status register
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 46 [21] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b5 38 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b538 = 3854611768

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b5 38 e0 0a     10:18:28.468  READ DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:28.468  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:28.466  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:28.465  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:28.459  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 45 [20] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b5 30 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b530 = 3854611760

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b5 30 e0 0a     10:18:26.566  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b5 28 e0 0a     10:18:26.566  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b5 20 e0 0a     10:18:26.566  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b5 18 e0 0a     10:18:26.565  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b5 10 e0 0a     10:18:26.565  READ DMA EXT

Error 44 [19] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 db e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b4db = 3854611675

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 d8 e0 0a     10:18:24.691  READ DMA EXT
  c8 00 00 00 10 00 00 00 20 1c e0 e0 0a     10:18:24.691  READ DMA
  25 00 00 00 08 00 00 e5 c0 b4 d0 e0 0a     10:18:24.669  READ DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:24.669  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:24.667  IDENTIFY DEVICE

Error 43 [18] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 ce e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b4ce = 3854611662

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 c8 e0 0a     10:18:22.871  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 c0 e0 0a     10:18:22.871  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 b8 e0 0a     10:18:22.871  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 b0 e0 0a     10:18:22.870  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 a8 e0 0a     10:18:22.870  READ DMA EXT

Error 42 [17] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 5a e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b45a = 3854611546

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 58 e0 0a     10:18:20.899  READ DMA EXT
  c8 00 00 00 08 00 00 00 20 33 88 e0 0a     10:18:20.899  READ DMA
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:20.899  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:20.896  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:20.896  SET FEATURES [Set transfer mode]

Error 41 [16] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 54 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b454 = 3854611540

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 50 e0 0a     10:18:19.077  READ DMA EXT
  35 00 00 00 08 00 00 e7 6e c0 d0 e0 0a     10:18:19.077  WRITE DMA EXT
  35 00 00 00 20 00 00 e7 5d 98 60 e0 0a     10:18:19.077  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:19.077  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:19.074  IDENTIFY DEVICE

Error 40 [15] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 48 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b448 = 3854611528

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 48 e0 0a     10:18:17.248  READ DMA EXT
  c8 00 00 00 08 00 00 00 20 33 d8 e0 0a     10:18:17.248  READ DMA
  35 00 00 00 10 00 00 e7 50 70 08 e0 0a     10:18:17.248  WRITE DMA EXT
  ea 00 00 00 00 00 00 e5 c0 d0 e4 e0 0a     10:18:17.202  FLUSH CACHE EXT
  35 00 00 00 22 00 00 e5 c0 d0 c3 e0 0a     10:18:17.202  WRITE DMA EXT

Error 39 [14] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 40 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b440 = 3854611520

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 40 e0 0a     10:18:15.380  READ DMA EXT
  35 00 00 00 01 00 00 e7 50 70 01 e0 0a     10:18:15.380  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:15.380  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:15.377  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:15.377  SET FEATURES [Set transfer mode]

Error 38 [13] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 38 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b438 = 3854611512

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 38 e0 0a     10:18:13.460  READ DMA EXT
  ea 00 00 00 00 00 00 e8 e0 88 af e0 0a     10:18:13.423  FLUSH CACHE EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:13.423  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:13.420  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:13.420  SET FEATURES [Set transfer mode]

Error 37 [12] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 30 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b430 = 3854611504

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 30 e0 0a     10:18:11.509  READ DMA EXT
  c8 00 00 00 08 00 00 00 20 37 40 e0 0a     10:18:11.509  READ DMA
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:11.509  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:11.506  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:11.506  SET FEATURES [Set transfer mode]

Error 36 [11] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b4 28 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b428 = 3854611496

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b4 28 e0 0a     10:18:09.606  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 20 e0 0a     10:18:09.606  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 18 e0 0a     10:18:09.605  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 10 e0 0a     10:18:09.605  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b4 08 e0 0a     10:18:09.605  READ DMA EXT

Error 35 [10] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b3 89 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b389 = 3854611337

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b3 88 e0 0a     10:18:07.587  READ DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:07.587  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:07.584  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:07.584  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:07.578  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 34 [9] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 b3 85 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0b385 = 3854611333

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 b3 80 e0 0a     10:18:05.688  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b3 78 e0 0a     10:18:05.688  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b3 70 e0 0a     10:18:05.688  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b3 68 e0 0a     10:18:05.688  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 b3 60 e0 0a     10:18:05.688  READ DMA EXT

Error 33 [8] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 aa 28 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0aa28 = 3854608936

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 aa 28 e0 0a     10:18:03.575  READ DMA EXT
  35 00 00 00 08 00 00 e5 d8 5c 48 e0 0a     10:18:03.575  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:03.575  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:03.572  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:03.572  SET FEATURES [Set transfer mode]

Error 32 [7] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 aa 21 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0aa21 = 3854608929

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 aa 20 e0 0a     10:18:01.185  READ DMA EXT
  35 00 00 00 10 00 00 e5 e1 cc e8 e0 0a     10:18:01.185  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:18:01.185  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:18:01.182  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:18:01.182  SET FEATURES [Set transfer mode]

Error 31 [6] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 aa 18 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0aa18 = 3854608920

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 aa 18 e0 0a     10:17:59.345  READ DMA EXT
  35 00 00 00 18 00 00 e4 4f a3 98 e0 0a     10:17:59.345  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:59.345  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:59.342  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:17:59.342  SET FEATURES [Set transfer mode]

Error 30 [5] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 aa 11 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0aa11 = 3854608913

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 aa 10 e0 0a     10:17:57.512  READ DMA EXT
  35 00 00 00 08 00 00 e7 76 9b d0 e0 0a     10:17:57.512  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:57.511  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:57.509  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:17:57.509  SET FEATURES [Set transfer mode]

Error 29 [4] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 aa 0a e0 00  Error: UNC 8 sectors at LBA = 0xe5c0aa0a = 3854608906

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 aa 08 e0 0a     10:17:55.711  READ DMA EXT
  25 00 00 00 08 00 00 e5 c0 aa 00 e0 0a     10:17:55.711  READ DMA EXT
  c8 00 00 00 10 00 00 00 20 1c b0 e0 0a     10:17:55.711  READ DMA
  25 00 00 00 08 00 00 e5 c0 a9 f8 e0 0a     10:17:55.711  READ DMA EXT
  35 00 00 00 08 00 00 e4 53 4f 58 e0 0a     10:17:55.711  WRITE DMA EXT

Error 28 [3] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 e8 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9e8 = 3854608872

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 e8 e0 0a     10:17:53.873  READ DMA EXT
  35 00 00 00 10 00 00 e5 e1 cc e0 e0 0a     10:17:53.873  WRITE DMA EXT
  c8 00 00 00 10 00 00 00 20 1c a0 e0 0a     10:17:53.873  READ DMA
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:53.872  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:53.870  IDENTIFY DEVICE

Error 27 [2] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 e0 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9e0 = 3854608864

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 e0 e0 0a     10:17:52.064  READ DMA EXT
  35 00 00 02 80 00 00 e4 5a 2c e8 e0 0a     10:17:52.063  WRITE DMA EXT
  c8 00 00 00 10 00 00 00 20 46 90 e0 0a     10:17:52.040  READ DMA
  35 00 00 00 08 00 00 e7 5c be 00 e0 0a     10:17:52.039  WRITE DMA EXT
  25 00 00 00 08 00 00 e5 c0 a9 d8 e0 0a     10:17:52.022  READ DMA EXT

Error 26 [1] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 d3 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9d3 = 3854608851

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 d0 e0 0a     10:17:49.253  READ DMA EXT
  ea 00 00 00 00 00 00 e5 c0 d0 c2 e0 0a     10:17:49.202  FLUSH CACHE EXT
  35 00 00 00 02 00 00 e5 c0 d0 c1 e0 0a     10:17:49.202  WRITE DMA EXT
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:49.202  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:49.199  IDENTIFY DEVICE

Error 25 [0] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 c8 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9c8 = 3854608840

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 c8 e0 0a     10:17:47.279  READ DMA EXT
  ea 00 00 00 00 00 00 00 20 19 af e0 0a     10:17:47.249  FLUSH CACHE EXT
  c8 00 00 00 10 00 00 00 20 19 a0 e0 0a     10:17:47.236  READ DMA
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:47.236  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:47.233  IDENTIFY DEVICE

Error 24 [23] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 c5 e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9c5 = 3854608837

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 c0 e0 0a     10:17:44.911  READ DMA EXT
  ea 00 00 00 00 00 00 e5 c0 d0 c0 e0 0a     10:17:44.881  FLUSH CACHE EXT
  35 00 00 00 1d 00 00 e5 c0 d0 a4 e0 0a     10:17:44.881  WRITE DMA EXT
  c8 00 00 00 18 00 00 00 20 29 80 e0 0a     10:17:44.873  READ DMA
  35 00 00 00 20 00 00 e2 b2 dd 00 e0 0a     10:17:44.873  WRITE DMA EXT

Error 23 [22] occurred at disk power-on lifetime: 4282 hours (178 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 08 00 00 e5 c0 a9 ba e0 00  Error: UNC 8 sectors at LBA = 0xe5c0a9ba = 3854608826

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 00 00 00 08 00 00 e5 c0 a9 b8 e0 0a     10:17:42.496  READ DMA EXT
  c8 00 00 00 08 00 00 00 20 44 60 e0 0a     10:17:42.496  READ DMA
  27 00 00 00 00 00 00 00 00 00 00 e0 0a     10:17:42.496  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 00 00 00 00 00 a0 0a     10:17:42.494  IDENTIFY DEVICE
  ef 00 03 00 46 00 00 00 00 00 00 a0 0a     10:17:42.493  SET FEATURES [Set transfer mode]

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4259         -

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

SCT Status Version:                  3
SCT Version (vendor specific):       258 (0x0102)
Device State:                        Active (0)
Current Temperature:                    26 Celsius
Power Cycle Min/Max Temperature:     21/26 Celsius
Lifetime    Min/Max Temperature:     17/46 Celsius
Under/Over Temperature Limit Count:   0/0
Vendor specific:
01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -41/85 Celsius
Temperature History Size (Index):    478 (463)

Index    Estimated Time   Temperature Celsius
 464    2021-01-24 03:18    26  *******
 ...    ..( 72 skipped).    ..  *******
  59    2021-01-24 04:31    26  *******
  60    2021-01-24 04:32     ?  -
  61    2021-01-24 04:33    21  **
  62    2021-01-24 04:34    22  ***
  63    2021-01-24 04:35    23  ****
 ...    ..(  2 skipped).    ..  ****
  66    2021-01-24 04:38    23  ****
  67    2021-01-24 04:39    24  *****
  68    2021-01-24 04:40    24  *****
  69    2021-01-24 04:41    25  ******
  70    2021-01-24 04:42    25  ******
  71    2021-01-24 04:43    25  ******
  72    2021-01-24 04:44    26  *******
 ...    ..( 14 skipped).    ..  *******
  87    2021-01-24 04:59    26  *******
  88    2021-01-24 05:00     ?  -
  89    2021-01-24 05:01    27  ********
 ...    ..(  5 skipped).    ..  ********
  95    2021-01-24 05:07    27  ********
  96    2021-01-24 05:08     ?  -
  97    2021-01-24 05:09    21  **
  98    2021-01-24 05:10    22  ***
  99    2021-01-24 05:11    23  ****
 ...    ..(  2 skipped).    ..  ****
 102    2021-01-24 05:14    23  ****
 103    2021-01-24 05:15    24  *****
 104    2021-01-24 05:16    24  *****
 105    2021-01-24 05:17    24  *****
 106    2021-01-24 05:18    25  ******
 ...    ..(  4 skipped).    ..  ******
 111    2021-01-24 05:23    25  ******
 112    2021-01-24 05:24    26  *******
 ...    ..( 22 skipped).    ..  *******
 135    2021-01-24 05:47    26  *******
 136    2021-01-24 05:48    27  ********
 ...    ..( 73 skipped).    ..  ********
 210    2021-01-24 07:02    27  ********
 211    2021-01-24 07:03    26  *******
 ...    ..(251 skipped).    ..  *******
 463    2021-01-24 11:15    26  *******

SCT Error Recovery Control:
           Read:     70 (7.0 seconds)
          Write:     70 (7.0 seconds)

Device Statistics (GP/SMART Log 0x04) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2            4  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            5  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x8000  4         2642  Vendor specific
```

---

### Post by DuckHook on 2021-01-24
HDDs are finicky little beasts. I've had similar experiences where they run great until one day they just don't. Some HDDs provide warning. Others, none.

You've already said that it's a clone drive, presumably for a low importance fallback use. You do need to assess whether it will fail at a highly crticial time, notwithstanding your backups, and how much of a real hardship this would be at that point. An IT variant of Murphy's Law states that fallbacks and backups will be unusable when you need them the most. But if you are sure that it's of low criticality, then you've answered your own query, and can just use it until it fails outright.

---

### Post by DuckHook on 2021-01-24
Perhaps I should also add that smartctl is not a be-all-end-all. It combines some metadata with actual data to try to be predictive, but if you think about it, how can it be anything other than peering into a crystal ball? It's when you do an actual disk access (like you did with dd) that you get real world results. Some firmware is pretty much useless with smartctl (are you listening, Seagate?), so its readings need to be treated with some reservations. It's a good tool, but not a failsafe one.

---

### Post by rsteinmetz70112 on 2021-01-24
It could be issues during the dd transfer. Did you get any errors or warnings? 
For a while I've used ddrescue (apt install gddrescue) to make clones when I want to. It will try to read and write sectors a number of times before moving on. It keeps a log. It can make an image which if interrupted can be resumed. It's designed to recover failing drives.

---

### Post by michael351 on 2021-01-24
Thanks for sharing your experiences and insights. For me, this is the first time I experienced 'warning' about a drive maybe going bad. In the past, my hard drive would just fail (laptops mostly) and I was glad I had a backup of the data or an outright clone. I never experienced a failing drive 'while' I was backing it up, however, which is why I posted the smartctl log info.
I was just curious if others experienced what I just did and if my 2 TB drive has life left to it. It's not critical, hence my curiosity on how long it will last before it goes poof.

The first error was reported after 1.4 TB's were transferred. The OS is on a 500 GB partition (ext4). My "home" partition (for programs and staging) occupies another 1TB and the rest is unused. The 500 GB of unused is useful for reallocation (assuming I understand how reallocation works).

As mentioned if the drive dies tomorrow, I have a clone I can pop in (which was the purpose of the DD) to bring the system back (which I re-tested today). And my non-system data is stored on NAS drives & servers redundantly.

---

