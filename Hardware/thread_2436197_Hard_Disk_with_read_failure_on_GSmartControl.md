---
title: "Hard Disk with read failure on GSmartControl"
date: 2020-02-02
forum: Hardware
---

### Post by valeg96 on 2020-02-02
Hello everyone,

I own a 6-years old Samsung PC with a 1TB HD Seagate Samsung SpinPoint M8 which I believe is causing a lot of issues on my PC.
I've been using Win10 up until a couple days ago, as I need to work with specialized scientific software that's not available on Linux; the last time I used a Linux release was about 10 years ago. These last 5-6 months my Win10 PC started doing some weid things that culminated with the OS not being able to load (random black screen freezes > nothing clickable and no text > hours to boot and load the desktop > endless recovery/reboot looping). I managed to slow down this destructive and autocatalytic behaviour twice by formatting the PC the first time, and resetting it to a previous image the second time, but now it's gotten out of hand. To try and find out what's wrong we installed Kubuntu (working, with just some minor glitches) and fiddled around with GSmartControl.
Unfortunately it's been a long time since I last used any Linux release and/or dealt with these things so I'd appreciate if someone could check out this error log and give me his opinion.
I've been told that these issues will most likely be fixed by replacing the HD with a SSD, and I'd like to hear what's your take on this.

The attached log is from an Extended Self-test (3h 37m) that ended after about 2 minutes at 10% with a *read* *failure*.

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.3.0-28-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Samsung SpinPoint M8 (AF)
Device Model:     ST1000LM024 HN-M101MBB
Serial Number:    S32HJ9CF203483
LU WWN Device Id: 5 0004cf 20c6f7854
Firmware Version: 2BA30001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Feb  2 10:50:41 2020 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Disabled
APM level is:     254 (maximum performance)
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, NOT FROZEN [SEC1]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (13020) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 217) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   100   100   051    -    12453
  2 Throughput_Performance  -OS--K   252   252   000    -    0
  3 Spin_Up_Time            PO---K   092   087   025    -    2492
  4 Start_Stop_Count        -O--CK   096   096   000    -    4336
  5 Reallocated_Sector_Ct   PO--CK   252   252   010    -    0
  7 Seek_Error_Rate         -OSR-K   252   252   051    -    0
  8 Seek_Time_Performance   --S--K   252   252   015    -    0
  9 Power_On_Hours          -O--CK   100   100   000    -    18755
 10 Spin_Retry_Count        -O--CK   252   252   051    -    0
 12 Power_Cycle_Count       -O--CK   096   096   000    -    4268
191 G-Sense_Error_Rate      -O---K   100   100   000    -    1105
192 Power-Off_Retract_Count -O---K   252   252   000    -    0
194 Temperature_Celsius     -O----   064   042   000    -    29 (Min/Max 10/62)
195 Hardware_ECC_Recovered  -O-RCK   100   100   000    -    0
196 Reallocated_Event_Count -O--CK   252   252   000    -    0
197 Current_Pending_Sector  -O--CK   100   098   000    -    2
198 Offline_Uncorrectable   ----CK   252   252   000    -    0
199 UDMA_CRC_Error_Count    -OS-CK   100   100   000    -    3
200 Multi_Zone_Error_Rate   -O-R-K   100   100   000    -    54781
223 Load_Retry_Count        -O--CK   100   100   000    -    118
225 Load_Cycle_Count        -O--CK   078   078   000    -    227073
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
0x02           SL  R/O      2  Comprehensive SMART error log
0x03       GPL     R/O      2  Ext. Comprehensive SMART error log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      2  Extended self-test log
0x08       GPL     R/O      2  Power Conditions log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  SATA NCQ Queued Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xc0-0xdf  GPL,SL  VS      16  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (2 sectors)
Device Error Count: 11317 (device log contains only the most recent 8 errors)
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

Error 11317 [4] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 02 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.643  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.897  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.897  READ LOG EXT
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.420  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.895  READ FPDMA QUEUED

Error 11316 [3] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.420  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.895  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.895  READ LOG EXT
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.615  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.893  READ FPDMA QUEUED

Error 11315 [2] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.615  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.893  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.893  READ LOG EXT
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.613  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.890  READ FPDMA QUEUED

Error 11314 [1] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.613  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.890  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.890  READ LOG EXT
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.610  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.888  READ FPDMA QUEUED

Error 11313 [0] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.610  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.888  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.888  READ LOG EXT
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.610  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.885  READ FPDMA QUEUED

Error 11312 [7] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.610  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.885  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.885  READ LOG EXT
  60 00 90 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.608  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.883  READ FPDMA QUEUED

