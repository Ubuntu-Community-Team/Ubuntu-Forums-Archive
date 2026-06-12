---
title: "hd may be failing - need help with analysis"
date: 2020-05-24
forum: Hardware
---

### Post by ATSC on 2020-05-24
Hello lads and ladettes :-)



my hd seems to be going down the drain. I performed a test with smartctl but I'm having difficulties to understand all the data. Can someone help? Here's the output:
Many thanks in advance!

```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate DB35.3
Device Model:     ST3160215ACE
Serial Number:    5RX3KW2J
Firmware Version: 3.ACB
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 (minor revision not indicated)
Local Time is:    Sun May 24 19:41:54 2020 UTC
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
data collection:         (15556) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  54) minutes.
SCT capabilities:            (0x0031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       34172656
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2714
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       34891046
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       6031
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2767
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   049   045    Old_age   Always       -       36 (Min/Max 35/36)
194 Temperature_Celsius     0x0022   036   051   000    Old_age   Always       -       36 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   095   074   000    Old_age   Always       -       205021561
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6031         -
# 2  Short offline       Completed without error       00%      6031         -
# 3  Short offline       Completed without error       00%      4008         -

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

### Post by Autodave on 2020-05-24
Someone higher on the payscale will come along that knows a little more than I do, but I don't see anything major wrong.  Realize that a passed test does not mean that there aren't problems. it just means that they didn't occur during the test.

What exactly is happening that makes you suspect a HDD problem?

---

### Post by ATSC on 2020-05-24
Several odd problems including (I believe) read/write errors during the startup-sequence.

---

### Post by TheFu on 2020-05-25
How much is your data worth?  more than $40?  if so, buy a replacement disk.  Regardless, have the backups you need, now.

There are some funny things in the output.  SMART data doesn't always show clear failures before death. 22% of the time, disks fail w/o any warning.

---

### Post by Yellow Pasque on 2020-05-26
> **ATSC said:**
> Several odd problems including (I believe) read/write errors during the startup-sequence.

Do you get the same errors if you boot a LiveUSB?

[QUOTE=TheFu]There are some funny things in the output.[/QUOTE]

Seagate doesn't make their SMART data easy to read. This might explain some of the odd things you see: [http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html](http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html)

> How much is your data worth? more than $40? if so, buy a replacement disk. Regardless, have the backups you need, now.

I usually don't recommend throwing money at problems, but replacing a 160GB PATA disk with a similar or larger SATA SSD would be well worth the $ to me, especially if I was using it for a boot/system disk. It will be much faster (and quieter).

---

### Post by kurt18947 on 2020-05-27
> **Yellow Pasque said:**
> Do you get the same errors if you boot a LiveUSB?



Seagate doesn't make their SMART data easy to read. This might explain some of the odd things you see: [http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html](http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html)



I usually don't recommend throwing money at problems, but replacing a 160GB PATA disk with a similar or larger SATA SSD would be well worth the $ to me, especially if I was using it for a boot/system disk. It will be much faster (and quieter).

If indeed the existing disk is PATA as it appears, commonly available SATA SSDs don't work. OP would need a PATA SSD. The largest PATA SSD I could find on Amazon is 128 GB. and cost $84. They make PATA/SATA converters but 1) I don't know if they would work, particularly would they work as a boot device  2) they wouldn't work/fit in laptops. Probably be easier/cheaper to find a PATA mechanical hard drive.

---

### Post by ATSC on 2020-05-28
> **TheFu said:**
>  more than $40?  if so, buy a replacement disk.

Yep, good idea. Thanks!

> **Yellow Pasque said:**
> Do you get the same errors if you boot a LiveUSB?

No.

/Marking this as solved for now.

---

