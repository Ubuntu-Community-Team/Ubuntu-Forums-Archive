---
title: "smartctl- Error 541 occurred at disk power-on lifetime"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by deepclutch on 2008-04-21
Hi,
I got a seagate 160GB sata hdd.when I ran smartctl -a /dev/sda  on this,it complains about [B]Error 545 occurred at disk power-on lifetime: 884 hours (36 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

[/B]Is this something I have to take care of?[B]

Thanks!
[/B]```
localhost:~# smartctl -a /dev/sda 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.9 family
Device Model:     ST3160211AS
Serial Number:    6PT1ZH4K
Firmware Version: 3.AAE
User Capacity:    160,040,803,840 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr 22 00:48:56 2008 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
**SMART overall-health self-assessment test result: PASSED**

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 430) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  54) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   094   006    Pre-fail  Always       -       92854892
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       443
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   074   060   030    Pre-fail  Always       -       4321255946
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       893
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       481
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   058   052   045    Old_age   Always       -       42 (Lifetime Min/Max 32/42)
194 Temperature_Celsius     0x0022   042   048   000    Old_age   Always       -       42 (0 26 0 0)
195 Hardware_ECC_Recovered  0x001a   061   045   000    Old_age   Always       -       169160628
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 545 (device log contains only the most recent five errors)
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

[B]Error 545 occurred at disk power-on lifetime: 884 hours (36 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.[/B]

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 6e 96 a1 e2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  37 00 01 6e 96 a1 e2 00      04:27:55.591  SET MAX ADDRESS EXT
  27 00 00 6e 96 a1 e0 00      04:27:55.519  READ NATIVE MAX ADDRESS EXT
  37 00 00 6e 96 a1 e2 00      04:27:54.539  SET MAX ADDRESS EXT
  27 00 01 6e 96 a1 e0 00      04:27:54.505  READ NATIVE MAX ADDRESS EXT
  37 00 01 6e 96 a1 e2 00      04:27:54.505  SET MAX ADDRESS EXT

Error 544 occurred at disk power-on lifetime: 884 hours (36 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 6e 96 a1 e2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  37 00 01 6e 96 a1 e2 00      04:27:55.591  SET MAX ADDRESS EXT
  27 00 00 6e 96 a1 e0 00      04:27:55.519  READ NATIVE MAX ADDRESS EXT
  37 00 00 6e 96 a1 e2 00      04:27:54.539  SET MAX ADDRESS EXT
  27 00 01 af 9e a1 e0 00      04:27:54.505  READ NATIVE MAX ADDRESS EXT
  29 00 01 af 9e a1 e0 00      04:27:54.505  READ MULTIPLE EXT

Error 543 occurred at disk power-on lifetime: 880 hours (36 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 6e 96 a1 e2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  37 00 01 6e 96 a1 e2 00      02:03:47.933  SET MAX ADDRESS EXT
  27 00 00 6e 96 a1 e0 00      02:03:47.869  READ NATIVE MAX ADDRESS EXT
  37 00 00 6e 96 a1 e2 00      02:03:45.789  SET MAX ADDRESS EXT
  27 00 01 6e 96 a1 e0 00      02:03:45.730  READ NATIVE MAX ADDRESS EXT
  37 00 01 6e 96 a1 e2 00      02:03:45.505  SET MAX ADDRESS EXT

Error 542 occurred at disk power-on lifetime: 880 hours (36 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 6e 96 a1 e2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  37 00 01 6e 96 a1 e2 00      02:03:44.046  SET MAX ADDRESS EXT
  27 00 00 6e 96 a1 e0 00      02:03:44.046  READ NATIVE MAX ADDRESS EXT
  37 00 00 6e 96 a1 e2 00      02:03:45.789  SET MAX ADDRESS EXT
  27 00 01 af 9e a1 e0 00      02:03:45.730  READ NATIVE MAX ADDRESS EXT
  29 00 01 af 9e a1 e0 00      02:03:45.505  READ MULTIPLE EXT

Error 541 occurred at disk power-on lifetime: 880 hours (36 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 6e 96 a1 e2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  37 00 01 6e 96 a1 e2 00      01:28:30.854  SET MAX ADDRESS EXT
  27 00 00 6e 96 a1 e0 00      01:28:30.788  READ NATIVE MAX ADDRESS EXT
  37 00 00 6e 96 a1 e2 00      01:28:30.645  SET MAX ADDRESS EXT
  27 00 01 6e 96 a1 e0 00      01:28:30.520  READ NATIVE MAX ADDRESS EXT
  37 00 01 6e 96 a1 e2 00      01:28:30.453  SET MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       893         -
# 2  Short offline       Completed without error       00%       893         -
# 3  Extended offline    Interrupted (host reset)      20%       188         -
# 4  Extended offline    Aborted by host               90%       187         -
# 5  Short offline       Completed without error       00%       187         -
# 6  Extended offline    Interrupted (host reset)      90%       187         -
# 7  Extended offline    Aborted by host               90%       186         -
# 8  Short offline       Completed without error       00%       186         -
# 9  Short offline       Completed without error       00%       172         -
#10  Short offline       Completed without error       00%       172         -
#11  Short offline       Completed without error       00%       172         -
#12  Short offline       Completed without error       00%       172         -
#13  Short offline       Completed without error       00%       172         -

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

localhost:~# 

```






```
localhost:~# smartctl -t short /dev/sda &&  smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Tue Apr 22 00:46:34 2008

Use smartctl -X to abort test.
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      20%       188         -
# 2  Extended offline    Aborted by host               90%       187         -
# 3  Short offline       Completed without error       00%       187         -
# 4  Extended offline    Interrupted (host reset)      90%       187         -
# 5  Extended offline    Aborted by host               90%       186         -
# 6  Short offline       Completed without error       00%       186         -
# 7  Short offline       Completed without error       00%       172         -
# 8  Short offline       Completed without error       00%       172         -
# 9  Short offline       Completed without error       00%       172         -
#10  Short offline       Completed without error       00%       172         -
#11  Short offline       Completed without error       00%       172         -
#12  Short offline       Self-test routine in progress 90%       893         -

localhost:~# smartctl -t short /dev/sda &&  smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Tue Apr 22 00:47:58 2008

Use smartctl -X to abort test.
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       893         -
# 2  Extended offline    Interrupted (host reset)      20%       188         -
# 3  Extended offline    Aborted by host               90%       187         -
# 4  Short offline       Completed without error       00%       187         -
# 5  Extended offline    Interrupted (host reset)      90%       187         -
# 6  Extended offline    Aborted by host               90%       186         -
# 7  Short offline       Completed without error       00%       186         -
# 8  Short offline       Completed without error       00%       172         -
# 9  Short offline       Completed without error       00%       172         -
#10  Short offline       Completed without error       00%       172         -
#11  Short offline       Completed without error       00%       172         -
#12  Short offline       Completed without error       00%       172         -
#13  Short offline       Self-test routine in progress 90%       893         -

```

---

