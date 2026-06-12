---
title: "What to do when smart findes bad blocks on hard disk"
date: 2010-12-25
forum: Hardware
---

### Post by UeB on 2010-12-25
Hallo,

I ran a smart test with:
smartctl /dev/sda -t long
and the importent part of the result is:
```

Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      8810         379252423

```

I attached the full output of the smart information.

My question is: What to do about this error?

I found a guide in the internet:
[http://www.vanderzee.org/bad_blocks_howto](http://www.vanderzee.org/bad_blocks_howto)
But I find it way to complicated. I mean if software can find the error there must be software that automates the things mentioned on this site.

thanks in advance and
marry Christmas

---

### Post by karthick87 on 2010-12-25
[B]Output:
[/B]```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MHZ2 BH series
Device Model:     FUJITSU MHZ2250BH G2
Serial Number:    K617T882MJ71
Firmware Version: 8909
User Capacity:    250.059.350.016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Sat Dec 25 13:14:51 2010 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

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
capabilities:              (0x51) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 143) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       7288
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       46137344
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1685
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       0 (2000, 0)
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       1609
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       8814
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1664
182 Erase_Fail_Count_Total  0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   253   253   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0010   100   100   000    Old_age   Offline      -       4
186 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   097   000    Old_age   Always       -       62534723829769
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   253   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   053   000    Old_age   Always       -       32 (Lifetime Min/Max 26/33)
191 G-Sense_Error_Rate      0x0032   253   099   000    Old_age   Always       -       16580610
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       5439571
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       89282
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0 (0, 6835)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       18913
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       3732287716844
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 48 (device log contains only the most recent five errors)
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

Error 48 occurred at disk power-on lifetime: 6964 hours (290 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 b3 c7 ee 9a e0  Error: AMNF 179 sectors at LBA = 0x009aeec7 = 10153671

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 7a ee 9a e0 08      02:48:05.809  READ DMA EXT
  25 00 28 1a 82 c4 e0 08      02:48:05.791  READ DMA EXT
  25 00 20 72 0c 43 e0 08      02:48:05.765  READ DMA EXT
  ef 10 02 00 00 00 a0 08      02:48:05.765  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 08      02:48:05.764  IDENTIFY DEVICE

Error 47 occurred at disk power-on lifetime: 6964 hours (290 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 41 03 c7 ee 9a 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 7a ee 9a 40 08      02:48:00.942  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      02:48:00.942  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 08      02:48:00.941  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      02:48:00.941  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      02:48:00.941  SET FEATURES [Reserved for Serial ATA]

Error 46 occurred at disk power-on lifetime: 6964 hours (290 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 41 03 c7 ee 9a 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 7a ee 9a 40 08      02:47:56.208  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      02:47:56.208  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 08      02:47:56.207  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      02:47:56.207  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      02:47:56.207  SET FEATURES [Reserved for Serial ATA]

Error 45 occurred at disk power-on lifetime: 6964 hours (290 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 41 03 86 22 c1 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 7a ee 9a 40 08      02:47:51.619  READ FPDMA QUEUED
  60 08 00 32 22 c1 40 08      02:47:51.619  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      02:47:51.618  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 08      02:47:51.618  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      02:47:51.617  SET FEATURES [Set transfer mode]

Error 44 occurred at disk power-on lifetime: 6964 hours (290 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 41 03 c6 f0 9a 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 10 32 22 c1 40 08      02:47:46.696  READ FPDMA QUEUED
  60 00 08 7a ee 9a 40 08      02:47:46.696  READ FPDMA QUEUED
  60 00 00 7a ef 9a 40 08      02:47:46.696  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      02:47:46.695  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 08      02:47:46.695  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      8810         379252423
# 2  Short offline       Completed: read failure       90%      8808         379252423
# 3  Extended offline    Aborted by host               90%      8808         -
# 4  Short offline       Interrupted (host reset)      10%      6445         -
# 5  Extended offline    Completed without error       00%      5537         -
# 6  Short offline       Completed without error       00%      1751         -

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

### Post by UeB on 2010-12-26
I already tried to do:
touch /forcefsck

to force a check of the disc at start up but this check did not solve the problem.

It did not even find an error (at least I think so because there were not any special msg during the disk check at start up)

---

### Post by UeB on 2010-12-27
anybody anything?

---

### Post by psusi on 2010-12-27
No, follow the guide.

---

