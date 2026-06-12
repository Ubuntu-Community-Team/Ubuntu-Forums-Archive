---
title: "External HDD failing or another problem?"
date: 2012-09-27
forum: Hardware
---

### Post by Caldrac on 2012-09-27
Hi there,

About one month ago I bought an external HDD (CnMemory, 1.5 TB, 3,5", USB 3.0). Some days ago Ubuntu tells me, that the HDD will fail soon. 

Nothing happened, which I could relate to the error in the very moment. No writing on the disk, just reading. No "feelable" read/write errors since it occured, although I stopped using it after one last intensive data exchange. Partitions on HDD are encrypted with crypt.

Regarding the low age of the HDD, I was not convinced, that the message was caused by an HDD-error of some kind and wanted to exclude e.g. a SMART over USB-Bridge or USB 3.0 device on USB 2.0-port error. So I tried to collect as much information about the problem, as I could (snippets and additional information at the end of post) and now I need some help concerning some questions of mine, as I reached my limits. Thanks for any feedback!
[B]
Problem 1[/B]:smartctl "Seek_Error_Rate" astronomicaly high [c.f. snippet 3]

[LIST]
[*]A) Why do all smartctl tests (extended, conveyance, short) fail with "unknown failure" at precisely 90% remaining? [c.f snippet 1, 2]
[*]B) Any chance to get a more informative statement than "unknown failure"? [c.f snippet 2]
[*]C) Any other chance to tell, if A) is related to a HDD error or not?
[/LIST]

**Problem 2** (conincided with Problem 1): Error umounting the partition [c.f snippet 6]. Found a [bugreport]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575") matching the error related to erroneous commands to lower level, perhaps SCSI.

[LIST]
[*]A) What is it's relationship to Problem 1?
[*]B) If there's no relationship, why did it not occure before (no updates done in that time period, validated by var/log/apt/history.log)?
[/LIST]

**Problem 3:** "Sense Key : Recovered Error" in dmesg after mounting [c.f. snippet 7]. Found a [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/704900") matching the error related to USB 3.0 device on USB 2.0-port. I don't know if the problem did occure before the HDD-error.

[LIST]
[*] A) What is it's relationship to Problem 1?
[/LIST]

[COLOR=DimGray]**Problem 4:** Log of temperature while HDD is offline (c.f. snippet 4)?
[/COLOR]
[LIST]
[*][COLOR=DimGray]Edit: Meanwhile I realised, that the column "estimated time" contains no information. Instead it is being rewritten each time starting from the last row hourly backwards.[/COLOR]
[/LIST]

**Snippets:**

