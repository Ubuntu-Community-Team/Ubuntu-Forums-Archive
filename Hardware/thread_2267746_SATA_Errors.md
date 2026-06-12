---
title: "SATA Errors"
date: 2015-03-03
forum: Hardware
---

### Post by marseille2 on 2015-03-03
I'm at the end of my rope here. I installed a new SATA drive, and have been miserable ever since. At first it completely locked up the OS, so I changed the cable ... things were good yesterday. Then this morning, it was back to this. 

I took a look at launchpad bugs, and found previous Ubuntu versions mentioning the same of issue -- in relation to power management issues (see [bug 539467]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539467")). I'm running UbuntuStudio 14.04, and don't know if this relates to me.

Is there anything I can do to stop the errors, and prevent another lock-up?


$ uname -a
```
Linux av 3.13.0-44-lowlatency #73-Ubuntu SMP PREEMPT Tue Dec 16 00:48:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

$ tail kern.log

```
Mar  3 12:59:38 av kernel: [ 4891.998037] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar  3 12:59:38 av kernel: [ 4892.006475] ata3.00: configured for UDMA/33
Mar  3 12:59:38 av kernel: [ 4892.006486] ata3: EH complete
Mar  3 13:02:22 av kernel: [ 5056.388672] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0xe frozen
Mar  3 13:02:22 av kernel: [ 5056.388680] ata3: irq_stat 0x00400000, PHY RDY changed
Mar  3 13:02:22 av kernel: [ 5056.388686] ata3: SError: { Persist PHYRdyChg }
Mar  3 13:02:22 av kernel: [ 5056.388694] ata3: hard resetting link
Mar  3 13:02:26 av kernel: [ 5059.719878] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar  3 13:02:26 av kernel: [ 5059.722803] ata3.00: configured for UDMA/33
Mar  3 13:02:26 av kernel: [ 5059.722813] ata3: EH complete
```


$ sudo smartctl -a -d ata /dev/sda

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-44-lowlatency] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST500DM002-1BD142
Serial Number:    Z6EBBMNP
LU WWN Device Id: 5 000c50 0794e400c
Firmware Version: KC48
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Tue Mar  3 13:49:04 2015 PST
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
data collection:         (  600) seconds.
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
recommended polling time:      (  86) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   101   099   006    Pre-fail  Always       -       280280
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1106
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       729831
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       193
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       34
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   098   098   000    Old_age   Always       -       2
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   063   045    Old_age   Always       -       34 (Min/Max 34/34)
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 21 0 0 0)
195 Hardware_ECC_Recovered  0x001a   058   040   000    Old_age   Always       -       280280
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       55h+52m+45.205s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2508963587
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3707711004

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       147         -
# 2  Short offline       Completed without error       00%       146         -

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

### Post by houstonbofh on 2015-03-04
Try another motherboard port as you may just have a bad connector.  Also try fliping AHCI/Legacy in the BIOS to see if it makes a difference.

---

### Post by Yellow Pasque on 2015-03-04
Can you give some info on your motherboard? The fact that it's a SATA 600 drive and only running a SATA150 speeds throws up a red flag for me.

---

### Post by marseille2 on 2015-03-04
Thank-you both for replying! I just got back, but things hit the fan right after my post ... and put me out of commission for the rest of the day:(

So far ... I ran Badblocks, changed the mobo setting from IDE to ACHPI mode, used a different molex connector, and updated the kernel. Now I'm just waiting to see if it happens again. 


Motherboard: [Asrock 970 Extreme4]("ftp://66.226.78.21/manual/970%20Extreme4.pdf") (PDF manual)

UPDATE: It's been a good 24 hours, and my SATA drive speed looks much better. I haven't had any weird drive sounds, freezes, or lock-ups ... so I'm going to mark this solved (crossing my fingers).

$ sudo smartctl -a -d ata /dev/sda

```

[sudo] password for av: 
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-46-lowlatency] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST500DM002-1BD142
Serial Number:    Z6EBBMNP
LU WWN Device Id: 5 000c50 0794e400c
Firmware Version: KC48
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Mar  5 11:41:57 2015 PST
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
data collection:         (  600) seconds.
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
recommended polling time:      (  86) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   105   099   006    Pre-fail  Always       -       7667072
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   093   093   020    Old_age   Always       -       7653
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   060   060   030    Pre-fail  Always       -       1088040
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       222
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       47
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   098   098   000    Old_age   Always       -       2
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 1
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   063   045    Old_age   Always       -       32 (Min/Max 23/32)
194 Temperature_Celsius     0x0022   032   040   000    Old_age   Always       -       32 (0 21 0 0 0)
195 Hardware_ECC_Recovered  0x001a   054   040   000    Old_age   Always       -       7667072
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       76h+37m+11.595s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2146924292
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1799416529

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       147         -
# 2  Short offline       Completed without error       00%       146         -

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