Error 11311 [6] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 90 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.608  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.883  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.883  READ LOG EXT
  60 00 90 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.607  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.881  READ FPDMA QUEUED

Error 11310 [5] occurred at disk power-on lifetime: 18746 hours (781 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 08 00 00 0f 1c 2e e0 40 00  Error: UNC at LBA = 0x0f1c2ee0 = 253505248

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 90 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.607  READ FPDMA QUEUED
  60 00 00 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.881  READ FPDMA QUEUED
  61 00 00 00 08 00 00 00 70 57 38 40 00     00:00:00.881  WRITE FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 e0 00     00:00:00.881  READ LOG EXT
  60 00 02 00 08 00 00 0f 1c 2e e0 40 00     00:00:00.407  READ FPDMA QUEUED

SMART Extended Self-test Log Version: 1 (2 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     18754         38368192
# 2  Short offline       Completed: read failure       90%     18748         38368192
# 3  Extended offline    Completed: read failure       90%     18747         38368192
# 4  Short offline       Completed: read failure       90%     18747         38368192

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_read_failure [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Status Version:                  2
SCT Version (vendor specific):       256 (0x0100)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    29 Celsius
Power Cycle Min/Max Temperature:     20/29 Celsius
Lifetime    Min/Max Temperature:     10/63 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         5 minutes
Temperature Logging Interval:        5 minutes
Min/Max recommended Temperature:     -5/80 Celsius
Min/Max Temperature Limit:           -10/85 Celsius
Temperature History Size (Index):    128 (120)

Index    Estimated Time   Temperature Celsius
 121    2020-02-02 00:15    29  **********
 122    2020-02-02 00:20    36  *****************
 ...    ..( 10 skipped).    ..  *****************
   5    2020-02-02 01:15    36  *****************
   6    2020-02-02 01:20    26  *******
   7    2020-02-02 01:25    29  **********
   8    2020-02-02 01:30    31  ************
   9    2020-02-02 01:35    32  *************
  10    2020-02-02 01:40    33  **************
  11    2020-02-02 01:45    34  ***************
  12    2020-02-02 01:50    35  ****************
  13    2020-02-02 01:55    36  *****************
  14    2020-02-02 02:00    36  *****************
  15    2020-02-02 02:05    36  *****************
  16    2020-02-02 02:10    37  ******************
  17    2020-02-02 02:15    35  ****************
  18    2020-02-02 02:20    36  *****************
  19    2020-02-02 02:25    35  ****************
  20    2020-02-02 02:30    37  ******************
  21    2020-02-02 02:35    37  ******************
  22    2020-02-02 02:40    24  *****
  23    2020-02-02 02:45    28  *********
  24    2020-02-02 02:50    30  ***********
  25    2020-02-02 02:55    31  ************
  26    2020-02-02 03:00    33  **************
  27    2020-02-02 03:05    34  ***************
  28    2020-02-02 03:10    35  ****************
 ...    ..(  4 skipped).    ..  ****************
  33    2020-02-02 03:35    35  ****************
  34    2020-02-02 03:40    34  ***************
  35    2020-02-02 03:45    35  ****************
  36    2020-02-02 03:50    35  ****************
  37    2020-02-02 03:55    33  **************
  38    2020-02-02 04:00    31  ************
  39    2020-02-02 04:05    32  *************
  40    2020-02-02 04:10    33  **************
  41    2020-02-02 04:15    32  *************
  42    2020-02-02 04:20    33  **************
  43    2020-02-02 04:25    34  ***************
  44    2020-02-02 04:30    34  ***************
  45    2020-02-02 04:35    35  ****************
 ...    ..(  2 skipped).    ..  ****************
  48    2020-02-02 04:50    35  ****************
  49    2020-02-02 04:55    29  **********
  50    2020-02-02 05:00    32  *************
  51    2020-02-02 05:05    33  **************
  52    2020-02-02 05:10    33  **************
  53    2020-02-02 05:15    33  **************
  54    2020-02-02 05:20    34  ***************
  55    2020-02-02 05:25    33  **************
  56    2020-02-02 05:30    35  ****************
  57    2020-02-02 05:35    32  *************
  58    2020-02-02 05:40    34  ***************
  59    2020-02-02 05:45    35  ****************
  60    2020-02-02 05:50    35  ****************
  61    2020-02-02 05:55    35  ****************
  62    2020-02-02 06:00    34  ***************
 ...    ..(  5 skipped).    ..  ***************
  68    2020-02-02 06:30    34  ***************
  69    2020-02-02 06:35    35  ****************
  70    2020-02-02 06:40    35  ****************
  71    2020-02-02 06:45    23  ****
  72    2020-02-02 06:50    26  *******
  73    2020-02-02 06:55    28  *********
  74    2020-02-02 07:00    29  **********
  75    2020-02-02 07:05    31  ************
  76    2020-02-02 07:10    31  ************
  77    2020-02-02 07:15    31  ************
  78    2020-02-02 07:20    32  *************
  79    2020-02-02 07:25    33  **************
  80    2020-02-02 07:30    33  **************
  81    2020-02-02 07:35    34  ***************
  82    2020-02-02 07:40    34  ***************
  83    2020-02-02 07:45    33  **************
  84    2020-02-02 07:50    34  ***************
 ...    ..( 20 skipped).    ..  ***************
 105    2020-02-02 09:35    34  ***************
 106    2020-02-02 09:40    35  ****************
 107    2020-02-02 09:45    35  ****************
 108    2020-02-02 09:50    34  ***************
 ...    ..(  5 skipped).    ..  ***************
 114    2020-02-02 10:20    34  ***************
 115    2020-02-02 10:25    35  ****************
 116    2020-02-02 10:30    35  ****************
 117    2020-02-02 10:35    36  *****************
 118    2020-02-02 10:40    23  ****
 119    2020-02-02 10:45    28  *********
 120    2020-02-02 10:50    29  **********

SCT Error Recovery Control:
           Read: Disabled
          Write: Disabled

Device Statistics (GP/SMART Log 0x04) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  4            0  Command failed due to ICRC error
0x0002  4            0  R_ERR response for data FIS
0x0003  4            0  R_ERR response for device-to-host data FIS
0x0004  4            0  R_ERR response for host-to-device data FIS
0x0005  4            0  R_ERR response for non-data FIS
0x0006  4            0  R_ERR response for device-to-host non-data FIS
0x0007  4            0  R_ERR response for host-to-device non-data FIS
0x0008  4            0  Device-to-host non-data FIS retries
0x0009  4            2  Transition from drive PhyRdy to drive PhyNRdy
0x000a  4            0  Device-to-host register FISes sent due to a COMRESET
0x000b  4            0  CRC errors within host-to-device FIS
0x000d  4            0  Non-CRC errors within host-to-device FIS
0x000f  4            0  R_ERR response for host-to-device data FIS, CRC
0x0010  4            0  R_ERR response for host-to-device data FIS, non-CRC
0x0012  4            0  R_ERR response for host-to-device non-data FIS, CRC
0x0013  4            0  R_ERR response for host-to-device non-data FIS, non-CRC
0x8e00  4            0  Vendor specific
0x8e01  4            0  Vendor specific
0x8e02  4            0  Vendor specific
0x8e03  4            0  Vendor specific
0x8e04  4            0  Vendor specific
0x8e05  4            0  Vendor specific
0x8e06  4            0  Vendor specific
0x8e07  4            0  Vendor specific
0x8e08  4            0  Vendor specific
0x8e09  4            0  Vendor specific
0x8e0a  4            0  Vendor specific
0x8e0b  4            0  Vendor specific
0x8e0c  4            0  Vendor specific
0x8e0d  4            0  Vendor specific
0x8e0e  4            0  Vendor specific
0x8e0f  4            0  Vendor specific
0x8e10  4            0  Vendor specific
0x8e11  4            0  Vendor specific
```

---

### Post by Autodave on 2020-02-02
I believe that it is time to try and save as much as you can from that drive and at least try another drive.....even if it is a small one just to make sure.  But, I believe that your drive has failed.

---

### Post by valeg96 on 2020-02-02
No worries, I've stopped storing data on that HD as soon as the first  freezes started happening this summer. The only thing I was about to  lose were my latest couple of TES: IV Oblivion game savefiles. Thanks  for the suggestion!

---

### Post by mikewhatever on 2020-02-02
Looks like you need to replace that HDD. Would be a good idea to backup important files asap.

---

### Post by TheFu on 2020-02-02
That disk is failing.  Don't use it for anything going forward, except to copy data off it.  When it does fail, that will be it.  Looks like both the controller and platters are failing from the data.

---

### Post by valeg96 on 2020-02-04
Hello world! I'm a 6-year old PC with a brand new 500GB Samsung 860 EVO SSD and all my important files are safe now! Thank you everyone!

---

### Post by TheFu on 2020-02-04
> **valeg96 said:**
> Hello world! I'm a 6-year old PC with a brand new 500GB Samsung 860 EVO SSD and all my important files are safe now! Thank you everyone!

They aren't safe if you don't have automatic, daily, versioned, backups too.  I prefer 60+ days of backup versions.

---

