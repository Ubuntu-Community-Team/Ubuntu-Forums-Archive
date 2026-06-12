---
title: "Failing badblocks test"
date: 2021-02-08
forum: Hardware
---

### Post by johan-2qie2h on 2021-02-08
I just bought five Toshiba N300 NAS HDWG180UZSVA 8TB and started initial tests to verify that the disks were ok.

My plan is to use them for ZFS, and in accordance with their recommendations I set the Error recovery control to 0.1 seconds:
```
smartctl -l scterc,01,01 /dev/sdg
smartctl -l scterc,01,01 /dev/sdh
smartctl -l scterc,01,01 /dev/sdi
smartctl -l scterc,01,01 /dev/sdj
smartctl -l scterc,01,01 /dev/sdk
```

First I ran a short SMART test:
```
smartctl --test=short /dev/sdg
smartctl --test=short /dev/sdh
smartctl --test=short /dev/sdi
smartctl --test=short /dev/sdj
smartctl --test=short /dev/sdk
```


When no errors were reported I ran a long SMART test:
```
smartctl --test=long  /dev/sdg
smartctl --test=long  /dev/sdh
smartctl --test=long  /dev/sdi
smartctl --test=long  /dev/sdj
smartctl --test=long  /dev/sdk

```

When no errors were reported I ran a test for badblocks with a blocksize of 4096k:
```
badblocks -s -v -w -b 4096 /dev/sdg
badblocks -s -v -w -b 4096 /dev/sdh
badblocks -s -v -w -b 4096 /dev/sdi
badblocks -s -v -w -b 4096 /dev/sdj
badblocks -s -v -w -b 4096 /dev/sdk
```

In the morning after about 21 hours, all disks were continuously failing at every tested block:
```
520923670one, 21:35:38 elapsed. (52493/0/0 errors)
520923671
520923672
520923673
520923674one, 21:35:40 elapsed. (52497/0/0 errors)
520923675
520923676
520923677
520923678one, 21:35:41 elapsed. (52501/0/0 errors)
520923679
^Z
[1]+  Stopped                 sudo badblocks -s -v -w -b 4096 /dev/sdj
```

I suspended the badblocks processes and fetched the SMART info from the disks, and they all had "Uncorrectable error in data" in the SMART error log. The SMART output from the first disk can be found at the bottom of this text, and all other disks show the same errors.

I then resumed the badblocks test on all disks and then they were running fine again on all disks from that point on. The max temperatures for every disks seem ok:
```
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Min/Max 23/39)
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Min/Max 23/39)
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Min/Max 22/38)
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Min/Max 23/38)
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       40 (Min/Max 23/41)
```

Is this an indication that the disks might be bad?

Why would they all start working correctly after a pause?

Best regards,
Johan Moe




SMART output from first disk:
```
==================
=== Attributes ===
==================


smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-65-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       7711
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       12
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       39
 10 Spin_Retry_Count        0x0033   100   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       12
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       15
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       34 (Min/Max 23/38)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   001   000    Old_age   Always       -       184811530
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       38
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       529
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0


====================
=== Capabilities ===
====================


smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-65-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x85)    Offline data collection activity
                    was aborted by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
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
recommended polling time:      ( 829) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


=================
=== Error log ===
=================


smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-65-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 52505 (device log contains only the most recent five errors)
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


Error 52505 occurred at disk power-on lifetime: 38 hours (1 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 51 65 40  Error: UNC at LBA = 0x00655100 = 6639872


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 00 51 65 40 00   1d+13:08:46.395  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:46.394  READ LOG EXT
  60 08 00 f8 50 65 40 00   1d+13:08:46.094  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:46.093  READ LOG EXT
  60 08 00 f0 50 65 40 00   1d+13:08:45.794  READ FPDMA QUEUED


Error 52504 occurred at disk power-on lifetime: 38 hours (1 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 f8 50 65 40  Error: UNC at LBA = 0x006550f8 = 6639864


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 f8 50 65 40 00   1d+13:08:46.094  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:46.093  READ LOG EXT
  60 08 00 f0 50 65 40 00   1d+13:08:45.794  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.793  READ LOG EXT
  60 08 00 e8 50 65 40 00   1d+13:08:45.485  READ FPDMA QUEUED


Error 52503 occurred at disk power-on lifetime: 38 hours (1 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 f0 50 65 40  Error: UNC at LBA = 0x006550f0 = 6639856


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 f0 50 65 40 00   1d+13:08:45.794  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.793  READ LOG EXT
  60 08 00 e8 50 65 40 00   1d+13:08:45.485  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.485  READ LOG EXT
  60 08 00 e0 50 65 40 00   1d+13:08:45.185  READ FPDMA QUEUED


Error 52502 occurred at disk power-on lifetime: 38 hours (1 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 e8 50 65 40  Error: UNC at LBA = 0x006550e8 = 6639848


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 e8 50 65 40 00   1d+13:08:45.485  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.485  READ LOG EXT
  60 08 00 e0 50 65 40 00   1d+13:08:45.185  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.185  READ LOG EXT
  60 08 00 d8 50 65 40 00   1d+13:08:44.885  READ FPDMA QUEUED


Error 52501 occurred at disk power-on lifetime: 38 hours (1 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 e0 50 65 40  Error: UNC at LBA = 0x006550e0 = 6639840


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 e0 50 65 40 00   1d+13:08:45.185  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:45.185  READ LOG EXT
  60 08 00 d8 50 65 40 00   1d+13:08:44.885  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00   1d+13:08:44.885  READ LOG EXT
  60 08 00 d0 50 65 40 00   1d+13:08:44.585  READ FPDMA QUEUED
```

---