**1. Execution of tests**
```
$sudo smartctl -d sat -t long /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 265 minutes for test to complete.
Test will complete after Sat Sep 22 21:37:52 2012

Use smartctl -X to abort test.

$sudo smartctl -d sat -t short /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Sat Sep 22 17:11:15 2012

Use smartctl -X to abort test.
```**2. Listing of executed tests**
```
$sudo smartctl -d sat -l selftest /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%        57         0
# 2  Short offline       Completed: unknown failure    90%        57         0
# 3  Short offline       Completed: unknown failure    90%        57         0
# 4  Short offline       Completed: unknown failure    90%        54         0
# 5  Short offline       Completed: unknown failure    90%        54         0
# 6  Short offline       Completed: unknown failure    90%        54         0
# 7  Short offline       Completed: unknown failure    90%        54         0
# 8  Short offline       Completed: unknown failure    90%        54         0
# 9  Short offline       Completed: unknown failure    90%        52         0
#10  Conveyance offline  Completed: unknown failure    90%        52         0
#11  Extended offline    Completed: unknown failure    90%        52         0
#12  Short offline       Completed: unknown failure    90%        52         0
#13  Short offline       Completed: unknown failure    90%        52         0
```**3. Smart Data**
```
$sudo smartctl -d sat -A /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       157273256
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   027   027   030    Pre-fail  Always   FAILING_NOW 9259950491626
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       57
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       48
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   048   045    Old_age   Always       -       34 (Min/Max 33/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       32
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       59
194 Temperature_Celsius     0x0022   034   052   000    Old_age   Always       -       34 (0 18 0 0 0)
195 Hardware_ECC_Recovered  0x001a   029   017   000    Old_age   Always       -       157273256
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       271738285850674
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       163727096
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1954503573
```**4. All information for device**
```
$sudo smartctl -x -d sat /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST1500DL003-9VT16L
Serial Number:    5YD8W7Z0
LU WWN Device Id: 5 000c50 04976145d
Firmware Version: CC4A
User Capacity:    1.500.301.910.016 bytes [1,50 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat Sep 22 21:56:16 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM level is:     208 (intermediate), recommended: 208
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, NOT FROZEN [SEC1]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
Total time to complete Offline 
data collection:         (  623) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 265) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x30b7)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR--   117   099   006    -    157721032
  3 Spin_Up_Time            PO----   093   092   000    -    0
  4 Start_Stop_Count        -O--CK   100   100   020    -    61
  5 Reallocated_Sector_Ct   PO--CK   100   100   036    -    0
  7 Seek_Error_Rate         POSR--   027   027   030    NOW  9259950491883
  9 Power_On_Hours          -O--CK   100   100   000    -    55
 10 Spin_Retry_Count        PO--C-   100   100   097    -    0
 12 Power_Cycle_Count       -O--CK   100   100   020    -    50
183 Runtime_Bad_Block       -O--CK   100   100   000    -    0
184 End-to-End_Error        -O--CK   100   100   099    -    0
187 Reported_Uncorrect      -O--CK   100   100   000    -    0
188 Command_Timeout         -O--CK   100   100   000    -    0
189 High_Fly_Writes         -O-RCK   100   100   000    -    0
190 Airflow_Temperature_Cel -O---K   073   048   045    -    27 (Min/Max 23/27)
191 G-Sense_Error_Rate      -O--CK   100   100   000    -    0
192 Power-Off_Retract_Count -O--CK   100   100   000    -    34
193 Load_Cycle_Count        -O--CK   100   100   000    -    61
194 Temperature_Celsius     -O---K   027   052   000    -    27 (0 18 0 0 0)
195 Hardware_ECC_Recovered  -O-RC-   029   017   000    -    157721032
197 Current_Pending_Sector  -O--C-   100   100   000    -    0
198 Offline_Uncorrectable   ----C-   100   100   000    -    0
199 UDMA_CRC_Error_Count    -OSRCK   200   200   000    -    0
240 Head_Flying_Hours       ------   100   253   000    -    5239860101170
241 Total_LBAs_Written      ------   100   253   000    -    163727216
242 Total_LBAs_Read         ------   100   253   000    -    1954514612
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
GP/S  Log at address 0x00 has    1 sectors [Log Directory]
SMART Log at address 0x01 has    1 sectors [Summary SMART error log]
SMART Log at address 0x02 has    5 sectors [Comprehensive SMART error log]
GP    Log at address 0x03 has    5 sectors [Ext. Comprehensive SMART error log]
SMART Log at address 0x06 has    1 sectors [SMART self-test log]
GP    Log at address 0x07 has    1 sectors [Extended self-test log]
SMART Log at address 0x09 has    1 sectors [Selective self-test log]
GP    Log at address 0x10 has    1 sectors [NCQ Command Error log]
GP    Log at address 0x11 has    1 sectors [SATA Phy Event Counters]
GP    Log at address 0x21 has    1 sectors [Write stream error log]
GP    Log at address 0x22 has    1 sectors [Read stream error log]
GP/S  Log at address 0x80 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x81 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x82 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x83 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x84 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x85 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x86 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x87 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x88 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x89 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8f has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x90 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x91 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x92 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x93 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x94 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x95 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x96 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x97 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x98 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x99 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9f has   16 sectors [Host vendor specific log]
GP/S  Log at address 0xa1 has   20 sectors [Device vendor specific log]
GP    Log at address 0xa2 has 2248 sectors [Device vendor specific log]
GP/S  Log at address 0xa8 has   20 sectors [Device vendor specific log]
GP/S  Log at address 0xa9 has    1 sectors [Device vendor specific log]
GP    Log at address 0xab has    1 sectors [Device vendor specific log]
GP    Log at address 0xb0 has 2819 sectors [Device vendor specific log]
GP    Log at address 0xbd has  252 sectors [Device vendor specific log]
GP    Log at address 0xbe has 65535 sectors [Device vendor specific log]
GP    Log at address 0xbf has 65535 sectors [Device vendor specific log]
GP/S  Log at address 0xc0 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xe0 has    1 sectors [SCT Command/Status]
GP/S  Log at address 0xe1 has    1 sectors [SCT Data Transfer]

SMART Extended Comprehensive Error Log Version: 1 (5 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%        55         0
# 2  Short offline       Completed: unknown failure    90%        55         0
# 3  Short offline       Completed: unknown failure    90%        55         0
# 4  Extended offline    Completed: unknown failure    90%        57         0
# 5  Short offline       Completed: unknown failure    90%        57         0
# 6  Short offline       Completed: unknown failure    90%        57         0
# 7  Short offline       Completed: unknown failure    90%        54         0
# 8  Short offline       Completed: unknown failure    90%        54         0
# 9  Short offline       Completed: unknown failure    90%        54         0
#10  Short offline       Completed: unknown failure    90%        54         0
#11  Short offline       Completed: unknown failure    90%        54         0
#12  Short offline       Completed: unknown failure    90%        52         0
#13  Conveyance offline  Completed: unknown failure    90%        52         0
#14  Extended offline    Completed: unknown failure    90%        52         0
#15  Short offline       Completed: unknown failure    90%        52         0
#16  Short offline       Completed: unknown failure    90%        52         0

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
SCT Version (vendor specific):       522 (0x020a)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    27 Celsius
Power Cycle Min/Max Temperature:     23/27 Celsius
Lifetime    Min/Max Temperature:     18/52 Celsius
Under/Over Temperature Limit Count:   0/0
SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        59 minutes
Min/Max recommended Temperature:     14/55 Celsius
Min/Max Temperature Limit:           10/60 Celsius
Temperature History Size (Index):    128 (6)

Index    Estimated Time   Temperature Celsius
   7    2012-09-17 16:59     ?  -
   8    2012-09-17 17:58    26  *******
   9    2012-09-17 18:57     ?  -
  10    2012-09-17 19:56    25  ******
  11    2012-09-17 20:55     ?  -
  12    2012-09-17 21:54    25  ******
  13    2012-09-17 22:53     ?  -
  14    2012-09-17 23:52    24  *****
  15    2012-09-18 00:51     ?  -
  16    2012-09-18 01:50    23  ****
  17    2012-09-18 02:49     ?  -
  18    2012-09-18 03:48    39  ********************
  19    2012-09-18 04:47    47  ****************************
  20    2012-09-18 05:46    50  *******************************
  21    2012-09-18 06:45    51  ********************************
 ...    ..(  3 skipped).    ..  ********************************
  25    2012-09-18 10:41    51  ********************************
  26    2012-09-18 11:40    52  *********************************
  27    2012-09-18 12:39    52  *********************************
  28    2012-09-18 13:38    51  ********************************
  29    2012-09-18 14:37    51  ********************************
  30    2012-09-18 15:36    50  *******************************
  31    2012-09-18 16:35     ?  -
  32    2012-09-18 17:34    23  ****
  33    2012-09-18 18:33    42  ***********************
  34    2012-09-18 19:32     ?  -
  35    2012-09-18 20:31    30  ***********
  36    2012-09-18 21:30     ?  -
  37    2012-09-18 22:29    32  *************
  38    2012-09-18 23:28     ?  -
  39    2012-09-19 00:27    23  ****
  40    2012-09-19 01:26    42  ***********************
  41    2012-09-19 02:25     ?  -
  42    2012-09-19 03:24    29  **********
  43    2012-09-19 04:23     ?  -
  44    2012-09-19 05:22    23  ****
  45    2012-09-19 06:21     ?  -
  46    2012-09-19 07:20    24  *****
  47    2012-09-19 08:19     ?  -
  48    2012-09-19 09:18    29  **********
  49    2012-09-19 10:17     ?  -
  50    2012-09-19 11:16    24  *****
  51    2012-09-19 12:15     ?  -
  52    2012-09-19 13:14    26  *******
  53    2012-09-19 14:13     ?  -
  54    2012-09-19 15:12    25  ******
  55    2012-09-19 16:11     ?  -
  56    2012-09-19 17:10    23  ****
  57    2012-09-19 18:09     ?  -
  58    2012-09-19 19:08    26  *******
  59    2012-09-19 20:07     ?  -
  60    2012-09-19 21:06    26  *******
  61    2012-09-19 22:05     ?  -
  62    2012-09-19 23:04    26  *******
  63    2012-09-20 00:03    33  **************
  64    2012-09-20 01:02     ?  -
  65    2012-09-20 02:01    22  ***
  66    2012-09-20 03:00    42  ***********************
  67    2012-09-20 03:59     ?  -
  68    2012-09-20 04:58    21  **
  69    2012-09-20 05:57     ?  -
  70    2012-09-20 06:56    25  ******
  71    2012-09-20 07:55    37  ******************
  72    2012-09-20 08:54     ?  -
  73    2012-09-20 09:53    20  *
  74    2012-09-20 10:52     ?  -
  75    2012-09-20 11:51    21  **
  76    2012-09-20 12:50    40  *********************
  77    2012-09-20 13:49    45  **************************
  78    2012-09-20 14:48     ?  -
  79    2012-09-20 15:47    21  **
  80    2012-09-20 16:46    31  ************
  81    2012-09-20 17:45    42  ***********************
  82    2012-09-20 18:44    46  ***************************
  83    2012-09-20 19:43     ?  -
  84    2012-09-20 20:42    22  ***
  85    2012-09-20 21:41     ?  -
  86    2012-09-20 22:40    24  *****
  87    2012-09-20 23:39     ?  -
  88    2012-09-21 00:38    24  *****
  89    2012-09-21 01:37     ?  -
  90    2012-09-21 02:36    21  **
  91    2012-09-21 03:35     ?  -
  92    2012-09-21 04:34    20  *
  93    2012-09-21 05:33    39  ********************
  94    2012-09-21 06:32    40  *********************
  95    2012-09-21 07:31     ?  -
  96    2012-09-21 08:30    22  ***
  97    2012-09-21 09:29     ?  -
  98    2012-09-21 10:28    41  **********************
  99    2012-09-21 11:27     ?  -
 100    2012-09-21 12:26    41  **********************
 101    2012-09-21 13:25     ?  -
 102    2012-09-21 14:24    41  **********************
 103    2012-09-21 15:23    43  ************************
 104    2012-09-21 16:22    47  ****************************
 105    2012-09-21 17:21     ?  -
 106    2012-09-21 18:20    22  ***
 107    2012-09-21 19:19     ?  -
 108    2012-09-21 20:18    23  ****
 109    2012-09-21 21:17    42  ***********************
 110    2012-09-21 22:16     ?  -
 111    2012-09-21 23:15    22  ***
 112    2012-09-22 00:14    44  *************************
 113    2012-09-22 01:13     ?  -
 114    2012-09-22 02:12    18  -
 115    2012-09-22 03:11    37  ******************
 116    2012-09-22 04:10     ?  -
 117    2012-09-22 05:09    33  **************
 118    2012-09-22 06:08    41  **********************
 119    2012-09-22 07:07    42  ***********************
 120    2012-09-22 08:06     ?  -
 121    2012-09-22 09:05    19  -
 122    2012-09-22 10:04    36  *****************
 123    2012-09-22 11:03     ?  -
 124    2012-09-22 12:02    25  ******
 125    2012-09-22 13:01    38  *******************
 126    2012-09-22 14:00     ?  -
 127    2012-09-22 14:59    38  *******************
   0    2012-09-22 15:58    34  ***************
   1    2012-09-22 16:57     ?  -
   2    2012-09-22 17:56    34  ***************
   3    2012-09-22 18:55     ?  -
   4    2012-09-22 19:54    19  -
   5    2012-09-22 20:53     ?  -
   6    2012-09-22 21:52    23  ****

Warning: device does not support SCT Error Recovery Control command
SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x000a  2            1  Device-to-host register FISes sent due to a COMRESET
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS

```**5. Drive Identity Strings**
```
$sudo smartctl -d sat -P show -a /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-2.6.38-13-generic-pae] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Drive found in smartmontools Database.  Drive identity strings:
MODEL:              ST1500DL003-9VT16L
FIRMWARE:           CC4A
match smartmontools Drive Database entry:
MODEL REGEXP:       ST((10|15|20)00DL00[123])-.*
FIRMWARE REGEXP:    .*
MODEL FAMILY:       Seagate Barracuda Green (Adv. Format)
ATTRIBUTE OPTIONS:  None preset; no -v options are required.
```**6. Error after unmounting HDD**
```
Laufwerk konnte nicht gestoppt werden

Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory
```**7. Error in dmesg**
```
$dmesg
...
[  115.945722] scsi 6:0:0:0: Direct-Access     ST1500DL 003-9VT16L       CC4A PQ: 0 ANSI: 0
[  115.951178] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  115.951534] sd 6:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[  115.952405] sd 6:0:0:0: [sdb] Write Protect is off
[  115.952410] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  115.952414] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  115.953903] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  115.984698]  sdb: sdb1 sdb2
[  115.987259] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  115.987266] sd 6:0:0:0: [sdb] Attached SCSI disk
[  116.097954] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[  116.097969] Descriptor sense data with sense descriptors (in hex):
[  116.097972]         72 01 04 1d 00 00 00 0a 09 0c 00 00 00 00 00 07 
[  116.097983]         00 00 
[  116.097987] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[  124.260812] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 1
[  128.601164] padlock_sha: VIA PadLock Hash Engine not detected.
[  129.225273] EXT3-fs: barriers not enabled
[  129.257154] kjournald starting.  Commit interval 5 seconds
[  129.257884] EXT3-fs (dm-5): warning: maximal mount count reached, running e2fsck is recommended
[  129.264646] EXT3-fs (dm-5): using internal journal
[  129.264651] EXT3-fs (dm-5): mounted filesystem with ordered data mode
[  135.158361] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:26:5b:f2:c6:58 tid = 0
[  146.020489] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[  146.020498] Descriptor sense data with sense descriptors (in hex):
[  146.020500]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 3a 37 
[  146.020511]         00 20 00 34 40 50 
[  146.020518] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[  146.110596] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[  146.110605] Descriptor sense data with sense descriptors (in hex):
[  146.110607]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  146.110619]         00 f4 00 2c 40 50 
[  146.110625] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[ 1864.080976] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[ 1864.080989] Descriptor sense data with sense descriptors (in hex):
[ 1864.080994]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 01 
[ 1864.081014]         00 4f 00 c2 00 50 
[ 1864.081025] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[ 1864.175964] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[ 1864.175973] Descriptor sense data with sense descriptors (in hex):
[ 1864.175976]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1864.175987]         00 f4 00 2c 40 50 
[ 1864.175993] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[ 3664.105443] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[ 3664.105451] Descriptor sense data with sense descriptors (in hex):
[ 3664.105454]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 3664.105465]         00 4f 00 c2 00 50 
[ 3664.105472] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
[ 3664.109317] sd 6:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[ 3664.109324] Descriptor sense data with sense descriptors (in hex):
[ 3664.109327]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 3664.109338]         00 00 00 00 40 50 
[ 3664.109344] sd 6:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
...
```
**Additional information:**

