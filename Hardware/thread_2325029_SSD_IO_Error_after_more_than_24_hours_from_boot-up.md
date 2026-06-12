---
title: "SSD I/O Error after more than 24 hours from boot-up"
date: 2016-05-18
forum: Hardware
---

### Post by Michael_Peng on 2016-05-18
My home server runs on a Silicon Power S60 solid state drive (a budget product), and it has been failing recently after more than 24 hours from boot. (in other words, when the drive fails, system uptime is more than 24 hours)
[B]
Symptoms when the drive is encountering issues:[/B] a random amount of commands fail, such as /sbin/poweroff, /usr/bin/sudo, and a few more that I've tested, including dmesg and cat. Because of the shutdown / restart commands failing, I have to press the power button for a force poweroff. When I start it up afterwards, the drive seems fine again.

Output of ```
smartctl /dev/sda -x
```:
```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.2.0-36-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     SPCC Solid State Disk
Serial Number:    FF2E0752040801329467
Firmware Version: S9FM02.0
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed May 18 08:04:25 2016 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM level is:     254 (maximum performance)
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, frozen [SEC2]
Wt Cache Reorder: Unavailable

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
data collection:         (   30) seconds.
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
recommended polling time:      (   2) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     -O-R--   100   100   000    -    0
  9 Power_On_Hours          -O--C-   100   100   000    -    3894
 12 Power_Cycle_Count       -O--C-   100   100   000    -    555
168 Unknown_Attribute       -O--C-   100   100   000    -    0
170 Unknown_Attribute       PO--C-   100   100   010    -    14
173 Unknown_Attribute       ------   100   100   000    -    23265357
192 Power-Off_Retract_Count -O--C-   100   100   000    -    18
194 Temperature_Celsius     PO---K   070   070   000    -    30
196 Reallocated_Event_Count ------   100   100   000    -    0
218 Unknown_Attribute       ------   100   100   000    -    0
241 Total_LBAs_Written      -O--C-   100   100   000    -    5642059
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O     51  Comprehensive SMART error log
0x03       GPL     R/O     64  Ext. Comprehensive SMART error log
0x04       GPL,SL  R/O      8  Device Statistics log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log

SMART Extended Comprehensive Error Log Version: 1 (64 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Commands not supported

Device Statistics (GP Log 0x04)
Page Offset Size         Value  Description
  7  =====  =                =  == Solid State Device Statistics (rev 1) ==
  7  0x008  1                2  Percentage Used Endurance Indicator

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  4            3  Transition from drive PhyRdy to drive PhyNRdy
0x000a  4            3  Device-to-host register FISes sent due to a COMRESET
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0010  2            0  R_ERR response for host-to-device data FIS, non-CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x0013  2            0  R_ERR response for host-to-device non-data FIS, non-CRC


```

**Is there a software error, or should I replace this SSD?**

---

### Post by QDR06VV9 on 2016-05-18
I would think seriously of replacing that drive soon!
Just for example below is how mine reads.
```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA)
Device Model:     WDC WD5000AAKS-00V1A0
Serial Number:    WD-WCAWF0858813
LU WWN Device Id: 5 0014ee 157ad709a
Firmware Version: 05.01D05
User Capacity:    500,106,780,160 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed May 18 10:47:26 2016 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)    Offline data collection activity
                    was aborted by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 7980) seconds.
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
recommended polling time:      (  95) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1145
  3 Spin_Up_Time            0x0027   142   140   021    Pre-fail  Always       -       3858
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2639
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       10066
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2564
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       919
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1719
194 Temperature_Celsius     0x0022   099   086   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   191   191   000    Old_age   Always       -       784
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1460
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged
```

---

### Post by Michael_Peng on 2016-05-18
Thanks for your response. I will get a replacement, meanwhile I will investigate the problems on this drive further. It seems to me that my smartctl output is not detecting any errors.

---

