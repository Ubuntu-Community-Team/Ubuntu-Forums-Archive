---
title: "Smartctl test log shows time travel??"
date: 2020-06-17
forum: Hardware
---

### Post by pianowow on 2020-06-17
I got a new drive on Amazon.  I ran a smartctl test when value 9 (power on hours) was 0 hours.  Recently I saw a second test in the log which confused me because it had over 40,000 hours.  I ran a third test to confirm the order of the log, it goes newest to oldest.  See the output here now showing all three tests.

```

~/ sudo smartctl -a /dev/sde
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-106-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     MB4000ECWLR
Serial Number:    PAGZSAET
LU WWN Device Id: 5 000cca 22bcdfabc
Firmware Version: HPG3
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Jun 17 05:34:25 2020 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (   24) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 533) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0027   138   100   054    Pre-fail  Always       -       76
  3 Spin_Up_Time            0x0023   100   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   140   100   020    Pre-fail  Offline      -       26
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       40
 10 Spin_Retry_Count        0x0033   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2
180 Unknown_HDD_Attribute   0x002b   100   100   098    Pre-fail  Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
185 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       161
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   052   048   000    Old_age   Always       -       48 (Min/Max 29/52)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   125   117   000    Old_age   Always       -       48 (Min/Max 23/52)
196 Reallocated_Event_Count 0x0033   100   100   000    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
ATA Error Count: 3
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


Error 3 occurred at disk power-on lifetime: 40829 hours (1701 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 08 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b1 c0 00 00 00 00 e0 00      00:00:02.226  DEVICE CONFIGURATION RESTORE [OBS-ACS-3]
  27 00 00 00 00 00 e0 00      00:00:02.224  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 01 00 00 00 e0 00      00:00:01.813  IDENTIFY DEVICE
  42 00 01 01 00 00 40 00      00:00:01.802  READ VERIFY SECTOR(S) EXT
  ec 00 01 00 00 00 e0 00      00:00:01.800  IDENTIFY DEVICE


Error 2 occurred at disk power-on lifetime: 40829 hours (1701 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 00 00 00


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  27 00 00 00 00 00 e0 00      00:00:02.224  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 01 00 00 00 e0 00      00:00:01.813  IDENTIFY DEVICE
  42 00 01 01 00 00 40 00      00:00:01.802  READ VERIFY SECTOR(S) EXT
  ec 00 01 00 00 00 e0 00      00:00:01.800  IDENTIFY DEVICE
  ec 00 00 00 00 00 00 00      00:00:01.799  IDENTIFY DEVICE


Error 1 occurred at disk power-on lifetime: 40829 hours (1701 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 3f 94 52 03  Error: IDNF 1 sectors at LBA = 0x0352943f = 55743551


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 d0 01 3f 94 52 40 00      00:00:02.979  READ DMA EXT
  25 d0 01 87 52 6a 40 00      00:00:02.963  READ DMA EXT
  25 d0 04 00 00 00 40 00      00:00:02.945  READ DMA EXT
  25 d0 01 af be c0 40 00      00:00:02.926  READ DMA EXT
  25 d0 01 01 00 00 40 00      00:00:02.926  READ DMA EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        40         -
# 2  Short offline       Completed without error       00%         0         -
# 3  Short offline       Completed without error       00%     40829         -


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

How is that first test logged with 40829 hours?  What are these other errors logged a the same amount of hours?  Was I sold a used drive that had 40k hours rolled back?  Is it even possible to roll back the odometer so to speak?

---