**Version of Ubuntu: 11.04 Natty Narwhal**
```
$uname -a
Linux 2.6.38-13-generic-pae #57-Ubuntu SMP Mon Mar 5 20:00:10 UTC 2012 i686 i686 i386 GNU/Linux
```**Version of smartctl (tested both): **

[LIST]
[*]ubuntu repository version: 5.40
[*]current version: 5.43
[/LIST]

**UBS device:**
```
$lsusb | grep ASM
Bus 002 Device 006: ID 174c:55aa ASMedia Technology Inc.
``````
$lsusb -v -v
...
Bus 002 Device 006: ID 174c:55aa ASMedia Technology Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x174c ASMedia Technology Inc.
  idProduct          0x55aa 
  bcdDevice            1.00
  iManufacturer           2 Asmedia
  iProduct                3 USB to S-ATA
  iSerial                 1             5YD8W7Z0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
...
```

---

### Post by ahallubuntu on 2012-09-27
Hard drives fail all the time, even when fairly new.  Replaces yours under warranty.

---

### Post by oldfred on 2012-09-28
I know nothing about Smart data.

But someone posted this but I think it was about Asrock and the SATA ports.
> 
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!


---

### Post by Caldrac on 2012-09-29
Thanks for your replies.

@ahallubuntu
Well, if it's really an HDD error, there would be no other option. What is startling me, is the "unknown failure" of smartctl tests, which prevents testing exactly that. I assume, smartctl is designed to handle errornous HDDs, and would just tell me if it's broken.

