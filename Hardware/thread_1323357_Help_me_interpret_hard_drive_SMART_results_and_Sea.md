---
title: "Help me interpret hard drive SMART results and Seatools results?"
date: 2009-11-11
forum: Hardware
---

### Post by Depafro on 2009-11-11
Two nights ago my computer was locking up, then shutting itself down. I suspected the problem to be the hard drive, or RAM. RAM is being tested as I write, and has passed 1 pass of MEmtest86+ off the Ubuntu live CD so far. I can still access files on the drive. 

**Seatools Results:**
Short Drive Self-test - FAIL
Long drive self-test FAIL
Short generic PASS
Long Generic PASS

**SmartCTL Output:**


```
sudo smartctl -s on -a /dev/sda2
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MHY2250BH
Serial Number:    K42RT7B25ADW
Firmware Version: 0000000B
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Tue Nov 10 07:30:35 2009 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:          (1009) seconds.
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
recommended polling time:      ( 143) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       42099
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       53149696
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       3335
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       2970
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   078   078   000    Old_age   Always       -       11127
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1046
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       48
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       35001
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       35 (Lifetime Min/Max 0/55)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       133
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       453509120
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       16204
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       1533285041046
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 68 (device log contains only the most recent five errors)
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

Error 68 occurred at disk power-on lifetime: 11122 hours (463 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 0b fc 58 fd 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 20 98 38 a9 40 00      00:57:58.372  READ FPDMA QUEUED
  61 80 18 e0 0a 99 40 00      00:57:58.372  WRITE FPDMA QUEUED
  61 01 10 18 6d 28 40 00      00:57:58.372  WRITE FPDMA QUEUED
  61 10 08 48 58 fd 40 00      00:57:58.372  WRITE FPDMA QUEUED
  ef 10 02 00 00 00 40 00      00:57:58.372  SET FEATURES [Reserved for Serial ATA]

Error 67 occurred at disk power-on lifetime: 11122 hours (463 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 13 d5 40 24 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 13 30 20 2d 12 40 00      00:56:38.343  WRITE FPDMA QUEUED
  61 01 28 e0 84 55 40 00      00:56:38.343  WRITE FPDMA QUEUED
  60 40 20 98 38 a9 40 00      00:56:38.343  READ FPDMA QUEUED
  61 01 18 90 d3 28 40 00      00:56:38.343  WRITE FPDMA QUEUED
  61 08 10 a8 40 24 40 00      00:56:38.343  WRITE FPDMA QUEUED

Error 66 occurred at disk power-on lifetime: 11122 hours (463 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 13 3e 6d 28 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 10 20 48 58 fd 40 00      00:55:18.314  WRITE FPDMA QUEUED
  60 40 18 98 38 a9 40 00      00:55:18.314  READ FPDMA QUEUED
  61 01 10 18 6d 28 40 00      00:55:18.314  WRITE FPDMA QUEUED
  ef 10 02 00 00 00 40 00      00:55:18.314  SET FEATURES [Reserved for Serial ATA]
  ef 10 03 00 00 00 40 00      00:55:18.314  SET FEATURES [Reserved for Serial ATA]

Error 65 occurred at disk power-on lifetime: 11122 hours (463 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 1b 35 08 7e 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 28 a8 40 24 40 00      00:54:03.623  WRITE FPDMA QUEUED
  60 40 20 98 38 a9 40 00      00:54:03.623  READ FPDMA QUEUED
  61 08 18 08 08 7e 40 00      00:54:03.623  WRITE FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:54:03.479  READ LOG EXT
  60 40 10 98 38 a9 40 00      00:53:58.286  READ FPDMA QUEUED

Error 64 occurred at disk power-on lifetime: 11122 hours (463 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 13 be 38 a9 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 10 98 38 a9 40 00      00:53:58.286  READ FPDMA QUEUED
  ef 10 02 00 00 00 40 00      00:53:58.285  SET FEATURES [Reserved for Serial ATA]
  ef 10 03 00 00 00 40 00      00:53:58.285  SET FEATURES [Reserved for Serial ATA]
  ef 03 45 00 00 00 40 00      00:53:58.285  SET FEATURES [Set transfer mode]
  c6 00 10 00 00 00 40 00      00:53:58.285  SET MULTIPLE MODE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     11120         27867326

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

[LIST]
[*]Do I need to buy a new drive?
[*]What does "pre-fail" mean in the smartCTL results?
[*]Which of these variables are important to look at?
[*]Is being on error 68 a bad sign? How many errors are normal?
[/LIST]

---

