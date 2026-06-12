---
title: "Smartctl Shows Bad Sectors Read Failure"
date: 2019-09-10
forum: Hardware
---

### Post by hifiuser on 2019-09-10
Hello. 

**_smartctl -a _**shows I have some bad sectors in 2 partitions (full output below). 

I am trying to correct those errors so I can use the disk again (self-test reports a Read Failure).


Questions:

[LIST=1]
[*]**_Current_Pending_Sector_** value is 368. Does that mean there are potentially 368 bad sectors on the drive? 
[*]After correcting these 368 bad sectors can I then _**mount**_ the drive? 
[*]I will use _**dd**_ to zero out the bad blocks/sectors, correct? 
[*]Before that can I _**recover the data**_ in these bad blocks?  Just in case the data is critical data... 
[*]From the above outputs,  is any _**PHYSICAL problem**_ with the disk? After fix all the bad sectors it is going to work again? 
[/LIST]


Thank you so so much!!!!





```
# smartctl -a /dev/sdb
smartctl 6.6 2017-11-05 r4594 [x86_64-linux-5.0.0-13-generic] (local build)
Copyright (C) 2002-17, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST1000LM035-1RK172
Serial Number:    WDE4S5YD
LU WWN Device Id: 5 000c50 0a855e37a
Firmware Version: ACM1
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Sep  9 03:34:09 2019 UTC
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
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x71) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 166) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   080   052   006    Pre-fail  Always       -       107767397
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   037   037   020    Old_age   Always       -       65535
  5 Reallocated_Sector_Ct   0x0033   097   097   036    Pre-fail  Always       -       1672
  7 Seek_Error_Rate         0x000f   082   060   045    Pre-fail  Always       -       4453874815
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       5653 (173 92 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       691
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       28429
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   055   040    Old_age   Always       -       31 (Min/Max 20/31)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       92
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       98
193 Load_Cycle_Count        0x0032   042   042   000    Old_age   Always       -       116839
194 Temperature_Celsius     0x0022   031   045   000    Old_age   Always       -       31 (0 11 0 0 0)
197 Current_Pending_Sector  0x0012   096   095   000    Old_age   Always       -       368
198 Offline_Uncorrectable   0x0010   096   095   000    Old_age   Offline      -       368
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       5460 (18 67 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       10332521622
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       13791968337
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 28431 (device log contains only the most recent five errors)
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

Error 28431 occurred at disk power-on lifetime: 5444 hours (226 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00   3d+20:04:14.516  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00   3d+20:04:14.505  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00   3d+20:04:14.479  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00   3d+20:04:14.477  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   3d+20:04:14.465  SET FEATURES [Set transfer mode]

Error 28430 occurred at disk power-on lifetime: 5444 hours (226 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00   3d+20:04:14.260  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:14.259  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:14.259  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:14.259  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:14.259  READ FPDMA QUEUED

Error 28429 occurred at disk power-on lifetime: 5444 hours (226 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00   3d+20:04:14.031  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00   3d+20:04:14.021  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00   3d+20:04:13.995  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00   3d+20:04:13.994  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   3d+20:04:13.981  SET FEATURES [Set transfer mode]

Error 28428 occurred at disk power-on lifetime: 5444 hours (226 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00   3d+20:04:13.761  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:13.721  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:13.721  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:13.721  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00   3d+20:04:13.721  READ FPDMA QUEUED

Error 28427 occurred at disk power-on lifetime: 5444 hours (226 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00   3d+20:04:13.521  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00   3d+20:04:13.511  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00   3d+20:04:13.484  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00   3d+20:04:13.483  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   3d+20:04:13.470  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      5653         291803192
# 2  Short offline       Completed: read failure       90%      5653         291803192
# 3  Extended offline    Completed: read failure       90%      5652         291803192

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

FDIISK:


```
Device             Start              End           Sectors           Size     Type
/dev/sda1           2048           206,847            204,800           100M     Microsoft basic data
/dev/sda2         239,616         289,302,112     289,062,497     137.9G Microsoft basic data
/dev/sda3          291,743,744     869,009,895     577,266,152     275.3G Microsoft basic data

(sda3 is infact LUKS encrypted ext4 and not NTFS. sda2 is NTFS).

```

FSCK:

```
# fsck.ext4 -v /dev/mapper/backup1
e2fsck 1.44.6 (5-Mar-2019)
Error reading block 10,3841,791 (Invalid argument).  Ignore error<y>? yes
Force rewrite<y>? yes
Superblock has an invalid journal (inode 8).
Clear<y>? yes
*** journal has been deleted ***

The filesystem size (according to the superblock) is 207,718,400 blocks
The physical size of the device is 72,154,173 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes
Error writing block 103,841,791 (Invalid argument).  Ignore error<y>? yes

/dev/mapper/backup1: ***** FILE SYSTEM WAS MODIFIED *****
```

---

### Post by TheFu on 2019-09-11
A disk with that many errors cannot be trusted.  Buy a new one and move on.  

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   080   052   006    Pre-fail  Always       -       **107767397**
  5 Reallocated_Sector_Ct   0x0033   097   097   036    Pre-fail  Always       -       **1672**
  7 Seek_Error_Rate         0x000f   082   060   045    Pre-fail  Always       -       **4453874815**
**187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       [B]28429**[/B]
**191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       92** 0 0 0)
**197 Current_Pending_Sector  0x0012   096   095   000    Old_age   Always       -       368**
**198 Offline_Uncorrectable   0x0010   096   095   000    Old_age   Offline      -       368**
```

Stop drop-kicking the HDD.   I'm surprised the disk even spins after 92 g-sense errors!

[LIST=1]
[*]Stop using this storage.  Unplug the power
[*]Get 2 new replacement storage devices
[*]Mirror the old onto the new using ddrescue; this will take some time
[*]Only attempt data recovery on the new disk, after you mirror it.
[/LIST]

Now you have 2 new storage devices. Use one for primary storage and use the other for backups.  Backups mean never having to deal with data loss again.  About once a year, I need backups to solve some issue with my systems.  Almost always, it was caused by me being stupid, but some times  a disk will fail.  Having backups turns total data loss into a minor inconvenience.

---

### Post by Autodave on 2019-09-12
Follow TheFu's instructions and when done, throw that old drive away.

---