@oldfred
It's just an external media memory, so no OS on it. I also already tested all USB-ports, to see, if it makes any difference. As it worked before, I exclude the hardware as the source of problem. As there were no updates of my OS, I'm also inclined to exclude driverlevel. 

@replacement under warranty
It's not easy, to shift all the data, as I am lacking space. I have a backup HDD (missing a lot of tidying up and new data), but I would have to delete the data on the backup HDD in order to backup the HDD. Even if I would "buffer" the data to exclude reading errors - is there any possibility, that Ubuntu would copy bad bits from an errornous HDD without noticing it?

---

### Post by ahallubuntu on 2012-09-29
While S.M.A.R.T. is semi-standard across hard drives, to the point where open source programs like smartmontools can access S.M.A.R.T. data on almost all hard drives, they may not be able to understand every error or reason for failure from every manufacturer's version of S.M.A.R.T..  This is where running a manufacturer-specific diagnostic utility could give you better information; they might have better information and messaging.   (And you'd probably have better luck if it was a brand-name drive like a Seagate or Western Digital for a good diagnostic utility.)  Still, I would consider an inability to complete a S.M.A.R.T. test to be a fatal error and assume the worst.

While it seems unlikely Ubuntu would not tell you about an error in the filesystem when copying files, what choice do you really have at this point?  You could try running e2fsck before copying the data (assuming it's an ext2/3/4 partition), but then you risk abusing your drive more (since e2fsck puts some load on the drive) and bringing it even closer to death.  If it were me, I'd try copying everything first with rsync, then re-run rsync again.  Or try copying a whole partition with ddrescue, then run e2fsck on the new partition and see if any errors show up.  Then you would know which files were corrupted.

I probably don't need to remind you that it's dangerous to have only one copy of your data on any drive, external or otherwise.  As a rule, I have a minimum of two copies of everything on separate devices.  If I buy a new 2TB drive, I buy two of them pretty much automatically and use one to backup the other one.  I don't give myself the choice of having only one.  Then if one fails (as has happened a few times), I don't have to worry as much - I just replace the bad drive and copy everything again.

---

