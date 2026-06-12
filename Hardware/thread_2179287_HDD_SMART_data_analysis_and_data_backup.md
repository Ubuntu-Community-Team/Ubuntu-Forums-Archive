---
title: "HDD: SMART data analysis and data backup"
date: 2013-10-07
forum: Hardware
---

### Post by djibdjib on 2013-10-07
Hi everyone,
I have problems with my laptop HDD.
It has become really slow. I read the SMART data and it looks really bad for me, can anyone confirm this?
```
$  sudo smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-54-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD3200BEVT-00ZCT0
Serial Number:    WD-WXE1E10Y2110
LU WWN Device Id: 5 0014ee 25981b222
Firmware Version: 11.01A11
User Capacity:    320 072 933 376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Oct  7 17:46:03 2013 CEST
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
data collection:         ( 9600) seconds.
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
recommended polling time:      ( 113) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   191   185   021    Pre-fail  Always       -       1433
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2446
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4301
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2116
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       326
193 Load_Cycle_Count        0x0032   192   192   000    Old_age   Always       -       25357
194 Temperature_Celsius     0x0022   117   077   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   196   196   000    Old_age   Always       -       212
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 354 (device log contains only the most recent five errors)
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

Error 354 occurred at disk power-on lifetime: 4301 hours (179 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 f8 e7 42 40  Error: UNC 8 sectors at LBA = 0x0042e7f8 = 4384760

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 d5 08 f8 e7 42 25 00      00:06:18.014  READ DMA EXT
  b0 d5 01 00 4f c2 00 00      00:06:18.013  SMART READ LOG
  25 da 08 d1 cd 05 13 00      00:06:18.013  READ DMA EXT
  25 da 08 18 b0 9e 0c 00      00:06:18.012  READ DMA EXT
  25 da 08 1c 90 8b 08 00      00:06:18.012  READ DMA EXT

Error 353 occurred at disk power-on lifetime: 4301 hours (179 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 f8 e7 42 40  Error: UNC 8 sectors at LBA = 0x0042e7f8 = 4384760

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 da 08 f8 e7 42 25 00      00:06:14.902  READ DMA EXT
  b0 da 00 00 4f c2 00 00      00:06:14.820  SMART RETURN STATUS
  25 d1 08 91 cd 05 13 00      00:06:14.819  READ DMA EXT
  25 d1 08 00 b8 9e 0c 00      00:06:14.805  READ DMA EXT
  25 d1 08 5c 90 8b 08 00      00:06:14.805  READ DMA EXT

Error 352 occurred at disk power-on lifetime: 4301 hours (179 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 a0 ea 42 40  Error: UNC 8 sectors at LBA = 0x0042eaa0 = 4385440

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 da 08 a0 ea 42 25 00      00:05:57.749  READ DMA EXT
  25 da 08 70 ea 42 25 00      00:05:54.515  READ DMA EXT
  25 da 01 af ea 42 25 00      00:05:54.504  READ DMA EXT
  25 da 01 ae ea 42 25 00      00:05:54.493  READ DMA EXT
  25 da 01 ad ea 42 25 00      00:05:54.482  READ DMA EXT

Error 351 occurred at disk power-on lifetime: 4301 hours (179 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 70 ea 42 40  Error: UNC 8 sectors at LBA = 0x0042ea70 = 4385392

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 da 08 70 ea 42 25 00      00:05:54.515  READ DMA EXT
  25 da 01 af ea 42 25 00      00:05:54.504  READ DMA EXT
  25 da 01 ae ea 42 25 00      00:05:54.493  READ DMA EXT
  25 da 01 ad ea 42 25 00      00:05:54.482  READ DMA EXT
  25 da 01 ac ea 42 25 00      00:05:54.040  READ DMA EXT

Error 350 occurred at disk power-on lifetime: 4301 hours (179 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ac ea 42 40  Error: UNC 1 sectors at LBA = 0x0042eaac = 4385452

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 da 01 ac ea 42 25 00      00:05:51.101  READ DMA EXT
  25 da 01 ab ea 42 25 00      00:05:49.255  READ DMA EXT
  25 da 01 aa ea 42 25 00      00:05:49.255  READ DMA EXT
  25 da 01 a9 ea 42 25 00      00:05:49.254  READ DMA EXT
  25 da 01 a8 ea 42 25 00      00:05:49.253  READ DMA EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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
I started to backup a 17GB holy file in which I have my honeymoon pictures (and no backup of course).
It is really slow (~100kB/s => 50 hours), anyone has an idea of how I could read it faster?
Thank you for your help,
Regards,
JB

---

### Post by TheFu on 2013-10-07
Bad news.  Usually by the time SMART shows anything, it is too late - though I don't see anything too bad, just a few sectors. Those should be automatically relocated, unless all the spare sectors are already used.

In my world, if I only have 1 copy, then I think i'm screwed. 2 copies is just a little better - 3 let's me sleep at night.

I would pull the drive immediately and the only time I'd use it again is to copy data off to another drive. Try to not let it overheat.
If the data is critical, I'd send it to a data recovery expert and get out my checkbook - $3000+ is the norm. It is cheaper to have multiple backups in the long run.

If that is out of your price range and there arn't any funny sounds coming from the HDD, you could try spinrite or dd_rescue or testdisk or ... badblocks - AFTER you get all the data you can off it.

---

