---
title: "Reporting with smartctl"
date: 2010-12-26
forum: Hardware
---

### Post by Rickolati on 2010-12-26
Hi guys

I have a query.. I am getting a read failure on a hard drive:

see below:

> 
sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00J2GB0
Serial Number:    WD-WCAYY0047514
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 27 09:34:45 2010 EST
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
data collection:                 (39600) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3031) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   161   159   021    Pre-fail  Always       -       8916
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   163   163   140    Pre-fail  Always       -       292
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       3753
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       57
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       43
193 Load_Cycle_Count        0x0032   125   125   000    Old_age   Always       -       227912
194 Temperature_Celsius     0x0022   120   104   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   027   027   000    Old_age   Always       -       173
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   199   000    Old_age   Offline      -       3

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      3684         152638424
# 2  Extended offline    Completed: read failure       90%      2880         152638424

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



So if I quote from here:

# 1  Extended offline    Completed: read failure       90%      3684         152638424
 # 2  Extended offline    Completed: read failure       90%      2880         152638424

which was the output of two tests, and

SMART overall-health self-assessment test result: PASSED

How does a read failure translate into a PASSED test result. It doesn not even seem as if the test was completed, as it states 90% remaining.

The drive is also part of a RAID5 array with mdadm.

Can anyone shed light on this?

Regards
Richard

---

