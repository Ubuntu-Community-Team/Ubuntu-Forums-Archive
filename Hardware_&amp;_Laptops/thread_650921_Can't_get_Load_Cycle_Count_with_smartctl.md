---
title: "Can't get Load_Cycle_Count with smartctl"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by jeeves on 2007-12-26
If I run **sudo smartctl -a /dev/hda** I can get all kinds of information, but not the  **Load_Cycle_Count**.

Anyone know what could be going wrong? Below is a typical output

```
~$ sudo smartctl -a /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3300622A
Serial Number:    5NG7XXXX
Firmware Version: 3.AAH
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Dec 26 20:42:28 2007 PST
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
data collection:                 ( 430) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 105) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   100   006    Pre-fail  Always       -       88384232
  3 Spin_Up_Time            0x0003   086   084   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       547
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   063   030    Pre-fail  Always       -       60930044
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2021
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       551
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Unknown_Attribute       0x0022   062   057   045    Old_age   Always       -       640024614
194 Temperature_Celsius     0x0022   038   043   000    Old_age   Always       -       38 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   082   068   000    Old_age   Always       -       92248847
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

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

### Post by emakarov on 2007-12-27
Same thing for me. What I noted, however, that it was Start_Stop_Count that increased rapidly (several times a minute). I also heard clicks. I followed the instructions at [http://kmmbvnr.googlepages.com/dellinspiron1520ubuntugustycompatibility]("http://kmmbvnr.googlepages.com/dellinspiron1520ubuntugustycompatibility") and both clicking and the increase of Start_Stop_Count stopped. Maybe Start_Stop_Count is something similar to Load_Cycle_Count?

---

### Post by Yellow Pasque on 2007-12-27
> Maybe Start_Stop_Count is something similar to Load_Cycle_Count?
It may be for your drive, but kind of doubt that it's the same for the OP, because the stop/start count is very close to the power cycle count. Some drives may simply not keep conut of Head Loading/Unloading.

---

