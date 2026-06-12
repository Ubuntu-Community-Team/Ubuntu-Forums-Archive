---
title: "Lucid-Disk Utility,SMART Data, Self tests - hangs, does not complete."
date: 2011-07-19
forum: Hardware
---

### Post by emarkay on 2011-07-19
204GB ATA Maxtor 6B200R0 BAH41E00 firmware.

Utility says "disk is Healthy" - and no errors show. However both the Short and Extended self tests hang near the end of the progress bar -; over 2 hours or more.

I have been having an occasional metallic click from the PC, then things stop responding and strange things happen until a full power off is done. I  think is coming from this drive (the other a 250GB 7L250R0 tests fine).

Currently, this disk is has had 2348 power cycles, and is 48C (CPU is 61C, GPU is 54C) for thermal issues, and it's the #1 PC in the sig for reference.  It's in an older homebrew PC with a SIS 661FM2 mainboard and a Celeron processor.

Any other tests to try?

Thanks!

---

### Post by psusi on 2011-07-19
The long test often takes several hours, are you sure that you let it go long enough?  Install the smartmontools package and post the output of sudo smartctl -a /dev/sda.

---

### Post by emarkay on 2011-07-19
```
SDA - the "good" one:
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor MaXLine III family (ATA/133 and SATA/150)
Device Model:     Maxtor 7L250R0
Serial Number:    L50VJELH
Firmware Version: BAH41G10
User Capacity:    251,000,193,024 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue Jul 19 16:14:58 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (  30) seconds.
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
recommended polling time:      ( 100) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   167   163   063    Pre-fail  Always       -       26079
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       1174
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   248   239   187    Pre-fail  Always       -       36280
  9 Power_On_Minutes        0x0032   180   180   000    Old_age   Always       -       374h+41m
 10 Spin_Retry_Count        0x002b   252   252   157    Pre-fail  Always       -       1
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   250   250   000    Old_age   Always       -       1264
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   027   253   000    Old_age   Always       -       44
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       5816
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   252   252   000    Old_age   Always       -       1
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   240   240   000    Old_age   Offline      -       163
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     25489         -

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

************************************

SDB (the one in question):
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
Device Model:     Maxtor 6B200R0
Serial Number:    B61DJQWH
Firmware Version: BAH41E00
User Capacity:    203,928,109,056 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue Jul 19 16:16:02 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (  17)    The self-test routine was aborted by
                    the host.
Total time to complete Offline 
data collection:          (1982) seconds.
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
recommended polling time:      (  89) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   174   173   063    Pre-fail  Always       -       29740
  4 Start_Stop_Count        0x0032   252   252   000    Old_age   Always       -       2942
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   250   241   187    Pre-fail  Always       -       42207
  9 Power_On_Minutes        0x0032   230   230   000    Old_age   Always       -       476h+17m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   248   248   000    Old_age   Always       -       2366
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   033   253   000    Old_age   Always       -       46
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       10148
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   241   241   000    Old_age   Offline      -       145
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
ATA Error Count: 6 (device log contains only the most recent five errors)
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

Error 6 occurred at disk power-on lifetime: 6994 hours (291 days + 10 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 b0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 b0 00      01:50:08.934  IDENTIFY DEVICE
  25 00 40 88 75 45 f0 00      01:50:04.148  READ DMA EXT
  27 00 00 00 00 00 f0 00      01:50:04.147  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 b0 00      01:50:04.139  IDENTIFY DEVICE
  ef 03 46 00 00 00 b0 00      01:50:04.132  SET FEATURES [Set transfer mode]

Error 5 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00  

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 39 00 00 00 00 00 00      00:00:00.000  NOP [Reserved subcommand]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               10%      8121         -
# 2  Extended offline    Aborted by host               40%      8118         -
# 3  Short offline       Aborted by host               10%      8116         -
# 4  Short offline       Aborted by host               10%      8115         -
# 5  Short offline       Aborted by host               10%      8115         -
# 6  Short offline       Completed without error       00%      2252         -
# 7  Short offline       Completed without error       00%      1516         -
# 8  Offline             Aborted by host               70%         0         -

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


So what do I do about "Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum." and the other errors?

Thank you!

---

### Post by psusi on 2011-07-19
The drive appears to be fine; you just kept giving up before the test could quite finish.

---

### Post by emarkay on 2011-07-20
Well I know there's been ongoing issues with it - and this morning the PC won't boot - Boot Disk Not Found.

Been wanting a larger drive anyway....

Marking "Solved".  ;)

---

