---
title: "840 evo ssd switches to read only (bug or hardware failure?)"
date: 2016-11-18
forum: Hardware
---

### Post by thorstenr_42 on 2016-11-18
Hi,
i have a problem with my 840 evo ssd. Suddenly the whole ssd was read-only and my dmesg was filled with the following error messages:

```

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: irq_stat 0x40000001
ata1.00: failed command: READ DMA EXT
ata1.00: cmd 25/00:08:c8:2a:e2/00:00:16:00:00/e0 tag 3 dma 4096 in
     res 51/04:08:c8:2a:e2/00:00:16:00:00/e0 Emask 0x1 (device error)
ata1.00: status: { DRDY ERR }
ata1.00: error: { ABRT }
ata1.00: supports DRM functions and may not be fully accessible
ata1.00: disabling queued TRIM support
ata1.00: supports DRM functions and may not be fully accessible
ata1.00: disabling queued TRIM support
ata1.00: configured for UDMA/133
ata1: EH complete

```
the number after 'tag' in line 4 is changing in the various messages. After rebooting the system everything worked fine again.

Something similar happened last year when i was using debian jessie. However i don't know if it was the same error message. Back then i thought it was the NCQ trim bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1338706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1338706)) which was fixed in kernel 3.19. Therefore i switched to ubuntu gnome 15.10 and now i am using 16.10 and suddenly it started again.
Overall it happened maybe 3 or 4 times and i am afraid that this isn't a bug but a beginning hardware failure. Therefore i did an extended scan with the gnome-disc tool which reported no errors. However there are some smart values which have failed in the past but now seem to be oky. At the end of this is the output of 'smartctl -a /dev/sda' which also contains the smart values. 

Since the 1TB ssd was quite expensive, i am not very keen on replacing it. I can live with a potential hardware defect that suddenly can occur if the device would just 'die'. Then my backup strategy would prevent me from real data loss. However i am afraid of a failing ssd that would start corrupting my files unnoticed and that the corrupted files gradually replace the healthy files in my backups...

So maybe someone can help me interpreting that error and can give me an advice if replacing the ssd despite the costs is the way to go. Thank you!

```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.8.0-27-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Samsung based SSDs
Device Model:     Samsung SSD 840 EVO 1TB
Serial Number:    xxxxxxxxxxxxxx
LU WWN Device Id: x xxxxxx xxxxxxxxxx
Firmware Version: EXT0DB6Q
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Nov 18 13:24:53 2016 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (15000) seconds.
Offline data collection
capabilities:              (0x53) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 250) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   001   010    Pre-fail  Always   In_the_past 0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       4181
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       4042
177 Wear_Leveling_Count     0x0013   099   099   000    Pre-fail  Always       -       9
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   001   010    Pre-fail  Always   In_the_past 0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   001   010    Pre-fail  Always   In_the_past 0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   066   050   000    Old_age   Always       -       34
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
199 CRC_Error_Count         0x003e   100   100   000    Old_age   Always       -       0
235 POR_Recovery_Count      0x0012   099   099   000    Old_age   Always       -       136
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       18509278920

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%         3         -
# 2  Extended offline    Aborted by host               00%         1         -
# 3  Short offline       Completed without error       00%         0         -
# 4  Short offline       Completed without error       00%         0         -
# 5  Short offline       Completed without error       00%         0         -
# 6  Short offline       Completed without error       00%         0         -
# 7  Short offline       Completed without error       00%         0         -
# 8  Short offline       Completed without error       00%         1         -

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

