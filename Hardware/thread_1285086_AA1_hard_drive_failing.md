---
title: "AA1 hard drive failing?"
date: 2009-10-07
forum: Hardware
---

### Post by merizim on 2009-10-07
I have an AA1 150-Aw, 1Gb RAM, 120Gb HD, Ubuntu 9.04. Twice in the last two months Ubuntu has failed to start completely, dumped me to a cli with a background screen saying thatthe X-system has failed to start. It prompts me to run fsck manually which I have done on both occasions, the first time there were about 15 to 20 inode issues which I was prompted to fix and did. The second time there were probably about 50 or so inode issues. The only way I could get around the issue both timse was to reinstall Ubuntu. I came to the conclusion that the hard drive was failing so I installed smartmontools and ran smartctl on the drive. The output was:
=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS543212L9A300
Serial Number:    080708FB0B00LGC0LRUA
Firmware Version: FBBOC40C
User Capacity:    120,034,123,776 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Wed Oct  7 15:16:09 2009 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 645) seconds.
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
recommended polling time:      (  52) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   253   033    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1066
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       1454
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1066
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       24
193 Load_Cycle_Count        0x0012   091   091   000    Old_age   Always       -       94427
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       32 (Lifetime Min/Max 14/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

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

I was surprised to see that there were no errors logged and am now totally confused as to what is happening. If nayone has any ideas I would be eternally grateful.

Paul.

ps: I keep a seperate home partition so have lost no data.

---

