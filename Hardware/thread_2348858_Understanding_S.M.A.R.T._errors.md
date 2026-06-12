---
title: "Understanding S.M.A.R.T. errors"
date: 2017-01-08
forum: Hardware
---

### Post by Hammi on 2017-01-08
Hi, I could use some help in understanding S.M.A.R.T. error messages and stats, please.

My syslog is showing:

```
Jan  8 08:14:43 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 08:14:43 radix smartd[2998]: Device: /dev/sdk [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 45 to 44
Jan  8 08:44:43 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 09:14:43 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 09:44:44 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 10:14:44 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 10:44:43 radix smartd[2998]: Device: /dev/sdk [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
Jan  8 10:44:43 radix smartd[2998]: Device: /dev/sdk [SAT], SMART Prefailure Attribute: 7 Seek_Error_Rate changed from 62 to 63
```

I don't quite understand this, because the S.M.A.R.T. status does not show any reallocated sector...?

```
=== START OF INFORMATION SECTION ===
Device Model:     ST6000VN0041-2EL11C

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   079   069   044    Pre-fail  Always       -       77200976
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       1
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   063   060   045    Pre-fail  Always       -       1804493
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       16 (173 12 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   066   040    Old_age   Always       -       30 (Min/Max 20/34)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       152
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       24
194 Temperature_Celsius     0x0022   030   040   000    Old_age   Always       -       30 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   044   034   000    Old_age   Always       -       77200976
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       7 (21 191 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3730948368
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       178451

```

Not sure what to make out of this...

Thanks!

---

### Post by TheFu on 2017-01-08
Replace the disk.
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   079   069   044    Pre-fail  Always       -       77200976
  7 Seek_Error_Rate         0x000f   063   060   045    Pre-fail  Always       -       1804493
```

Backblaze writes a quarterly report about disk failures in their environment. Explains much and shows which disks they have the most luck with.

---

### Post by Hammi on 2017-01-08
Could it also be that smartctl has just difficulties reading the SMART values from the disc?

```
SMART Status not supported: Incomplete response, ATA output registers missing
```

I'm just asking as this disk is brand new.

```
12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1
```

Full smartctl -a output:

```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-57-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST6000VN0041-2EL11C
Serial Number:    LKJHA172
LU WWN Device Id: 5 000c50 093539b6c
Firmware Version: SC61
User Capacity:    6.001.175.126.016 bytes [6,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Jan  8 13:31:03 2017 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Status not supported: Incomplete response, ATA output registers missing
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
Total time to complete Offline 
data collection:         (  567) seconds.
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
recommended polling time:      ( 567) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x50bd)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   079   069   044    Pre-fail  Always       -       77222552
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       1
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   063   060   045    Pre-fail  Always       -       2163387
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       18 (92 209 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   098   098   000    Old_age   Always       -       8590065666
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   065   040    Old_age   Always       -       32 (Min/Max 20/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       152
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   032   040   000    Old_age   Always       -       32 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   015   015   000    Old_age   Always       -       77222552
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       8 (156 54 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3730948400
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       199995

SMART Error Log Version: 1
ATA Error Count: 2
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

Error 2 occurred at disk power-on lifetime: 16 hours (0 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 00 00 00  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 00 ff      16:32:14.531  NOP [Abort queued commands]
  b0 d4 00 81 4f c2 00 00      16:31:54.460  SMART EXECUTE OFF-LINE IMMEDIATE
  b0 d0 01 00 4f c2 00 00      16:31:54.439  SMART READ DATA
  ec 00 01 00 00 00 00 00      16:31:54.428  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      16:31:54.426  IDENTIFY DEVICE

Error 1 occurred at disk power-on lifetime: 16 hours (0 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 00 00 00  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 00 ff      16:31:18.526  NOP [Abort queued commands]
  b0 d4 00 81 4f c2 00 00      16:30:57.466  SMART EXECUTE OFF-LINE IMMEDIATE
  b0 d0 01 00 4f c2 00 00      16:30:57.224  SMART READ DATA
  ec 00 01 00 00 00 00 00      16:30:57.211  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      16:30:57.209  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Self-test routine in progress 90%        18         -
# 2  Extended offline    Interrupted (host reset)      90%        17         -
# 3  Conveyance offline  Completed without error       00%        16         -
# 4  Short offline       Completed without error       00%        16         -
# 5  Short captive       Interrupted (host reset)      70%        16         -
# 6  Short captive       Interrupted (host reset)      70%        16         -

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

### Post by TheFu on 2017-01-08
It may be new to you, but I doubt it is a new disk.
If it was sold as "new", take it back. Get a refund.  However, some SATA controllers/USB connections don't support SMART at all.  I've seen those refuse to provide any SMART data, not like what you are seeing above.

```
$ sudo smartctl -a  /dev/sdg
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-106-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

/dev/sdg: Unknown USB bridge [0x152d:0x0567 (0x205)]

```
It does output some more stuff, not the table with values. Then ...```

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Error Counter logging not supported

Device does not support Self Test logging
```

I have multiple of this same disk - some inside normal disk arrays and some via a cheap ($99) USB3 array.  The normal arrays work as expected with SMART. The cheap one doesn't.

---

### Post by Hammi on 2017-01-13
Ok, so I returned the disk, got a new one elsewhere, and that other disk also immediately starts counting up Raw Read Error Rate and the other values.

I googled around and found, e.g., this: [http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html](http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html)

So it appears that these values actually don't as such mean that there is such a high error rate. It's rather that the disk is counting sectors or something. 

The thing I originally struggled with at the beginning of this thread, by the way, is that smartd apparently keeps sending errors on a daily message, even if that error has been dealt with already and/or the respective disk is no longer in the system. There is probably some configuration option for smartd to change it, and I just haven't found it yet in the manual.

---

