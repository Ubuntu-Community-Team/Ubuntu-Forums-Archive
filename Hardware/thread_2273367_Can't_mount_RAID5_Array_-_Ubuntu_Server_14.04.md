---
title: "Can't mount RAID5 Array - Ubuntu Server 14.04"
date: 2015-04-12
forum: Hardware
---

### Post by superandyjamieson on 2015-04-12
My server froze the other night so I had to do a cold reboot, upon logging in I couldn't see my RAID5 Array mounted, I checked in Disk Utility to start the array but recieved this error message.

    ```
Error starting RAID array: Command-line `mdadm --assemble  --scan --uuid "1c13268a:028b8e7e:306b74ea:4cb00f81"' exited with non-zero exit status 2:  (udisks-error-quark, 0)
```

Looking up - exited with non-zero exit status 2

    ```
2 - The array has multiple failed devices such that it is unusable.
```

Which looks like one of the drives became toast, the one with the UUID of "1c13268a:028b8e7e:306b74ea:4cb00f81"

I tried this -

```
[FONT=arial]sudo mdadm --assemble  --scan --uuid "1c13268a:028b8e7e:306b74ea:[/FONT][FONT=arial]4cb00f81" --force[/FONT]
```

But nothing came up, is there anything that I can attempt to do?

Any help or ideas would be greatly appreciated!

---

### Post by weatherman2 on 2015-04-12
First, confirm which drive has actually failed.  Try GSmartControl.  When you figure that out, try removing the failed drive from the array.  Do a web search for instructions on how to do that exactly.

---

### Post by superandyjamieson on 2015-04-13
> **weatherman2 said:**
> First, confirm which drive has actually failed.  Try GSmartControl.  When you figure that out, try removing the failed drive from the array.  Do a web search for instructions on how to do that exactly.

Thanks, I'll try that and report back

---

### Post by superandyjamieson on 2015-04-13
Ran a quick test in GSmartControl, all of the drives passed...

Digging around a bit more, I decided to look at that UUID using -

```
sudo blkid

```
Which produced

```
/dev/sda1: UUID="1c13268a-028b-8e7e-306b-74ea4cb00f81" UUID_SUB="b39e5af7-ec1a-f0c8-961e-17510b9334db" LABEL="AnotherMass:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="1c13268a-028b-8e7e-306b-74ea4cb00f81" UUID_SUB="084693a7-a30e-17e1-3504-bbcd0c256fdd" LABEL="AnotherMass:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="1c13268a-028b-8e7e-306b-74ea4cb00f81" UUID_SUB="eccee9bc-874c-d32f-798a-13f0a4fb2c74" LABEL="AnotherMass:0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="1c13268a-028b-8e7e-306b-74ea4cb00f81" UUID_SUB="a795a957-6a18-00ff-2b20-2a68f6933399" LABEL="AnotherMass:0" TYPE="linux_raid_member" 
/dev/sde1: UUID="eb422a72-f822-4922-9d7f-67990b8b12de" TYPE="ext4" 
/dev/sde5: UUID="1ee03bd9-6029-40fe-96c2-80f92e918ac1" TYPE="swap" 

```

Now I'm guessing that the [COLOR=#000000][FONT=Ubuntu Mono]"1c13268a:028b8e7e:306b74ea:4cb00f81"[/FONT][/COLOR] UUID is for the overall RAID? SDE is the OS SSD.

Any ideas where to go from here?

---

### Post by superandyjamieson on 2015-04-14
Here's some more info if that helps -

```
**sudo smartctl -a /dev/sda**


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WMC4M1167934
LU WWN Device Id: 5 0014ee 6ae6cdf02
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Apr 13 23:55:33 2015 BST
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
data collection:         (26760) seconds.
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
recommended polling time:      ( 270) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   172   168   021    Pre-fail  Always       -       4383
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       103
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10945
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       77
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       645806
194 Temperature_Celsius     0x0022   112   102   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%     10944         -
# 2  Short offline       Completed without error       00%     10944         -
# 3  Short offline       Completed without error       00%     10943         -


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




**sudo smartctl -a /dev/sdb**


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WMC4M0490537
LU WWN Device Id: 5 0014ee 6590437a6
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Apr 13 23:55:59 2015 BST
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
data collection:         (27060) seconds.
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
recommended polling time:      ( 273) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   174   171   021    Pre-fail  Always       -       4300
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       102
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10926
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       102
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       76
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       646924
194 Temperature_Celsius     0x0022   113   102   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%     10925         -
# 2  Short offline       Completed without error       00%     10924         -
# 3  Short offline       Completed without error       00%     10924         -


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




**sudo smartctl -a /dev/sdc**


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EZRX-00DC0B0
Serial Number:    WD-WCC300850556
LU WWN Device Id: 5 0014ee 208f54f65
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Apr 13 23:56:13 2015 BST
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
data collection:         (26280) seconds.
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
recommended polling time:      ( 266) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x70b5)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   173   021    Pre-fail  Always       -       4200
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       103
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10868
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       77
193 Load_Cycle_Count        0x0032   005   005   000    Old_age   Always       -       586172
194 Temperature_Celsius     0x0022   114   105   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     10867         -
# 2  Short offline       Completed without error       00%     10866         -


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




**sudo smartctl -a /dev/sdd**


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WMC4M1582103
LU WWN Device Id: 5 0014ee 6aea1ac3a
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Apr 13 23:56:39 2015 BST
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
data collection:         (28020) seconds.
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
recommended polling time:      ( 283) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   173   021    Pre-fail  Always       -       4200
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       79
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10782
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       79
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       60
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       649169
194 Temperature_Celsius     0x0022   116   110   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     10781         -
# 2  Short offline       Completed without error       00%     10780         -
# 3  Short offline       Completed without error       00%     10707         -


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





```
**cat /etc/mdadm/mdadm.conf**


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This file was auto-generated on Wed, 11 Dec 2013 20:44:28 +0000
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 name=AnotherMass:0 UUID=1c13268a:028b8e7e:306b74ea:4cb00f81

```





```
**sudo mdadm -E /dev/sd[abcd]**


/dev/sda:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
user@AnotherMass:~$ 

```

---

### Post by tgalati4 on 2015-04-14
Well, when a spinning drive stops spinning, the hot grease in the spindle cools down and becomes like glue.  The spin-up becomes problematic.

> 
Spin_Up_Time            0x0027   172   168   021    Pre-fail  Always       -       4383


This is perhaps 4.38 seconds for spin up time, which is quite slow. But, with 11K hours, that is typical.  The drive still works, it's just sluggish.  What is the spin-up time of the other drives?

Keep trying, when the drives warm up, they should spin up faster and then the array should self-assemble.  Now is a good time to clean out the machine and reseat all of the cables.

---

### Post by superandyjamieson on 2015-04-15
Speeds are as follows

```
**/dev/sda**
0x0027   172   168   021    Pre-fail  Always       -      ** 4383**


**/dev/sdb**
0x0027   174   171   021    Pre-fail  Always       -       **4300**


**/dev/sdc**
0x0027   176   173   021    Pre-fail  Always       -       **4200**


**/dev/sdd**
0x0027   176   173   021    Pre-fail  Always       -       **4200**

```

Server has been up for 6 days now :? still not been able to mount the RAID.

---

### Post by tgalati4 on 2015-04-15
So, you have 4 x 2TB in a RAID5 configuration.  The original *mdadm* error was that too many devices failed (perhaps 2 disks went down).  Was there anything in /var/log/syslog that pointed to the original server freeze?  Post any error messages just before the freeze.  It's possible that a power supply problem is not able to support all of your disks causing strange errors.  Check voltages with a voltmeter or try a newer PSU.

If you did indeed have two disks fail (such that SMART didn't pick up the errors--some errors are not captured) then you might have a problem recovering the  pool.  Hardware RAID controllers have their own battery to keep writing to the pool in the event of a power dip, but software RAID is at the mercy of the hardware.  Since your server froze and you don't know exactly what caused it, troubleshooting the RAID5 data pool becomes more difficult.

---

### Post by superandyjamieson on 2015-04-15
Here's the output from **kern.log**

```
Apr  6 07:36:05 AnotherMass kernel: [2619156.047489] type=1400 audit(1428302165.338:157): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=30052 comm="apparmor_parser"
Apr  6 07:36:05 AnotherMass kernel: [2619156.047507] type=1400 audit(1428302165.338:158): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=30052 comm="apparmor_parser"
Apr  6 07:36:05 AnotherMass kernel: [2619156.048439] type=1400 audit(1428302165.338:159): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=30052 comm="apparmor_parser"
Apr  7 08:02:18 AnotherMass kernel: [2707085.926881] type=1400 audit(1428390138.608:160): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=12368 comm="apparmor_parser"
Apr  7 08:02:18 AnotherMass kernel: [2707085.926894] type=1400 audit(1428390138.608:161): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=12368 comm="apparmor_parser"
Apr  7 08:02:18 AnotherMass kernel: [2707085.927468] type=1400 audit(1428390138.608:162): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=12368 comm="apparmor_parser"
Apr  8 07:38:35 AnotherMass kernel: [2792021.276307] type=1400 audit(1428475115.878:163): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=25852 comm="apparmor_parser"
Apr  8 07:38:35 AnotherMass kernel: [2792021.276324] type=1400 audit(1428475115.878:164): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=25852 comm="apparmor_parser"
Apr  8 07:38:35 AnotherMass kernel: [2792021.277254] type=1400 audit(1428475115.878:165): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=25852 comm="apparmor_parser"
Apr  8 23:01:45 AnotherMass kernel: [2847383.320470] radeon 0000:01:05.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Apr  8 23:01:45 AnotherMass kernel: [2847383.320485] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  8 23:01:45 AnotherMass kernel: [2847383.320509] pci 0000:00:00.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320512] pci 0000:00:00.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320518] pci 0000:00:01.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320520] pci 0000:00:01.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320528] radeon 0000:01:05.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320530] radeon 0000:01:05.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320536] pcieport 0000:00:06.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320559] ahci 0000:00:11.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320561] ahci 0000:00:11.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320570] ohci-pci 0000:00:12.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320572] ohci-pci 0000:00:12.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320580] ehci-pci 0000:00:12.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320582] ehci-pci 0000:00:12.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320590] ohci-pci 0000:00:13.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320591] ohci-pci 0000:00:13.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320599] ehci-pci 0000:00:13.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320601] ehci-pci 0000:00:13.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320609] piix4_smbus 0000:00:14.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320610] piix4_smbus 0000:00:14.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320618] pci 0000:00:14.3: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320619] pci 0000:00:14.3: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320627] pci 0000:00:14.4: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320629] pci 0000:00:14.4: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320639] ohci-pci 0000:00:16.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320641] ohci-pci 0000:00:16.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320648] ehci-pci 0000:00:16.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320650] ehci-pci 0000:00:16.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320658] pci 0000:00:18.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320660] pci 0000:00:18.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320664] pci 0000:00:18.1: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320666] pci 0000:00:18.1: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320670] amd64_edac 0000:00:18.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320672] amd64_edac 0000:00:18.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320677] k10temp 0000:00:18.3: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320679] k10temp 0000:00:18.3: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320683] pci 0000:00:18.4: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320684] pci 0000:00:18.4: using default PCI settings
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Linux version 3.13.0-48-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 (Ubuntu 3.13.0-48.80-generic 3.13.11-ckt16)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] KERNEL supported cpus:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Intel GenuineIntel
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   AMD AuthenticAMD
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Centaur CentaurHauls
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d7f8ffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7f9e000-0x00000000d7f9ffff] type 9
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fa0000-0x00000000d7fadfff] ACPI data
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fae000-0x00000000d7fdffff] ACPI NVS
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fe0000-0x00000000d7ffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000019fffffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] SMBIOS 2.6 present.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR default type: uncachable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   00000-9FFFF write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   A0000-EFFFF uncachable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR variable ranges enabled:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   3 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   4 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   5 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   6 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   7 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] TOM2: 00000001a0000000 aka 6656M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Using GB pages for direct mapping
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19fe00000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x19fe00000-0x19fffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19c000000-0x19fdfffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x19c000000-0x19fdfffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x180000000-0x19bffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x180000000-0x19bffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xd7f8ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0xc0000000-0xd7dfffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0xd7e00000-0xd7f8ffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x100000000-0x17fffffff] page 1G
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] RAMDISK: [mem 0x35a4e000-0x36d1efff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: RSDP 00000000000f8f50 000024 (v02 HP    )
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: XSDT 00000000d7fa0100 00007C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: FACP 00000000d7fa0290 0000F4 (v03 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: DSDT 00000000d7fa0620 006947 (v01 HP     ProLiant 00000006 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: FACS 00000000d7fae000 000040
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: APIC 00000000d7fa0390 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: MCFG 00000000d7fa0410 00003C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: SPMI 00000000d7fa0450 000041 (v05 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: OEMB 00000000d7fae040 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HPET 00000000d7fab4e0 000038 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: EINJ 00000000d7fab520 000130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: BERT 00000000d7fab6b0 000030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: ERST 00000000d7fab6e0 0001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HEST 00000000d7fab890 0000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: SSDT 00000000d7fab940 00052A (v01 HP     ProLiant 00000001 AMD  00000001)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No NUMA configuration found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000019fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   NODE_DATA [mem 0x19fff9000-0x19fffdfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199800000-ffff88019f5fffff] on node 0
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Zone ranges:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal   [mem 0x100000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Movable zone start for each node
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Early memory node ranges
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00100000-0xd7f8ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x100000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] On node 0 totalpages: 1539885
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32 zone: 13759 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32 zone: 880528 pages, LIFO batch:31
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal zone: 10240 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal zone: 655360 pages, LIFO batch:31
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] nr_irqs_gsi: 40
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e1fff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e2000-0x000fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f90000-0xd7f9dfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f9e000-0xd7f9ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fa0000-0xd7fadfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fae000-0xd7fdffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fe0000-0xd7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xff9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: [mem 0xf0000000-0xff9fffff] available for PCI devices
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s82368 r8192 d24128 u524288
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] pcpu-alloc: s82368 r8192 d24128 u524288 alloc=1*2097152
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1515801
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Policy zone: Normal
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Checking aperture...
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Node 0: aperture @ f1ba000000 size 32 MB
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] This costs you 64 MB of RAM
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc000000-0xcfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Memory: 5895336K/6159540K available (7385K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 264204K reserved)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Hierarchical RCU implementation.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] console [tty0] enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] allocated 24641536 bytes of page_cgroup
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] hpet clockevent registered
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Apr  8 23:41:52 AnotherMass kernel: [    0.004000] tsc: Detected 2196.381 MHz processor
Apr  8 23:41:52 AnotherMass kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4392.76 BogoMIPS (lpj=8785524)
Apr  8 23:41:52 AnotherMass kernel: [    0.000067] pid_max: default: 32768 minimum: 301
Apr  8 23:41:52 AnotherMass kernel: [    0.000133] Security Framework initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.000184] AppArmor: AppArmor initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.000215] Yama: becoming mindful.
Apr  8 23:41:52 AnotherMass kernel: [    0.000916] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.004859] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.006717] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.006763] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.007154] Initializing cgroup subsys memory
Apr  8 23:41:52 AnotherMass kernel: [    0.007197] Initializing cgroup subsys devices
Apr  8 23:41:52 AnotherMass kernel: [    0.007230] Initializing cgroup subsys freezer
Apr  8 23:41:52 AnotherMass kernel: [    0.007262] Initializing cgroup subsys blkio
Apr  8 23:41:52 AnotherMass kernel: [    0.007293] Initializing cgroup subsys perf_event
Apr  8 23:41:52 AnotherMass kernel: [    0.007326] Initializing cgroup subsys hugetlb
Apr  8 23:41:52 AnotherMass kernel: [    0.008014] tseg: 0000000000
Apr  8 23:41:52 AnotherMass kernel: [    0.008022] CPU: Physical Processor ID: 0
Apr  8 23:41:52 AnotherMass kernel: [    0.008053] CPU: Processor Core ID: 0
Apr  8 23:41:52 AnotherMass kernel: [    0.008084] mce: CPU supports 6 MCE banks
Apr  8 23:41:52 AnotherMass kernel: [    0.008121] LVT offset 0 assigned for vector 0xf9
Apr  8 23:41:52 AnotherMass kernel: [    0.008155] process: using AMD E400 aware idle routine
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] tlb_flushall_shift: 4
Apr  8 23:41:52 AnotherMass kernel: [    0.008342] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Apr  8 23:41:52 AnotherMass kernel: [    0.009921] ACPI: Core revision 20131115
Apr  8 23:41:52 AnotherMass kernel: [    0.012479] ACPI: All ACPI Tables successfully acquired
Apr  8 23:41:52 AnotherMass kernel: [    0.014380] ftrace: allocating 28562 entries in 112 pages
Apr  8 23:41:52 AnotherMass kernel: [    0.029082] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  8 23:41:52 AnotherMass kernel: [    0.068789] smpboot: CPU0: AMD Turion(tm) II Neo N54L Dual-Core Processor (fam: 10, model: 06, stepping: 03)
Apr  8 23:41:52 AnotherMass kernel: [    0.175446] Performance Events: AMD PMU driver.
Apr  8 23:41:52 AnotherMass kernel: [    0.175508] ... version:                0
Apr  8 23:41:52 AnotherMass kernel: [    0.175539] ... bit width:              48
Apr  8 23:41:52 AnotherMass kernel: [    0.175569] ... generic registers:      4
Apr  8 23:41:52 AnotherMass kernel: [    0.175600] ... value mask:             0000ffffffffffff
Apr  8 23:41:52 AnotherMass kernel: [    0.175631] ... max period:             00007fffffffffff
Apr  8 23:41:52 AnotherMass kernel: [    0.175662] ... fixed-purpose events:   0
Apr  8 23:41:52 AnotherMass kernel: [    0.175693] ... event mask:             000000000000000f
Apr  8 23:41:52 AnotherMass kernel: [    0.177481] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  8 23:41:52 AnotherMass kernel: [    0.177608] x86: Booting SMP configuration:
Apr  8 23:41:52 AnotherMass kernel: [    0.177640] .... node  #0, CPUs:      #1
Apr  8 23:41:52 AnotherMass kernel: [    0.190774] x86: Booted up 1 node, 2 CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.190814] process: System has AMD C1E enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.190824] process: Switch to broadcast mode on CPU1
Apr  8 23:41:52 AnotherMass kernel: [    0.190898] smpboot: Total of 2 processors activated (8785.52 BogoMIPS)
Apr  8 23:41:52 AnotherMass kernel: [    0.191624] process: Switch to broadcast mode on CPU0
Apr  8 23:41:52 AnotherMass kernel: [    0.191798] devtmpfs: initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.197367] EVM: security.selinux
Apr  8 23:41:52 AnotherMass kernel: [    0.197398] EVM: security.SMACK64
Apr  8 23:41:52 AnotherMass kernel: [    0.197429] EVM: security.ima
Apr  8 23:41:52 AnotherMass kernel: [    0.197459] EVM: security.capability
Apr  8 23:41:52 AnotherMass kernel: [    0.198093] PM: Registering ACPI NVS region [mem 0xd7fae000-0xd7fdffff] (204800 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.199990] pinctrl core: initialized pinctrl subsystem
Apr  8 23:41:52 AnotherMass kernel: [    0.200109] regulator-dummy: no parameters
Apr  8 23:41:52 AnotherMass kernel: [    0.200170] RTC time: 22:41:39, date: 04/08/15
Apr  8 23:41:52 AnotherMass kernel: [    0.200253] NET: Registered protocol family 16
Apr  8 23:41:52 AnotherMass kernel: [    0.200422] cpuidle: using governor ladder
Apr  8 23:41:52 AnotherMass kernel: [    0.200454] cpuidle: using governor menu
Apr  8 23:41:52 AnotherMass kernel: [    0.200491] node 0 link 0: io port [1000, ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200494] TOM: 00000000e0000000 aka 3584M
Apr  8 23:41:52 AnotherMass kernel: [    0.200527] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200530] node 0 link 0: mmio [a0000, bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200533] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200536] node 0 link 0: mmio [f8000000, fe6fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200538] node 0 link 0: mmio [fe700000, fe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200540] node 0 link 0: mmio [fe900000, ffdfffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200541] TOM2: 00000001a0000000 aka 6656M
Apr  8 23:41:52 AnotherMass kernel: [    0.200575] bus: [bus 00-1f] on node 0 link 0
Apr  8 23:41:52 AnotherMass kernel: [    0.200577] bus: 00 [io  0x0000-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200578] bus: 00 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200580] bus: 00 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200581] bus: 00 [mem 0x1a0000000-0xfcffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.201342] ACPI: bus type PCI registered
Apr  8 23:41:52 AnotherMass kernel: [    0.201376] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  8 23:41:52 AnotherMass kernel: [    0.201478] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  8 23:41:52 AnotherMass kernel: [    0.201515] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  8 23:41:52 AnotherMass kernel: [    0.212989] PCI: Using configuration type 1 for base access
Apr  8 23:41:52 AnotherMass kernel: [    0.213202] mtrr: your CPUs had inconsistent variable MTRR settings
Apr  8 23:41:52 AnotherMass kernel: [    0.213237] mtrr: probably your BIOS does not setup all CPUs.
Apr  8 23:41:52 AnotherMass kernel: [    0.213268] mtrr: corrected configuration.
Apr  8 23:41:52 AnotherMass kernel: [    0.214302] bio: create slab <bio-0> at 0
Apr  8 23:41:52 AnotherMass kernel: [    0.214644] ACPI: Added _OSI(Module Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.214680] ACPI: Added _OSI(Processor Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.214712] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  8 23:41:52 AnotherMass kernel: [    0.214744] ACPI: Added _OSI(Processor Aggregator Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.216399] ACPI: Executed 2 blocks of module-level executable AML code
Apr  8 23:41:52 AnotherMass kernel: [    0.218320] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.218952] ACPI: OEMN 00000000d7faaeb0 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.219255] ACPI: Dynamic OEM Table Load:
Apr  8 23:41:52 AnotherMass kernel: [    0.219341] ACPI: OEMN           (null) 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.223007] \_SB_:_OSC evaluation returned wrong type
Apr  8 23:41:52 AnotherMass kernel: [    0.223012] _OSC request data:1 1f 
Apr  8 23:41:52 AnotherMass kernel: [    0.223169] ACPI: Interpreter enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.223212] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223302] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223392] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223489] ACPI: (supports S0 S4 S5)
Apr  8 23:41:52 AnotherMass kernel: [    0.223520] ACPI: Using IOAPIC for interrupt routing
Apr  8 23:41:52 AnotherMass kernel: [    0.223739] HEST: Table parsing has been initialized.
Apr  8 23:41:52 AnotherMass kernel: [    0.223773] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  8 23:41:52 AnotherMass kernel: [    0.223911] ACPI: No dock devices found.
Apr  8 23:41:52 AnotherMass kernel: [    0.228498] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  8 23:41:52 AnotherMass kernel: [    0.228539] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  8 23:41:52 AnotherMass kernel: [    0.228835] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Apr  8 23:41:52 AnotherMass kernel: [    0.229316] acpi PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.229356] acpi PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xfebfffff] ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.229399] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000dffff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff])
Apr  8 23:41:52 AnotherMass kernel: [    0.229658] PCI host bridge to bus 0000:00
Apr  8 23:41:52 AnotherMass kernel: [    0.229691] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229726] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.229762] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229796] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229831] pci_bus 0000:00: root bus resource [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229865] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229908] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.230028] pci 0000:00:01.0: [103c:9602] type 01 class 0x060400
Apr  8 23:41:52 AnotherMass kernel: [    0.230128] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
Apr  8 23:41:52 AnotherMass kernel: [    0.230165] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  8 23:41:52 AnotherMass kernel: [    0.230216] pci 0000:00:06.0: System wakeup disabled by ACPI
Apr  8 23:41:52 AnotherMass kernel: [    0.230303] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Apr  8 23:41:52 AnotherMass kernel: [    0.230324] pci 0000:00:11.0: reg 0x10: [io  0xd000-0xd007]
Apr  8 23:41:52 AnotherMass kernel: [    0.230334] pci 0000:00:11.0: reg 0x14: [io  0xc000-0xc003]
Apr  8 23:41:52 AnotherMass kernel: [    0.230344] pci 0000:00:11.0: reg 0x18: [io  0xb000-0xb007]
Apr  8 23:41:52 AnotherMass kernel: [    0.230353] pci 0000:00:11.0: reg 0x1c: [io  0xa000-0xa003]
Apr  8 23:41:52 AnotherMass kernel: [    0.230362] pci 0000:00:11.0: reg 0x20: [io  0x9000-0x900f]
Apr  8 23:41:52 AnotherMass kernel: [    0.230372] pci 0000:00:11.0: reg 0x24: [mem 0xfe6ffc00-0xfe6fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230493] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.230507] pci 0000:00:12.0: reg 0x10: [mem 0xfe6fe000-0xfe6fefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230631] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.230650] pci 0000:00:12.2: reg 0x10: [mem 0xfe6ff800-0xfe6ff8ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230728] pci 0000:00:12.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.230730] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.230811] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.230828] pci 0000:00:13.0: reg 0x10: [mem 0xfe6fd000-0xfe6fdfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230952] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.230970] pci 0000:00:13.2: reg 0x10: [mem 0xfe6ff400-0xfe6ff4ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231049] pci 0000:00:13.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.231050] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.231133] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Apr  8 23:41:52 AnotherMass kernel: [    0.231259] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Apr  8 23:41:52 AnotherMass kernel: [    0.231386] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Apr  8 23:41:52 AnotherMass kernel: [    0.231461] pci 0000:00:14.4: System wakeup disabled by ACPI
Apr  8 23:41:52 AnotherMass kernel: [    0.231525] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.231539] pci 0000:00:16.0: reg 0x10: [mem 0xfe6fc000-0xfe6fcfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231662] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.231680] pci 0000:00:16.2: reg 0x10: [mem 0xfe6ff000-0xfe6ff0ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231760] pci 0000:00:16.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.231761] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.231840] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.231912] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.231980] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232047] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232117] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232238] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
Apr  8 23:41:52 AnotherMass kernel: [    0.232247] pci 0000:01:05.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.232252] pci 0000:01:05.0: reg 0x14: [io  0xe000-0xe0ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232257] pci 0000:01:05.0: reg 0x18: [mem 0xfe8f0000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232268] pci 0000:01:05.0: reg 0x24: [mem 0xfe700000-0xfe7fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232287] pci 0000:01:05.0: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.232348] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  8 23:41:52 AnotherMass kernel: [    0.232382] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232385] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232389] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.232451] pci 0000:02:00.0: [14e4:165b] type 00 class 0x020000
Apr  8 23:41:52 AnotherMass kernel: [    0.232470] pci 0000:02:00.0: reg 0x10: [mem 0xfe9f0000-0xfe9fffff 64bit]
Apr  8 23:41:52 AnotherMass kernel: [    0.232574] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  8 23:41:52 AnotherMass kernel: [    0.238882] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  8 23:41:52 AnotherMass kernel: [    0.238925] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.239024] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239064] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239066] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239069] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239071] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239073] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239423] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.239761] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240096] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240430] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240750] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241059] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241368] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241677] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.242076] ACPI: Enabled 4 GPEs in block 00 to 1F
Apr  8 23:41:52 AnotherMass kernel: [    0.242170] ACPI: \_SB_.PCI0: notify handler is installed
Apr  8 23:41:52 AnotherMass kernel: [    0.242204] Found 1 acpi root devices
Apr  8 23:41:52 AnotherMass kernel: [    0.242378] vgaarb: setting as boot device: PCI:0000:01:05.0
Apr  8 23:41:52 AnotherMass kernel: [    0.242411] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Apr  8 23:41:52 AnotherMass kernel: [    0.242446] vgaarb: loaded
Apr  8 23:41:52 AnotherMass kernel: [    0.242477] vgaarb: bridge control possible 0000:01:05.0
Apr  8 23:41:52 AnotherMass kernel: [    0.242704] SCSI subsystem initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.242827] libata version 3.00 loaded.
Apr  8 23:41:52 AnotherMass kernel: [    0.242851] ACPI: bus type USB registered
Apr  8 23:41:52 AnotherMass kernel: [    0.242903] usbcore: registered new interface driver usbfs
Apr  8 23:41:52 AnotherMass kernel: [    0.242942] usbcore: registered new interface driver hub
Apr  8 23:41:52 AnotherMass kernel: [    0.243091] usbcore: registered new device driver usb
Apr  8 23:41:52 AnotherMass kernel: [    0.243333] PCI: Using ACPI for IRQ routing
Apr  8 23:41:52 AnotherMass kernel: [    0.251507] PCI: pci_cache_line_size set to 64 bytes
Apr  8 23:41:52 AnotherMass kernel: [    0.251553] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.251556] e820: reserve RAM buffer [mem 0xd7f90000-0xd7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.251665] NetLabel: Initializing
Apr  8 23:41:52 AnotherMass kernel: [    0.251696] NetLabel:  domain hash size = 128
Apr  8 23:41:52 AnotherMass kernel: [    0.251727] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  8 23:41:52 AnotherMass kernel: [    0.251771] NetLabel:  unlabeled traffic allowed by default
Apr  8 23:41:52 AnotherMass kernel: [    0.251922] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  8 23:41:52 AnotherMass kernel: [    0.252062] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr  8 23:41:52 AnotherMass kernel: [    0.254151] Switched to clocksource hpet
Apr  8 23:41:52 AnotherMass kernel: [    0.260344] AppArmor: AppArmor Filesystem Enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.260417] pnp: PnP ACPI init
Apr  8 23:41:52 AnotherMass kernel: [    0.260465] ACPI: bus type PNP registered
Apr  8 23:41:52 AnotherMass kernel: [    0.260713] system 00:00: [mem 0xd8000000-0xdfffffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.260748] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260808] pnp 00:01: [dma 4]
Apr  8 23:41:52 AnotherMass kernel: [    0.260833] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260872] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260931] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260961] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261002] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261096] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261130] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261163] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261340] system 00:07: [io  0x04d0-0x04d1] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261373] system 00:07: [io  0x040b] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261405] system 00:07: [io  0x04d6] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261437] system 00:07: [io  0x0c00-0x0c01] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261470] system 00:07: [io  0x0c14] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261502] system 00:07: [io  0x0c50-0x0c51] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261534] system 00:07: [io  0x0c52] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261566] system 00:07: [io  0x0c6c] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261598] system 00:07: [io  0x0c6f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261630] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261662] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261695] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261727] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261759] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261792] system 00:07: [io  0x0800-0x089f] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261824] system 00:07: [io  0x0b00-0x0b1f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261857] system 00:07: [io  0x0b20-0x0b3f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261889] system 00:07: [io  0x0900-0x090f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261922] system 00:07: [io  0x0910-0x091f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261955] system 00:07: [io  0xfe00-0xfefe] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261988] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262020] system 00:07: [mem 0xfec10000-0xfec1001f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262053] system 00:07: [mem 0xfed80000-0xfed80fff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262087] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262167] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262201] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262321] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262355] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262388] system 00:09: [mem 0x00100000-0xd7ffffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262421] system 00:09: [mem 0xfec00000-0xffffffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262454] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262546] pnp: PnP ACPI: found 10 devices
Apr  8 23:41:52 AnotherMass kernel: [    0.262577] ACPI: bus type PNP unregistered
Apr  8 23:41:52 AnotherMass kernel: [    0.270959] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  8 23:41:52 AnotherMass kernel: [    0.270995] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271030] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271065] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.271108] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  8 23:41:52 AnotherMass kernel: [    0.271141] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271179] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  8 23:41:52 AnotherMass kernel: [    0.271223] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.271226] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271228] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271230] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271232] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271234] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271236] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271239] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.271241] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271244] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.271246] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271248] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271250] pci_bus 0000:03: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271252] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271294] NET: Registered protocol family 2
Apr  8 23:41:52 AnotherMass kernel: [    0.271605] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.271973] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.272518] TCP: Hash tables configured (established 65536 bind 65536)
Apr  8 23:41:52 AnotherMass kernel: [    0.272644] TCP: reno registered
Apr  8 23:41:52 AnotherMass kernel: [    0.272689] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.272814] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.273041] NET: Registered protocol family 1
Apr  8 23:41:52 AnotherMass kernel: [    0.273089] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Apr  8 23:41:52 AnotherMass kernel: [    1.250125] pci 0000:01:05.0: Video device with shadowed ROM
Apr  8 23:41:52 AnotherMass kernel: [    1.250134] PCI: CLS 64 bytes, default 64
Apr  8 23:41:52 AnotherMass kernel: [    1.250205] Trying to unpack rootfs image as initramfs...
Apr  8 23:41:52 AnotherMass kernel: [    1.625545] Freeing initrd memory: 19268K (ffff880035a4e000 - ffff880036d1f000)
Apr  8 23:41:52 AnotherMass kernel: [    1.625806] PCI-DMA: Disabling AGP.
Apr  8 23:41:52 AnotherMass kernel: [    1.625950] PCI-DMA: aperture base @ cc000000 size 65536 KB
Apr  8 23:41:52 AnotherMass kernel: [    1.625982] PCI-DMA: using GART IOMMU.
Apr  8 23:41:52 AnotherMass kernel: [    1.626015] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr  8 23:41:52 AnotherMass kernel: [    1.630263] LVT offset 1 assigned for vector 0x400
Apr  8 23:41:52 AnotherMass kernel: [    1.630310] IBS: LVT offset 1 assigned
Apr  8 23:41:52 AnotherMass kernel: [    1.630378] perf: AMD IBS detected (0x0000001f)
Apr  8 23:41:52 AnotherMass kernel: [    1.630474] microcode: CPU0: patch_level=0x010000c8
Apr  8 23:41:52 AnotherMass kernel: [    1.630515] microcode: CPU1: patch_level=0x010000c8
Apr  8 23:41:52 AnotherMass kernel: [    1.630641] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  8 23:41:52 AnotherMass kernel: [    1.630676] Scanning for low memory corruption every 60 seconds
Apr  8 23:41:52 AnotherMass kernel: [    1.631023] Initialise system trusted keyring
Apr  8 23:41:52 AnotherMass kernel: [    1.631109] audit: initializing netlink socket (disabled)
Apr  8 23:41:52 AnotherMass kernel: [    1.631154] type=2000 audit(1428532900.524:1): initialized
Apr  8 23:41:52 AnotherMass kernel: [    1.664697] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  8 23:41:52 AnotherMass kernel: [    1.666415] zbud: loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.666752] VFS: Disk quotas dquot_6.5.2
Apr  8 23:41:52 AnotherMass kernel: [    1.666846] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    1.667529] fuse init (API version 7.22)
Apr  8 23:41:52 AnotherMass kernel: [    1.667764] msgmni has been set to 11680
Apr  8 23:41:52 AnotherMass kernel: [    1.667873] Key type big_key registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668492] Key type asymmetric registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668529] Asymmetric key parser 'x509' registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668644] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Apr  8 23:41:52 AnotherMass kernel: [    1.668731] io scheduler noop registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668765] io scheduler deadline registered (default)
Apr  8 23:41:52 AnotherMass kernel: [    1.668823] io scheduler cfq registered
Apr  8 23:41:52 AnotherMass kernel: [    1.669674] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    1.669752] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
Apr  8 23:41:52 AnotherMass kernel: [    1.669790] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Apr  8 23:41:52 AnotherMass kernel: [    1.669823] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.669835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  8 23:41:52 AnotherMass kernel: [    1.669879] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  8 23:41:52 AnotherMass kernel: [    1.669960] ipmi message handler version 39.2
Apr  8 23:41:52 AnotherMass kernel: [    1.670065] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr  8 23:41:52 AnotherMass kernel: [    1.670107] ACPI: Power Button [PWRB]
Apr  8 23:41:52 AnotherMass kernel: [    1.670174] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  8 23:41:52 AnotherMass kernel: [    1.670210] ACPI: Power Button [PWRF]
Apr  8 23:41:52 AnotherMass kernel: [    1.670313] ACPI: processor limited to max C-state 1
Apr  8 23:41:52 AnotherMass kernel: [    1.670575] ERST: Failed to get Error Log Address Range.
Apr  8 23:41:52 AnotherMass kernel: [    1.685666] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
Apr  8 23:41:52 AnotherMass kernel: [    1.685802] GHES: APEI firmware first mode is enabled by WHEA _OSC.
Apr  8 23:41:52 AnotherMass kernel: [    1.686033] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  8 23:41:52 AnotherMass kernel: [    1.688048] Linux agpgart interface v0.103
Apr  8 23:41:52 AnotherMass kernel: [    1.689945] brd: module loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.691303] loop: module loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.691737] libphy: Fixed MDIO Bus: probed
Apr  8 23:41:52 AnotherMass kernel: [    1.691861] tun: Universal TUN/TAP device driver, 1.6
Apr  8 23:41:52 AnotherMass kernel: [    1.691896] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  8 23:41:52 AnotherMass kernel: [    1.692095] PPP generic driver version 2.4.2
Apr  8 23:41:52 AnotherMass kernel: [    1.692221] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  8 23:41:52 AnotherMass kernel: [    1.692262] ehci-pci: EHCI PCI platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.692448] QUIRK: Enable AMD PLL fix
Apr  8 23:41:52 AnotherMass kernel: [    1.692471] ehci-pci 0000:00:12.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.692507] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr  8 23:41:52 AnotherMass kernel: [    1.692545] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.692589] ehci-pci 0000:00:12.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.692666] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe6ff800
Apr  8 23:41:52 AnotherMass kernel: [    1.701543] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.701665] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.701699] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.701733] usb usb1: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.701765] usb usb1: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.701797] usb usb1: SerialNumber: 0000:00:12.2
Apr  8 23:41:52 AnotherMass kernel: [    1.702000] hub 1-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.702037] hub 1-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.702348] ehci-pci 0000:00:13.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.702385] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr  8 23:41:52 AnotherMass kernel: [    1.702421] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.702466] ehci-pci 0000:00:13.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.702529] ehci-pci 0000:00:13.2: irq 17, io mem 0xfe6ff400
Apr  8 23:41:52 AnotherMass kernel: [    1.713542] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.713648] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.713682] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.713719] usb usb2: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.713753] usb usb2: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.713786] usb usb2: SerialNumber: 0000:00:13.2
Apr  8 23:41:52 AnotherMass kernel: [    1.714011] hub 2-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.714050] hub 2-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.714381] ehci-pci 0000:00:16.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.714419] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr  8 23:41:52 AnotherMass kernel: [    1.714460] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.714509] ehci-pci 0000:00:16.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.714579] ehci-pci 0000:00:16.2: irq 17, io mem 0xfe6ff000
Apr  8 23:41:52 AnotherMass kernel: [    1.725526] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.725617] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.725650] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.725685] usb usb3: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.725716] usb usb3: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.725748] usb usb3: SerialNumber: 0000:00:16.2
Apr  8 23:41:52 AnotherMass kernel: [    1.725949] hub 3-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.725985] hub 3-0:1.0: 4 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.726129] ehci-platform: EHCI generic platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726204] ohci-pci: OHCI PCI platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726395] ohci-pci 0000:00:12.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.726432] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr  8 23:41:52 AnotherMass kernel: [    1.726492] ohci-pci 0000:00:12.0: irq 18, io mem 0xfe6fe000
Apr  8 23:41:52 AnotherMass kernel: [    1.785534] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.785572] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.785606] usb usb4: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.785639] usb usb4: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.785670] usb usb4: SerialNumber: 0000:00:12.0
Apr  8 23:41:52 AnotherMass kernel: [    1.785874] hub 4-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.785913] hub 4-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.786200] ohci-pci 0000:00:13.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.786237] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr  8 23:41:52 AnotherMass kernel: [    1.786286] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe6fd000
Apr  8 23:41:52 AnotherMass kernel: [    1.845506] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.845544] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.845579] usb usb5: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.845610] usb usb5: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.845642] usb usb5: SerialNumber: 0000:00:13.0
Apr  8 23:41:52 AnotherMass kernel: [    1.845845] hub 5-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.845885] hub 5-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.846166] ohci-pci 0000:00:16.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.846204] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 6
Apr  8 23:41:52 AnotherMass kernel: [    1.846254] ohci-pci 0000:00:16.0: irq 18, io mem 0xfe6fc000
Apr  8 23:41:52 AnotherMass kernel: [    1.905484] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.905523] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.905558] usb usb6: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.905590] usb usb6: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.905622] usb usb6: SerialNumber: 0000:00:16.0
Apr  8 23:41:52 AnotherMass kernel: [    1.905839] hub 6-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.905881] hub 6-0:1.0: 4 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.906018] ohci-platform: OHCI generic platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.906061] uhci_hcd: USB Universal Host Controller Interface driver
Apr  8 23:41:52 AnotherMass kernel: [    1.906154] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr  8 23:41:52 AnotherMass kernel: [    2.629042] tsc: Refined TSC clocksource calibration: 2196.341 MHz
Apr  8 23:41:52 AnotherMass kernel: [    2.927855] i8042: No controller found
Apr  8 23:41:52 AnotherMass kernel: [    2.928142] mousedev: PS/2 mouse device common for all mice
Apr  8 23:41:52 AnotherMass kernel: [    2.928359] rtc_cmos 00:02: RTC can wake from S4
Apr  8 23:41:52 AnotherMass kernel: [    2.928547] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Apr  8 23:41:52 AnotherMass kernel: [    2.928607] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  8 23:41:52 AnotherMass kernel: [    2.928723] device-mapper: uevent: version 1.0.3
Apr  8 23:41:52 AnotherMass kernel: [    2.928895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Apr  8 23:41:52 AnotherMass kernel: [    2.928953] ledtrig-cpu: registered to indicate activity on CPUs
Apr  8 23:41:52 AnotherMass kernel: [    2.929109] TCP: cubic registered
Apr  8 23:41:52 AnotherMass kernel: [    2.929247] NET: Registered protocol family 10
Apr  8 23:41:52 AnotherMass kernel: [    2.929469] NET: Registered protocol family 17
Apr  8 23:41:52 AnotherMass kernel: [    2.929513] Key type dns_resolver registered
Apr  8 23:41:52 AnotherMass kernel: [    2.929868] Loading compiled-in X.509 certificates
Apr  8 23:41:52 AnotherMass kernel: [    2.931146] Loaded X.509 cert 'Magrathea: Glacier signing key: 4eb2de249917cbf39cb85692e54cebade594d680'
Apr  8 23:41:52 AnotherMass kernel: [    2.931228] registered taskstats version 1
Apr  8 23:41:52 AnotherMass kernel: [    2.933921] Key type trusted registered
Apr  8 23:41:52 AnotherMass kernel: [    2.938733] Key type encrypted registered
Apr  8 23:41:52 AnotherMass kernel: [    2.938776] AppArmor: AppArmor sha1 policy hashing enabled
Apr  8 23:41:52 AnotherMass kernel: [    2.938814] IMA: No TPM chip found, activating TPM-bypass!
Apr  8 23:41:52 AnotherMass kernel: [    2.939346] regulator-dummy: disabling
Apr  8 23:41:52 AnotherMass kernel: [    2.939444]   Magic number: 11:56:704
Apr  8 23:41:52 AnotherMass kernel: [    2.939534] event_source cpu: hash matches
Apr  8 23:41:52 AnotherMass kernel: [    2.939611]  cpu: hash matches
Apr  8 23:41:52 AnotherMass kernel: [    2.939684] rtc_cmos 00:02: setting system clock to 2015-04-08 22:41:42 UTC (1428532902)
Apr  8 23:41:52 AnotherMass kernel: [    2.939911] acpi-cpufreq: overriding BIOS provided _PSD data
Apr  8 23:41:52 AnotherMass kernel: [    2.940025] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  8 23:41:52 AnotherMass kernel: [    2.940057] EDD information not available.
Apr  8 23:41:52 AnotherMass kernel: [    2.940122] PM: Hibernation image not present or could not be loaded.
Apr  8 23:41:52 AnotherMass kernel: [    2.941950] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Apr  8 23:41:52 AnotherMass kernel: [    2.942029] Write protecting the kernel read-only data: 12288k
Apr  8 23:41:52 AnotherMass kernel: [    2.944793] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
Apr  8 23:41:52 AnotherMass kernel: [    2.947148] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
Apr  8 23:41:52 AnotherMass kernel: [    2.987058] pps_core: LinuxPPS API ver. 1 registered
Apr  8 23:41:52 AnotherMass kernel: [    2.987104] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Apr  8 23:41:52 AnotherMass kernel: [    2.988719] PTP clock support registered
Apr  8 23:41:52 AnotherMass kernel: [    2.995380] md: linear personality registered for level -1
Apr  8 23:41:52 AnotherMass kernel: [    2.996298] ahci 0000:00:11.0: version 3.0
Apr  8 23:41:52 AnotherMass kernel: [    2.996506] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    2.996617] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Apr  8 23:41:52 AnotherMass kernel: [    2.996657] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
Apr  8 23:41:52 AnotherMass kernel: [    2.997876] scsi0 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998000] scsi1 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998093] scsi2 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998185] scsi3 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998747] scsi4 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998837] scsi5 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998984] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999027] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999068] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999108] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999709] ata5: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999746] ata6: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    3.002621] md: multipath personality registered for level -4
Apr  8 23:41:52 AnotherMass kernel: [    3.008105] md: raid0 personality registered for level 0
Apr  8 23:41:52 AnotherMass kernel: [    3.008906] tg3.c:v3.134 (Sep 16, 2013)
Apr  8 23:41:52 AnotherMass kernel: [    3.013095] md: raid1 personality registered for level 1
Apr  8 23:41:52 AnotherMass kernel: [    3.084822] raid6: sse2x1    3072 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.152785] raid6: sse2x2    4612 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.220743] raid6: sse2x4    5533 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.220777] raid6: using algorithm sse2x4 (5533 MB/s)
Apr  8 23:41:52 AnotherMass kernel: [    3.220812] raid6: using intx1 recovery algorithm
Apr  8 23:41:52 AnotherMass kernel: [    3.222668] xor: measuring software checksum speed
Apr  8 23:41:52 AnotherMass kernel: [    3.260713]    prefetch64-sse:  8984.000 MB/sec
Apr  8 23:41:52 AnotherMass kernel: [    3.300693]    generic_sse:  8418.000 MB/sec
Apr  8 23:41:52 AnotherMass kernel: [    3.300727] xor: using function: prefetch64-sse (8984.000 MB/sec)
Apr  8 23:41:52 AnotherMass kernel: [    3.302372] async_tx: api initialized (async)
Apr  8 23:41:52 AnotherMass kernel: [    3.311135] md: raid6 personality registered for level 6
Apr  8 23:41:52 AnotherMass kernel: [    3.311170] md: raid5 personality registered for level 5
Apr  8 23:41:52 AnotherMass kernel: [    3.311202] md: raid4 personality registered for level 4
Apr  8 23:41:52 AnotherMass kernel: [    3.319858] md: raid10 personality registered for level 10
Apr  8 23:41:52 AnotherMass kernel: [    3.328772] ata5: SATA link down (SStatus 0 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.357838] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 38:ea:a7:a3:2a:32
Apr  8 23:41:52 AnotherMass kernel: [    3.357887] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Apr  8 23:41:52 AnotherMass kernel: [    3.357925] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  8 23:41:52 AnotherMass kernel: [    3.357960] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  8 23:41:52 AnotherMass kernel: [    3.360759] usb 4-2: new low-speed USB device number 2 using ohci-pci
Apr  8 23:41:52 AnotherMass kernel: [    3.496677] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.497320] ata1.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.497359] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.498021] ata1.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.498383] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.498739] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.498777] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.498840] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.499005] sd 0:0:0:0: [sda] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.499054] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.499099] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.504672] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.504738] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.504807] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.505208] ata6.00: ATA-9: SanDisk SDSSDRC032G, 3.0.0, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505254] ata6.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr  8 23:41:52 AnotherMass kernel: [    3.505356] ata3.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505397] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.505497] ata4.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505535] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.506011] ata3.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.506192] ata6.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.506249] ata4.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.508656] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.509268] ata2.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.509306] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.509938] ata2.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.510232] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.510479] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.510515] sd 1:0:0:0: [sdb] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.510575] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.510703] sd 1:0:0:0: [sdb] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.510742] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.510765] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.510776] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.510905] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.510941] sd 2:0:0:0: [sdc] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.511001] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.511084] sd 2:0:0:0: [sdc] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.511124] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.511145] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.511431] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.511591] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.511608] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.511659] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.511775] scsi 5:0:0:0: Direct-Access     ATA      SanDisk SDSSDRC0 3.0. PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.511924] sd 5:0:0:0: [sde] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.511970] sd 3:0:0:0: [sdd] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.512006] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.512029] sd 3:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.512050] sd 5:0:0:0: [sde] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.512052] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.512073] sd 5:0:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.512176] sd 5:0:0:0: Attached scsi generic sg4 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.513222]  sde: sde1 sde2 < sde5 >
Apr  8 23:41:52 AnotherMass kernel: [    3.513909] sd 5:0:0:0: [sde] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.524620] usb 4-2: New USB device found, idVendor=04f3, idProduct=0103
Apr  8 23:41:52 AnotherMass kernel: [    3.524664] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  8 23:41:52 AnotherMass kernel: [    3.531479] hidraw: raw HID events driver (C) Jiri Kosina
Apr  8 23:41:52 AnotherMass kernel: [    3.544838] usbcore: registered new interface driver usbhid
Apr  8 23:41:52 AnotherMass kernel: [    3.544877] usbhid: USB HID core driver
Apr  8 23:41:52 AnotherMass kernel: [    3.547072] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input2
Apr  8 23:41:52 AnotherMass kernel: [    3.547208] hid-generic 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:12.0-2/input0
Apr  8 23:41:52 AnotherMass kernel: [    3.550768] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input3
Apr  8 23:41:52 AnotherMass kernel: [    3.550908] hid-generic 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:12.0-2/input1
Apr  8 23:41:52 AnotherMass kernel: [    3.565040]  sda: sda1
Apr  8 23:41:52 AnotherMass kernel: [    3.565520] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.583160]  sdb: sdb1
Apr  8 23:41:52 AnotherMass kernel: [    3.583561] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.589338]  sdd: sdd1
Apr  8 23:41:52 AnotherMass kernel: [    3.589743] sd 3:0:0:0: [sdd] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.628689] Switched to clocksource tsc
Apr  8 23:41:52 AnotherMass kernel: [    4.125996]  sdc: sdc1
Apr  8 23:41:52 AnotherMass kernel: [    4.126825] sd 2:0:0:0: [sdc] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    4.198003] random: nonblocking pool is initialized
Apr  8 23:41:52 AnotherMass kernel: [    4.201351] md: bind<sdd1>
Apr  8 23:41:52 AnotherMass kernel: [    4.203508] md: bind<sda1>
Apr  8 23:41:52 AnotherMass kernel: [    4.205769] md: bind<sdb1>
Apr  8 23:41:52 AnotherMass kernel: [    4.212392] EXT4-fs (sde1): INFO: recovery required on readonly filesystem
Apr  8 23:41:52 AnotherMass kernel: [    4.212440] EXT4-fs (sde1): write access will be enabled during recovery
Apr  8 23:41:52 AnotherMass kernel: [    4.221732] md: bind<sdc1>
Apr  8 23:41:52 AnotherMass kernel: [    4.379378] EXT4-fs (sde1): recovery complete
Apr  8 23:41:52 AnotherMass kernel: [    4.380855] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Apr  8 23:41:52 AnotherMass kernel: [    4.927269] Adding 6157308k swap on /dev/sde5.  Priority:-1 extents:1 across:6157308k SSFS
Apr  8 23:41:52 AnotherMass kernel: [    4.976940] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
Apr  8 23:41:52 AnotherMass kernel: [    6.081717] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 23:41:52 AnotherMass kernel: [    6.261744] lp: driver loaded but no devices found
Apr  8 23:41:52 AnotherMass kernel: [    6.286540] ppdev: user-space parallel port driver
Apr  8 23:41:52 AnotherMass kernel: [    6.302772] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  8 23:41:52 AnotherMass kernel: [    6.381174] [drm] Initialized drm 1.1.0 20060810
Apr  8 23:41:52 AnotherMass kernel: [    6.402747] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr  8 23:41:52 AnotherMass kernel: [    6.402816] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
Apr  8 23:41:52 AnotherMass kernel: [    6.409855] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Apr  8 23:41:52 AnotherMass kernel: [    6.409940] sp5100_tco: PCI Revision ID: 0x42
Apr  8 23:41:52 AnotherMass kernel: [    6.409983] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
Apr  8 23:41:52 AnotherMass kernel: [    6.409995] sp5100_tco: Last reboot was not triggered by watchdog.
Apr  8 23:41:52 AnotherMass kernel: [    6.410108] sp5100_tco: initialized (0xffffc90000c7ab00). heartbeat=60 sec (nowayout=0)
Apr  8 23:41:52 AnotherMass kernel: [    6.412412] type=1400 audit(1428532905.972:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412421] type=1400 audit(1428532905.972:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412427] type=1400 audit(1428532905.972:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412993] type=1400 audit(1428532905.972:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412999] type=1400 audit(1428532905.972:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.413314] type=1400 audit(1428532905.972:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.417952] MCE: In-kernel MCE decoding enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.445213] EDAC MC: Ver: 3.0.0
Apr  8 23:41:52 AnotherMass kernel: [    6.457119] AMD64 EDAC driver v3.4.0
Apr  8 23:41:52 AnotherMass kernel: [    6.457158] EDAC amd64: DRAM ECC enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.457164] EDAC amd64: F10h detected (node 0).
Apr  8 23:41:52 AnotherMass kernel: [    6.457179] EDAC MC: DCT0 chip selects:
Apr  8 23:41:52 AnotherMass kernel: [    6.457181] EDAC amd64: MC: 0:  1024MB 1:  1024MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457183] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457184] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457186] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457187] EDAC MC: DCT1 chip selects:
Apr  8 23:41:52 AnotherMass kernel: [    6.457189] EDAC amd64: MC: 0:  2048MB 1:  2048MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457190] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457191] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457193] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457194] EDAC amd64: using x4 syndromes.
Apr  8 23:41:52 AnotherMass kernel: [    6.457195] EDAC amd64: MCT channel count: 2
Apr  8 23:41:52 AnotherMass kernel: [    6.457218] EDAC amd64: CS0: Unbuffered DDR3 RAM
Apr  8 23:41:52 AnotherMass kernel: [    6.457219] EDAC amd64: CS1: Unbuffered DDR3 RAM
Apr  8 23:41:52 AnotherMass kernel: [    6.461574] EDAC MC0: Giving out device to module amd64_edac controller F10h: DEV 0000:00:18.2 (INTERRUPT)
Apr  8 23:41:52 AnotherMass kernel: [    6.461632] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
Apr  8 23:41:52 AnotherMass kernel: [    6.555086] kvm: Nested Virtualization enabled
Apr  8 23:41:52 AnotherMass kernel: [    6.555093] kvm: Nested Paging enabled
Apr  8 23:41:52 AnotherMass kernel: [    6.566152] [drm] radeon kernel modesetting enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.566389] tg3 0000:02:00.0: irq 42 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    6.707053] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
Apr  8 23:41:52 AnotherMass kernel: [    6.707072] [drm] register mmio base: 0xFE8F0000
Apr  8 23:41:52 AnotherMass kernel: [    6.707074] [drm] register mmio size: 65536
Apr  8 23:41:52 AnotherMass kernel: [    6.707777] ATOM BIOS: AMD_1407_150
Apr  8 23:41:52 AnotherMass kernel: [    6.707844] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
Apr  8 23:41:52 AnotherMass kernel: [    6.707847] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Apr  8 23:41:52 AnotherMass kernel: [    6.707893] [drm] Detected VRAM RAM=128M, BAR=128M
Apr  8 23:41:52 AnotherMass kernel: [    6.707895] [drm] RAM width 32bits DDR
Apr  8 23:41:52 AnotherMass kernel: [    6.707967] [TTM] Zone  kernel: Available graphics memory: 2991704 kiB
Apr  8 23:41:52 AnotherMass kernel: [    6.707969] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Apr  8 23:41:52 AnotherMass kernel: [    6.707970] [TTM] Initializing pool allocator
Apr  8 23:41:52 AnotherMass kernel: [    6.707976] [TTM] Initializing DMA pool allocator
Apr  8 23:41:52 AnotherMass kernel: [    6.707994] [drm] radeon: 128M of VRAM memory ready
Apr  8 23:41:52 AnotherMass kernel: [    6.707996] [drm] radeon: 512M of GTT memory ready.
Apr  8 23:41:52 AnotherMass kernel: [    6.708004] [drm] Loading RS780 Microcode
Apr  8 23:41:52 AnotherMass kernel: [    7.341172] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 23:41:52 AnotherMass kernel: [    7.429443] [drm] GART: num cpu pages 131072, num gpu pages 131072
Apr  8 23:41:52 AnotherMass kernel: [    7.524270] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Apr  8 23:41:52 AnotherMass kernel: [    7.524357] radeon 0000:01:05.0: WB enabled
Apr  8 23:41:52 AnotherMass kernel: [    7.524361] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff8800d6763c00
Apr  8 23:41:52 AnotherMass kernel: [    7.524364] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff8800d6763c0c
Apr  8 23:41:52 AnotherMass kernel: [    7.524367] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  8 23:41:52 AnotherMass kernel: [    7.524368] [drm] Driver supports precise vblank timestamp query.
Apr  8 23:41:52 AnotherMass kernel: [    7.524370] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
Apr  8 23:41:52 AnotherMass kernel: [    7.524389] [drm] radeon: irq initialized.
Apr  8 23:41:52 AnotherMass kernel: [    7.563940] [drm] ring test on 0 succeeded in 1 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.563952] [drm] ring test on 3 succeeded in 2 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564097] [drm] Enabling audio 0 support
Apr  8 23:41:52 AnotherMass kernel: [    7.564118] [drm] ib test on ring 0 succeeded in 0 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564132] [drm] ib test on ring 3 succeeded in 0 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564349] [drm] Radeon Display Connectors
Apr  8 23:41:52 AnotherMass kernel: [    7.564351] [drm] Connector 0:
Apr  8 23:41:52 AnotherMass kernel: [    7.564352] [drm]   VGA-1
Apr  8 23:41:52 AnotherMass kernel: [    7.564354] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Apr  8 23:41:52 AnotherMass kernel: [    7.564355] [drm]   Encoders:
Apr  8 23:41:52 AnotherMass kernel: [    7.564357] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Apr  8 23:41:52 AnotherMass kernel: [    7.564376] [drm] radeon: power management initialized
Apr  8 23:41:52 AnotherMass kernel: [    7.614107] [drm] fb mappable at 0xF0141000
Apr  8 23:41:52 AnotherMass kernel: [    7.614112] [drm] vram apper at 0xF0000000
Apr  8 23:41:52 AnotherMass kernel: [    7.614114] [drm] size 5324800
Apr  8 23:41:52 AnotherMass kernel: [    7.614115] [drm] fb depth is 24
Apr  8 23:41:52 AnotherMass kernel: [    7.614117] [drm]    pitch is 5888
Apr  8 23:41:52 AnotherMass kernel: [    7.614197] fbcon: radeondrmfb (fb0) is primary device
Apr  8 23:41:52 AnotherMass kernel: [    7.644860] Console: switching to colour frame buffer device 180x56
Apr  8 23:41:52 AnotherMass kernel: [    7.658769] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
Apr  8 23:41:52 AnotherMass kernel: [    7.658772] radeon 0000:01:05.0: registered panic notifier
Apr  8 23:41:52 AnotherMass kernel: [    7.658788] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0
Apr  8 23:41:52 AnotherMass kernel: [    9.904798] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
Apr  8 23:41:52 AnotherMass kernel: [    9.904803] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
Apr  8 23:41:52 AnotherMass kernel: [    9.904825] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  8 23:41:52 AnotherMass kernel: [   12.773555] Bluetooth: Core ver 2.17
Apr  8 23:41:52 AnotherMass kernel: [   12.773584] NET: Registered protocol family 31
Apr  8 23:41:52 AnotherMass kernel: [   12.773586] Bluetooth: HCI device and connection manager initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773599] Bluetooth: HCI socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773602] Bluetooth: L2CAP socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773607] Bluetooth: SCO socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793804] Bluetooth: RFCOMM TTY layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793821] Bluetooth: RFCOMM socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793829] Bluetooth: RFCOMM ver 1.11
Apr  8 23:41:52 AnotherMass kernel: [   12.795083] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  8 23:41:52 AnotherMass kernel: [   12.795088] Bluetooth: BNEP filters: protocol multicast
Apr  8 23:41:52 AnotherMass kernel: [   12.795100] Bluetooth: BNEP socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.828129] type=1400 audit(1428532912.392:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=864 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [   12.828140] type=1400 audit(1428532912.392:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [   12.828691] type=1400 audit(1428532912.392:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.114632] type=1400 audit(1428532917.680:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.114643] type=1400 audit(1428532917.680:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.114649] type=1400 audit(1428532917.680:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115213] type=1400 audit(1428532917.680:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115218] type=1400 audit(1428532917.680:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115537] type=1400 audit(1428532917.680:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134026] type=1400 audit(1428532917.700:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134036] type=1400 audit(1428532917.700:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134393] type=1400 audit(1428532917.700:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.171058] type=1400 audit(1428532917.736:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=1116 comm="apparmor_parser"
Apr  8 23:42:57 AnotherMass kernel: [   42.940594] audit_printk_skb: 123 callbacks suppressed
Apr  8 23:42:57 AnotherMass kernel: [   42.940599] type=1400 audit(1428532977.430:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2764 comm="apparmor_parser"
Apr  8 23:42:57 AnotherMass kernel: [   42.940608] type=1400 audit(1428532977.430:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2764 comm="apparmor_parser"
Apr  8 23:42:57 AnotherMass kernel: [   42.941215] type=1400 audit(1428532977.434:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2764 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Linux version 3.13.0-48-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 (Ubuntu 3.13.0-48.80-generic 3.13.11-ckt16)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] KERNEL supported cpus:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Intel GenuineIntel
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   AMD AuthenticAMD
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Centaur CentaurHauls
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d7f8ffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7f9e000-0x00000000d7f9ffff] type 9
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fa0000-0x00000000d7fadfff] ACPI data
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fae000-0x00000000d7fdffff] ACPI NVS
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fe0000-0x00000000d7ffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000019fffffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] SMBIOS 2.6 present.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR default type: uncachable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   00000-9FFFF write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   A0000-EFFFF uncachable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR variable ranges enabled:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   3 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   4 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   5 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   6 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   7 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] TOM2: 00000001a0000000 aka 6656M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Using GB pages for direct mapping
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19fe00000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x19fe00000-0x19fffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19c000000-0x19fdfffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x19c000000-0x19fdfffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x180000000-0x19bffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x180000000-0x19bffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xd7f8ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0xc0000000-0xd7dfffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0xd7e00000-0xd7f8ffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x100000000-0x17fffffff] page 1G
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] RAMDISK: [mem 0x35a4e000-0x36d1efff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: RSDP 00000000000f8f50 000024 (v02 HP    )
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: XSDT 00000000d7fa0100 00007C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: FACP 00000000d7fa0290 0000F4 (v03 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: DSDT 00000000d7fa0620 006947 (v01 HP     ProLiant 00000006 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: FACS 00000000d7fae000 000040
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: APIC 00000000d7fa0390 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: MCFG 00000000d7fa0410 00003C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: SPMI 00000000d7fa0450 000041 (v05 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: OEMB 00000000d7fae040 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HPET 00000000d7fab4e0 000038 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: EINJ 00000000d7fab520 000130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: BERT 00000000d7fab6b0 000030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: ERST 00000000d7fab6e0 0001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HEST 00000000d7fab890 0000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: SSDT 00000000d7fab940 00052A (v01 HP     ProLiant 00000001 AMD  00000001)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No NUMA configuration found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000019fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   NODE_DATA [mem 0x19fff9000-0x19fffdfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199800000-ffff88019f5fffff] on node 0
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Zone ranges:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal   [mem 0x100000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Movable zone start for each node
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Early memory node ranges
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00100000-0xd7f8ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x100000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] On node 0 totalpages: 1539885
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32 zone: 13759 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32 zone: 880528 pages, LIFO batch:31
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal zone: 10240 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal zone: 655360 pages, LIFO batch:31
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] nr_irqs_gsi: 40
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e1fff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e2000-0x000fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f90000-0xd7f9dfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f9e000-0xd7f9ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fa0000-0xd7fadfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fae000-0xd7fdffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fe0000-0xd7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xff9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: [mem 0xf0000000-0xff9fffff] available for PCI devices
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s82368 r8192 d24128 u524288
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] pcpu-alloc: s82368 r8192 d24128 u524288 alloc=1*2097152
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1515801
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Policy zone: Normal
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Checking aperture...
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Node 0: aperture @ fdfc000000 size 32 MB
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] This costs you 64 MB of RAM
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc000000-0xcfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Memory: 5895336K/6159540K available (7385K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 264204K reserved)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Hierarchical RCU implementation.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Console: colour dummy device 80x25
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] console [tty0] enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] allocated 24641536 bytes of page_cgroup
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] hpet clockevent registered
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] tsc: Fast TSC calibration failed
Apr  9 07:32:06 AnotherMass kernel: [    0.012000] tsc: PIT calibration matches HPET. 2 loops
Apr  9 07:32:06 AnotherMass kernel: [    0.012000] tsc: Detected 2196.352 MHz processor
Apr  9 07:32:06 AnotherMass kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4392.70 BogoMIPS (lpj=8785408)
Apr  9 07:32:06 AnotherMass kernel: [    0.000011] pid_max: default: 32768 minimum: 301
Apr  9 07:32:06 AnotherMass kernel: [    0.000048] Security Framework initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.000070] AppArmor: AppArmor initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.000072] Yama: becoming mindful.
Apr  9 07:32:06 AnotherMass kernel: [    0.000758] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.004705] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006589] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006607] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006975] Initializing cgroup subsys memory
Apr  9 07:32:06 AnotherMass kernel: [    0.006986] Initializing cgroup subsys devices
Apr  9 07:32:06 AnotherMass kernel: [    0.006989] Initializing cgroup subsys freezer
Apr  9 07:32:06 AnotherMass kernel: [    0.006992] Initializing cgroup subsys blkio
Apr  9 07:32:06 AnotherMass kernel: [    0.006995] Initializing cgroup subsys perf_event
Apr  9 07:32:06 AnotherMass kernel: [    0.007000] Initializing cgroup subsys hugetlb
Apr  9 07:32:06 AnotherMass kernel: [    0.007024] tseg: 0000000000
Apr  9 07:32:06 AnotherMass kernel: [    0.007032] CPU: Physical Processor ID: 0
Apr  9 07:32:06 AnotherMass kernel: [    0.007035] CPU: Processor Core ID: 0
Apr  9 07:32:06 AnotherMass kernel: [    0.007038] mce: CPU supports 6 MCE banks
Apr  9 07:32:06 AnotherMass kernel: [    0.007046] LVT offset 0 assigned for vector 0xf9
Apr  9 07:32:06 AnotherMass kernel: [    0.007051] process: using AMD E400 aware idle routine
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] tlb_flushall_shift: 4
Apr  9 07:32:06 AnotherMass kernel: [    0.007178] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Apr  9 07:32:06 AnotherMass kernel: [    0.008119] ACPI: Core revision 20131115
Apr  9 07:32:06 AnotherMass kernel: [    0.011272] ACPI: All ACPI Tables successfully acquired
Apr  9 07:32:06 AnotherMass kernel: [    0.013039] ftrace: allocating 28562 entries in 112 pages
Apr  9 07:32:06 AnotherMass kernel: [    0.027635] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  9 07:32:06 AnotherMass kernel: [    0.068088] smpboot: CPU0: AMD Turion(tm) II Neo N54L Dual-Core Processor (fam: 10, model: 06, stepping: 03)
Apr  9 07:32:06 AnotherMass kernel: [    0.173246] Performance Events: AMD PMU driver.
Apr  9 07:32:06 AnotherMass kernel: [    0.173252] ... version:                0
Apr  9 07:32:06 AnotherMass kernel: [    0.173254] ... bit width:              48
Apr  9 07:32:06 AnotherMass kernel: [    0.173257] ... generic registers:      4
Apr  9 07:32:06 AnotherMass kernel: [    0.173259] ... value mask:             0000ffffffffffff
Apr  9 07:32:06 AnotherMass kernel: [    0.173261] ... max period:             00007fffffffffff
Apr  9 07:32:06 AnotherMass kernel: [    0.173263] ... fixed-purpose events:   0
Apr  9 07:32:06 AnotherMass kernel: [    0.173265] ... event mask:             000000000000000f
Apr  9 07:32:06 AnotherMass kernel: [    0.175041] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  9 07:32:06 AnotherMass kernel: [    0.175140] x86: Booting SMP configuration:
Apr  9 07:32:06 AnotherMass kernel: [    0.175144] .... node  #0, CPUs:      #1
Apr  9 07:32:06 AnotherMass kernel: [    0.188204] x86: Booted up 1 node, 2 CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.188208] smpboot: Total of 2 processors activated (8785.40 BogoMIPS)
Apr  9 07:32:06 AnotherMass kernel: [    0.188249] process: System has AMD C1E enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.188268] process: Switch to broadcast mode on CPU1
Apr  9 07:32:06 AnotherMass kernel: [    0.188922] process: Switch to broadcast mode on CPU0
Apr  9 07:32:06 AnotherMass kernel: [    0.189033] devtmpfs: initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.194229] EVM: security.selinux
Apr  9 07:32:06 AnotherMass kernel: [    0.194232] EVM: security.SMACK64
Apr  9 07:32:06 AnotherMass kernel: [    0.194234] EVM: security.ima
Apr  9 07:32:06 AnotherMass kernel: [    0.194236] EVM: security.capability
Apr  9 07:32:06 AnotherMass kernel: [    0.194326] PM: Registering ACPI NVS region [mem 0xd7fae000-0xd7fdffff] (204800 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.195482] pinctrl core: initialized pinctrl subsystem
Apr  9 07:32:06 AnotherMass kernel: [    0.195572] regulator-dummy: no parameters
Apr  9 07:32:06 AnotherMass kernel: [    0.195606] RTC time:  6:31:33, date: 04/09/15
Apr  9 07:32:06 AnotherMass kernel: [    0.195658] NET: Registered protocol family 16
Apr  9 07:32:06 AnotherMass kernel: [    0.195791] cpuidle: using governor ladder
Apr  9 07:32:06 AnotherMass kernel: [    0.195795] cpuidle: using governor menu
Apr  9 07:32:06 AnotherMass kernel: [    0.195801] node 0 link 0: io port [1000, ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195804] TOM: 00000000e0000000 aka 3584M
Apr  9 07:32:06 AnotherMass kernel: [    0.195807] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195810] node 0 link 0: mmio [a0000, bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195813] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195816] node 0 link 0: mmio [f8000000, fe6fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195818] node 0 link 0: mmio [fe700000, fe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195820] node 0 link 0: mmio [fe900000, ffdfffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195821] TOM2: 00000001a0000000 aka 6656M
Apr  9 07:32:06 AnotherMass kernel: [    0.195824] bus: [bus 00-1f] on node 0 link 0
Apr  9 07:32:06 AnotherMass kernel: [    0.195826] bus: 00 [io  0x0000-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195827] bus: 00 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195829] bus: 00 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195830] bus: 00 [mem 0x1a0000000-0xfcffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195892] ACPI: bus type PCI registered
Apr  9 07:32:06 AnotherMass kernel: [    0.195895] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  9 07:32:06 AnotherMass kernel: [    0.195961] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  9 07:32:06 AnotherMass kernel: [    0.195966] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  9 07:32:06 AnotherMass kernel: [    0.208048] PCI: Using configuration type 1 for base access
Apr  9 07:32:06 AnotherMass kernel: [    0.208241] mtrr: your CPUs had inconsistent variable MTRR settings
Apr  9 07:32:06 AnotherMass kernel: [    0.208244] mtrr: probably your BIOS does not setup all CPUs.
Apr  9 07:32:06 AnotherMass kernel: [    0.208246] mtrr: corrected configuration.
Apr  9 07:32:06 AnotherMass kernel: [    0.209208] bio: create slab <bio-0> at 0
Apr  9 07:32:06 AnotherMass kernel: [    0.209528] ACPI: Added _OSI(Module Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.209535] ACPI: Added _OSI(Processor Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.209538] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  9 07:32:06 AnotherMass kernel: [    0.209541] ACPI: Added _OSI(Processor Aggregator Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.211138] ACPI: Executed 2 blocks of module-level executable AML code
Apr  9 07:32:06 AnotherMass kernel: [    0.212995] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.216396] ACPI: OEMN 00000000d7faaeb0 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.216614] ACPI: Dynamic OEM Table Load:
Apr  9 07:32:06 AnotherMass kernel: [    0.216618] ACPI: OEMN           (null) 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.220457] \_SB_:_OSC evaluation returned wrong type
Apr  9 07:32:06 AnotherMass kernel: [    0.220463] _OSC request data:1 1f 
Apr  9 07:32:06 AnotherMass kernel: [    0.220622] ACPI: Interpreter enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.220633] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220640] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220646] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220660] ACPI: (supports S0 S4 S5)
Apr  9 07:32:06 AnotherMass kernel: [    0.220663] ACPI: Using IOAPIC for interrupt routing
Apr  9 07:32:06 AnotherMass kernel: [    0.220858] HEST: Table parsing has been initialized.
Apr  9 07:32:06 AnotherMass kernel: [    0.220863] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  9 07:32:06 AnotherMass kernel: [    0.220971] ACPI: No dock devices found.
Apr  9 07:32:06 AnotherMass kernel: [    0.225530] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  9 07:32:06 AnotherMass kernel: [    0.225539] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  9 07:32:06 AnotherMass kernel: [    0.225802] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Apr  9 07:32:06 AnotherMass kernel: [    0.226249] acpi PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.226254] acpi PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xfebfffff] ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.226261] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000dffff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff])
Apr  9 07:32:06 AnotherMass kernel: [    0.226485] PCI host bridge to bus 0000:00
Apr  9 07:32:06 AnotherMass kernel: [    0.226489] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226493] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.226496] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226500] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226505] pci_bus 0000:00: root bus resource [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226509] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226522] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.226639] pci 0000:00:01.0: [103c:9602] type 01 class 0x060400
Apr  9 07:32:06 AnotherMass kernel: [    0.226737] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
Apr  9 07:32:06 AnotherMass kernel: [    0.226773] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  9 07:32:06 AnotherMass kernel: [    0.226823] pci 0000:00:06.0: System wakeup disabled by ACPI
Apr  9 07:32:06 AnotherMass kernel: [    0.226873] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Apr  9 07:32:06 AnotherMass kernel: [    0.226894] pci 0000:00:11.0: reg 0x10: [io  0xd000-0xd007]
Apr  9 07:32:06 AnotherMass kernel: [    0.226904] pci 0000:00:11.0: reg 0x14: [io  0xc000-0xc003]
Apr  9 07:32:06 AnotherMass kernel: [    0.226913] pci 0000:00:11.0: reg 0x18: [io  0xb000-0xb007]
Apr  9 07:32:06 AnotherMass kernel: [    0.226923] pci 0000:00:11.0: reg 0x1c: [io  0xa000-0xa003]
Apr  9 07:32:06 AnotherMass kernel: [    0.226932] pci 0000:00:11.0: reg 0x20: [io  0x9000-0x900f]
Apr  9 07:32:06 AnotherMass kernel: [    0.226942] pci 0000:00:11.0: reg 0x24: [mem 0xfe6ffc00-0xfe6fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227065] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.227078] pci 0000:00:12.0: reg 0x10: [mem 0xfe6fe000-0xfe6fefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227201] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.227220] pci 0000:00:12.2: reg 0x10: [mem 0xfe6ff800-0xfe6ff8ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227299] pci 0000:00:12.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.227301] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.227384] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.227397] pci 0000:00:13.0: reg 0x10: [mem 0xfe6fd000-0xfe6fdfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227520] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.227539] pci 0000:00:13.2: reg 0x10: [mem 0xfe6ff400-0xfe6ff4ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227617] pci 0000:00:13.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.227619] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.227699] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Apr  9 07:32:06 AnotherMass kernel: [    0.227828] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Apr  9 07:32:06 AnotherMass kernel: [    0.227957] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Apr  9 07:32:06 AnotherMass kernel: [    0.228031] pci 0000:00:14.4: System wakeup disabled by ACPI
Apr  9 07:32:06 AnotherMass kernel: [    0.228068] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.228081] pci 0000:00:16.0: reg 0x10: [mem 0xfe6fc000-0xfe6fcfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228205] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.228224] pci 0000:00:16.2: reg 0x10: [mem 0xfe6ff000-0xfe6ff0ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228307] pci 0000:00:16.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.228309] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.228388] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228459] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228527] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228595] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228665] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228785] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
Apr  9 07:32:06 AnotherMass kernel: [    0.228794] pci 0000:01:05.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.228799] pci 0000:01:05.0: reg 0x14: [io  0xe000-0xe0ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228804] pci 0000:01:05.0: reg 0x18: [mem 0xfe8f0000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228815] pci 0000:01:05.0: reg 0x24: [mem 0xfe700000-0xfe7fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228834] pci 0000:01:05.0: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.228893] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  9 07:32:06 AnotherMass kernel: [    0.228898] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228901] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228905] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.228966] pci 0000:02:00.0: [14e4:165b] type 00 class 0x020000
Apr  9 07:32:06 AnotherMass kernel: [    0.228985] pci 0000:02:00.0: reg 0x10: [mem 0xfe9f0000-0xfe9fffff 64bit]
Apr  9 07:32:06 AnotherMass kernel: [    0.229089] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  9 07:32:06 AnotherMass kernel: [    0.236326] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  9 07:32:06 AnotherMass kernel: [    0.236341] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.236441] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236452] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236455] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236457] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236459] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236461] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.237436] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237508] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237578] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237644] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237698] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237742] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237785] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237829] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237955] ACPI: Enabled 4 GPEs in block 00 to 1F
Apr  9 07:32:06 AnotherMass kernel: [    0.237963] ACPI: \_SB_.PCI0: notify handler is installed
Apr  9 07:32:06 AnotherMass kernel: [    0.237997] Found 1 acpi root devices
Apr  9 07:32:06 AnotherMass kernel: [    0.238162] vgaarb: setting as boot device: PCI:0000:01:05.0
Apr  9 07:32:06 AnotherMass kernel: [    0.238166] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Apr  9 07:32:06 AnotherMass kernel: [    0.238169] vgaarb: loaded
Apr  9 07:32:06 AnotherMass kernel: [    0.238172] vgaarb: bridge control possible 0000:01:05.0
Apr  9 07:32:06 AnotherMass kernel: [    0.238370] SCSI subsystem initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.238449] libata version 3.00 loaded.
Apr  9 07:32:06 AnotherMass kernel: [    0.238471] ACPI: bus type USB registered
Apr  9 07:32:06 AnotherMass kernel: [    0.238491] usbcore: registered new interface driver usbfs
Apr  9 07:32:06 AnotherMass kernel: [    0.238500] usbcore: registered new interface driver hub
Apr  9 07:32:06 AnotherMass kernel: [    0.238602] usbcore: registered new device driver usb
Apr  9 07:32:06 AnotherMass kernel: [    0.238796] PCI: Using ACPI for IRQ routing
Apr  9 07:32:06 AnotherMass kernel: [    0.246925] PCI: pci_cache_line_size set to 64 bytes
Apr  9 07:32:06 AnotherMass kernel: [    0.246970] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.246973] e820: reserve RAM buffer [mem 0xd7f90000-0xd7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.247076] NetLabel: Initializing
Apr  9 07:32:06 AnotherMass kernel: [    0.247079] NetLabel:  domain hash size = 128
Apr  9 07:32:06 AnotherMass kernel: [    0.247081] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  9 07:32:06 AnotherMass kernel: [    0.247094] NetLabel:  unlabeled traffic allowed by default
Apr  9 07:32:06 AnotherMass kernel: [    0.247213] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  9 07:32:06 AnotherMass kernel: [    0.247219] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr  9 07:32:06 AnotherMass kernel: [    0.249286] Switched to clocksource hpet
Apr  9 07:32:06 AnotherMass kernel: [    0.255191] AppArmor: AppArmor Filesystem Enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.255236] pnp: PnP ACPI init
Apr  9 07:32:06 AnotherMass kernel: [    0.255256] ACPI: bus type PNP registered
Apr  9 07:32:06 AnotherMass kernel: [    0.255478] system 00:00: [mem 0xd8000000-0xdfffffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255485] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255545] pnp 00:01: [dma 4]
Apr  9 07:32:06 AnotherMass kernel: [    0.255568] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255602] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255663] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255688] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255729] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255823] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255827] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255831] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256008] system 00:07: [io  0x04d0-0x04d1] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256012] system 00:07: [io  0x040b] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256015] system 00:07: [io  0x04d6] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256019] system 00:07: [io  0x0c00-0x0c01] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256023] system 00:07: [io  0x0c14] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256026] system 00:07: [io  0x0c50-0x0c51] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256029] system 00:07: [io  0x0c52] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256033] system 00:07: [io  0x0c6c] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256036] system 00:07: [io  0x0c6f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256040] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256048] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256052] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256056] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256059] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256063] system 00:07: [io  0x0800-0x089f] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256066] system 00:07: [io  0x0b00-0x0b1f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256070] system 00:07: [io  0x0b20-0x0b3f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256073] system 00:07: [io  0x0900-0x090f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256077] system 00:07: [io  0x0910-0x091f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256081] system 00:07: [io  0xfe00-0xfefe] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256085] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256089] system 00:07: [mem 0xfec10000-0xfec1001f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256093] system 00:07: [mem 0xfed80000-0xfed80fff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256097] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256160] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256165] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256283] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256288] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256292] system 00:09: [mem 0x00100000-0xd7ffffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256296] system 00:09: [mem 0xfec00000-0xffffffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256300] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256391] pnp: PnP ACPI: found 10 devices
Apr  9 07:32:06 AnotherMass kernel: [    0.256394] ACPI: bus type PNP unregistered
Apr  9 07:32:06 AnotherMass kernel: [    0.263537] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  9 07:32:06 AnotherMass kernel: [    0.263542] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263547] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263552] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.263558] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  9 07:32:06 AnotherMass kernel: [    0.263562] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263568] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  9 07:32:06 AnotherMass kernel: [    0.263581] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.263584] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263586] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263588] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263590] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263593] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263595] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263597] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.263600] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263602] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.263604] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263606] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263608] pci_bus 0000:03: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263611] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263647] NET: Registered protocol family 2
Apr  9 07:32:06 AnotherMass kernel: [    0.263912] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264211] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264647] TCP: Hash tables configured (established 65536 bind 65536)
Apr  9 07:32:06 AnotherMass kernel: [    0.264725] TCP: reno registered
Apr  9 07:32:06 AnotherMass kernel: [    0.264744] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264826] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264992] NET: Registered protocol family 1
Apr  9 07:32:06 AnotherMass kernel: [    0.265009] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Apr  9 07:32:06 AnotherMass kernel: [    1.245263] pci 0000:01:05.0: Video device with shadowed ROM
Apr  9 07:32:06 AnotherMass kernel: [    1.245271] PCI: CLS 64 bytes, default 64
Apr  9 07:32:06 AnotherMass kernel: [    1.245354] Trying to unpack rootfs image as initramfs...
Apr  9 07:32:06 AnotherMass kernel: [    1.621606] Freeing initrd memory: 19268K (ffff880035a4e000 - ffff880036d1f000)
Apr  9 07:32:06 AnotherMass kernel: [    1.621853] PCI-DMA: Disabling AGP.
Apr  9 07:32:06 AnotherMass kernel: [    1.621971] PCI-DMA: aperture base @ cc000000 size 65536 KB
Apr  9 07:32:06 AnotherMass kernel: [    1.621975] PCI-DMA: using GART IOMMU.
Apr  9 07:32:06 AnotherMass kernel: [    1.621979] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr  9 07:32:06 AnotherMass kernel: [    1.626021] LVT offset 1 assigned for vector 0x400
Apr  9 07:32:06 AnotherMass kernel: [    1.626040] IBS: LVT offset 1 assigned
Apr  9 07:32:06 AnotherMass kernel: [    1.626077] perf: AMD IBS detected (0x0000001f)
Apr  9 07:32:06 AnotherMass kernel: [    1.626148] microcode: CPU0: patch_level=0x010000c8
Apr  9 07:32:06 AnotherMass kernel: [    1.626161] microcode: CPU1: patch_level=0x010000c8
Apr  9 07:32:06 AnotherMass kernel: [    1.626252] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  9 07:32:06 AnotherMass kernel: [    1.626257] Scanning for low memory corruption every 60 seconds
Apr  9 07:32:06 AnotherMass kernel: [    1.626540] Initialise system trusted keyring
Apr  9 07:32:06 AnotherMass kernel: [    1.626597] audit: initializing netlink socket (disabled)
Apr  9 07:32:06 AnotherMass kernel: [    1.626615] type=2000 audit(1428561094.528:1): initialized
Apr  9 07:32:06 AnotherMass kernel: [    1.660089] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  9 07:32:06 AnotherMass kernel: [    1.661755] zbud: loaded
Apr  9 07:32:06 AnotherMass kernel: [    1.662058] VFS: Disk quotas dquot_6.5.2
Apr  9 07:32:06 AnotherMass kernel: [    1.662126] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    1.662778] fuse init (API version 7.22)
Apr  9 07:32:06 AnotherMass kernel: [    1.662960] msgmni has been set to 11680
Apr  9 07:32:06 AnotherMass kernel: [    1.663035] Key type big_key registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663638] Key type asymmetric registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663641] Asymmetric key parser 'x509' registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663678] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Apr  9 07:32:06 AnotherMass kernel: [    1.663727] io scheduler noop registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663730] io scheduler deadline registered (default)
Apr  9 07:32:06 AnotherMass kernel: [    1.663759] io scheduler cfq registered
Apr  9 07:32:06 AnotherMass kernel: [    1.664031] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [    1.664105] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
Apr  9 07:32:06 AnotherMass kernel: [    1.664110] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Apr  9 07:32:06 AnotherMass kernel: [    1.664114] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
Apr  9 07:32:06 AnotherMass kernel: [    1.664127] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  9 07:32:06 AnotherMass kernel: [    1.664143] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  9 07:32:06 AnotherMass kernel: [    1.664182] vesafb: mode is 1152x864x32, linelength=4608, pages=0
Apr  9 07:32:06 AnotherMass kernel: [    1.664185] vesafb: scrolling: redraw
Apr  9 07:32:06 AnotherMass kernel: [    1.664188] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Apr  9 07:32:06 AnotherMass kernel: [    1.664379] vesafb: framebuffer at 0xf0000000, mapped to 0xffffc90010e80000, using 3904k, total 3904k
Apr  9 07:32:06 AnotherMass kernel: [    1.819607] Console: switching to colour frame buffer device 144x54
Apr  9 07:32:06 AnotherMass kernel: [    1.976152] fb0: VESA VGA frame buffer device
Apr  9 07:32:06 AnotherMass kernel: [    1.977219] ipmi message handler version 39.2
Apr  9 07:32:06 AnotherMass kernel: [    1.978288] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr  9 07:32:06 AnotherMass kernel: [    1.980166] ACPI: Power Button [PWRB]
Apr  9 07:32:06 AnotherMass kernel: [    1.981085] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  9 07:32:06 AnotherMass kernel: [    1.982768] ACPI: Power Button [PWRF]
Apr  9 07:32:06 AnotherMass kernel: [    1.983666] ACPI: processor limited to max C-state 1
Apr  9 07:32:06 AnotherMass kernel: [    1.984913] ERST: Failed to get Error Log Address Range.
Apr  9 07:32:06 AnotherMass kernel: [    2.000633] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
Apr  9 07:32:06 AnotherMass kernel: [    2.002842] GHES: APEI firmware first mode is enabled by WHEA _OSC.
Apr  9 07:32:06 AnotherMass kernel: [    2.004472] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  9 07:32:06 AnotherMass kernel: [    2.007814] Linux agpgart interface v0.103
Apr  9 07:32:06 AnotherMass kernel: [    2.010850] brd: module loaded
Apr  9 07:32:06 AnotherMass kernel: [    2.012951] loop: module loaded
Apr  9 07:32:06 AnotherMass kernel: [    2.014073] libphy: Fixed MDIO Bus: probed
Apr  9 07:32:06 AnotherMass kernel: [    2.015101] tun: Universal TUN/TAP device driver, 1.6
Apr  9 07:32:06 AnotherMass kernel: [    2.016259] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  9 07:32:06 AnotherMass kernel: [    2.017828] PPP generic driver version 2.4.2
Apr  9 07:32:06 AnotherMass kernel: [    2.018947] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  9 07:32:06 AnotherMass kernel: [    2.020484] ehci-pci: EHCI PCI platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.021692] QUIRK: Enable AMD PLL fix
Apr  9 07:32:06 AnotherMass kernel: [    2.021715] ehci-pci 0000:00:12.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.022908] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr  9 07:32:06 AnotherMass kernel: [    2.024637] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.026646] ehci-pci 0000:00:12.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.027763] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe6ff800
Apr  9 07:32:06 AnotherMass kernel: [    2.040505] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.041894] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.043439] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.045124] usb usb1: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.101215] usb usb1: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.157623] usb usb1: SerialNumber: 0000:00:12.2
Apr  9 07:32:06 AnotherMass kernel: [    2.213611] hub 1-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.269347] hub 1-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.324358] ehci-pci 0000:00:13.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.379222] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr  9 07:32:06 AnotherMass kernel: [    2.434911] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.491516] ehci-pci 0000:00:13.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.547909] ehci-pci 0000:00:13.2: irq 17, io mem 0xfe6ff400
Apr  9 07:32:06 AnotherMass kernel: [    2.616221] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.672146] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.728161] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.784912] usb usb2: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.841679] usb usb2: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.898910] usb usb2: SerialNumber: 0000:00:13.2
Apr  9 07:32:06 AnotherMass kernel: [    2.955230] tsc: Refined TSC clocksource calibration: 2196.341 MHz
Apr  9 07:32:06 AnotherMass kernel: [    2.956190] hub 2-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.956198] hub 2-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.956500] ehci-pci 0000:00:16.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.956505] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr  9 07:32:06 AnotherMass kernel: [    2.956508] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.956524] ehci-pci 0000:00:16.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.956571] ehci-pci 0000:00:16.2: irq 17, io mem 0xfe6ff000
Apr  9 07:32:06 AnotherMass kernel: [    2.964061] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.964121] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.964123] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.964124] usb usb3: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.964125] usb usb3: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.964126] usb usb3: SerialNumber: 0000:00:16.2
Apr  9 07:32:06 AnotherMass kernel: [    2.964251] hub 3-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.964258] hub 3-0:1.0: 4 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.964382] ehci-platform: EHCI generic platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964396] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964396] ohci-pci: OHCI PCI platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964569] ohci-pci 0000:00:12.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    2.964575] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr  9 07:32:06 AnotherMass kernel: [    2.964605] ohci-pci 0000:00:12.0: irq 18, io mem 0xfe6fe000
Apr  9 07:32:06 AnotherMass kernel: [    3.024076] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    3.024077] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    3.024079] usb usb4: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    3.024080] usb usb4: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    3.024081] usb usb4: SerialNumber: 0000:00:12.0
Apr  9 07:32:06 AnotherMass kernel: [    3.024212] hub 4-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    3.024227] hub 4-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    3.024511] ohci-pci 0000:00:13.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    3.024516] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr  9 07:32:06 AnotherMass kernel: [    3.024538] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe6fd000
Apr  9 07:32:06 AnotherMass kernel: [    4.635306] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    4.684552] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    4.734316] usb usb5: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    4.784777] usb usb5: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    4.834651] usb usb5: SerialNumber: 0000:00:13.0
Apr  9 07:32:06 AnotherMass kernel: [    4.884203] hub 5-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    4.895117] usb 4-2: new low-speed USB device number 2 using ohci-pci
Apr  9 07:32:06 AnotherMass kernel: [    4.982982] hub 5-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    5.032667] ohci-pci 0000:00:16.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    5.082623] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 6
Apr  9 07:32:06 AnotherMass kernel: [    5.104121] usb 4-2: New USB device found, idVendor=04f3, idProduct=0103
Apr  9 07:32:06 AnotherMass kernel: [    5.104123] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  9 07:32:06 AnotherMass kernel: [    5.235932] ohci-pci 0000:00:16.0: irq 18, io mem 0xfe6fc000
Apr  9 07:32:06 AnotherMass kernel: [    5.346916] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    5.397902] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    5.449519] usb usb6: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    5.501535] usb usb6: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    5.553470] usb usb6: SerialNumber: 0000:00:16.0
Apr  9 07:32:06 AnotherMass kernel: [    5.605094] hub 6-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    5.655801] hub 6-0:1.0: 4 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    5.706177] Switched to clocksource tsc
Apr  9 07:32:06 AnotherMass kernel: [    5.706249] ohci-platform: OHCI generic platform driver
Apr  9 07:32:06 AnotherMass kernel: [    5.706263] uhci_hcd: USB Universal Host Controller Interface driver
Apr  9 07:32:06 AnotherMass kernel: [    5.706329] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr  9 07:32:06 AnotherMass kernel: [    6.730619] i8042: No controller found
Apr  9 07:32:06 AnotherMass kernel: [    6.781411] mousedev: PS/2 mouse device common for all mice
Apr  9 07:32:06 AnotherMass kernel: [    6.833174] rtc_cmos 00:02: RTC can wake from S4
Apr  9 07:32:06 AnotherMass kernel: [    6.884178] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Apr  9 07:32:06 AnotherMass kernel: [    6.934800] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  9 07:32:06 AnotherMass kernel: [    6.986399] device-mapper: uevent: version 1.0.3
Apr  9 07:32:06 AnotherMass kernel: [    7.038139] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Apr  9 07:32:06 AnotherMass kernel: [    7.090830] ledtrig-cpu: registered to indicate activity on CPUs
Apr  9 07:32:06 AnotherMass kernel: [    7.143821] TCP: cubic registered
Apr  9 07:32:06 AnotherMass kernel: [    7.196068] NET: Registered protocol family 10
Apr  9 07:32:06 AnotherMass kernel: [    7.248431] NET: Registered protocol family 17
Apr  9 07:32:06 AnotherMass kernel: [    7.299969] Key type dns_resolver registered
Apr  9 07:32:06 AnotherMass kernel: [    7.351855] Loading compiled-in X.509 certificates
Apr  9 07:32:06 AnotherMass kernel: [    7.405274] Loaded X.509 cert 'Magrathea: Glacier signing key: 4eb2de249917cbf39cb85692e54cebade594d680'
Apr  9 07:32:06 AnotherMass kernel: [    7.459440] registered taskstats version 1
Apr  9 07:32:06 AnotherMass kernel: [    7.515805] Key type trusted registered
Apr  9 07:32:06 AnotherMass kernel: [    7.573196] Key type encrypted registered
Apr  9 07:32:06 AnotherMass kernel: [    7.626460] AppArmor: AppArmor sha1 policy hashing enabled
Apr  9 07:32:06 AnotherMass kernel: [    7.680578] IMA: No TPM chip found, activating TPM-bypass!
Apr  9 07:32:06 AnotherMass kernel: [    7.735314] regulator-dummy: disabling
Apr  9 07:32:06 AnotherMass kernel: [    7.788932]   Magic number: 11:773:518
Apr  9 07:32:06 AnotherMass kernel: [    7.842426] rtc_cmos 00:02: setting system clock to 2015-04-09 06:31:41 UTC (1428561101)
Apr  9 07:32:06 AnotherMass kernel: [    7.896864] acpi-cpufreq: overriding BIOS provided _PSD data
Apr  9 07:32:06 AnotherMass kernel: [    7.951310] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  9 07:32:06 AnotherMass kernel: [    8.006537] EDD information not available.
Apr  9 07:32:06 AnotherMass kernel: [    8.061721] PM: Hibernation image not present or could not be loaded.
Apr  9 07:32:06 AnotherMass kernel: [    8.063444] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Apr  9 07:32:06 AnotherMass kernel: [    8.120603] Write protecting the kernel read-only data: 12288k
Apr  9 07:32:06 AnotherMass kernel: [    8.180573] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
Apr  9 07:32:06 AnotherMass kernel: [    8.240618] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
Apr  9 07:32:06 AnotherMass kernel: [    8.436246] md: linear personality registered for level -1
Apr  9 07:32:06 AnotherMass kernel: [    8.494666] pps_core: LinuxPPS API ver. 1 registered
Apr  9 07:32:06 AnotherMass kernel: [    8.553087] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Apr  9 07:32:06 AnotherMass kernel: [    8.615703] md: multipath personality registered for level -4
Apr  9 07:32:06 AnotherMass kernel: [    8.684730] hidraw: raw HID events driver (C) Jiri Kosina
Apr  9 07:32:06 AnotherMass kernel: [    8.751775] md: raid0 personality registered for level 0
Apr  9 07:32:06 AnotherMass kernel: [    8.811959] PTP clock support registered
Apr  9 07:32:06 AnotherMass kernel: [    8.874981] ahci 0000:00:11.0: version 3.0
Apr  9 07:32:06 AnotherMass kernel: [    8.875220] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [    8.875330] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Apr  9 07:32:06 AnotherMass kernel: [    8.936619] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
Apr  9 07:32:06 AnotherMass kernel: [    8.997795] tg3.c:v3.134 (Sep 16, 2013)
Apr  9 07:32:06 AnotherMass kernel: [    9.058490] md: raid1 personality registered for level 1
Apr  9 07:32:06 AnotherMass kernel: [    9.124996] scsi0 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.185051] scsi1 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.188909] raid6: sse2x1    2994 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.256870] raid6: sse2x2    4707 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.324840] raid6: sse2x4    5532 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.324841] raid6: using algorithm sse2x4 (5532 MB/s)
Apr  9 07:32:06 AnotherMass kernel: [    9.324842] raid6: using intx1 recovery algorithm
Apr  9 07:32:06 AnotherMass kernel: [    9.531779] scsi2 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589106] xor: measuring software checksum speed
Apr  9 07:32:06 AnotherMass kernel: [    9.589329] scsi3 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589404] scsi4 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589477] scsi5 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589519] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589522] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589525] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589528] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589531] ata5: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589533] ata6: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.593108] usbcore: registered new interface driver usbhid
Apr  9 07:32:06 AnotherMass kernel: [    9.593110] usbhid: USB HID core driver
Apr  9 07:32:06 AnotherMass kernel: [   10.234490] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input2
Apr  9 07:32:06 AnotherMass kernel: [   10.268367]    prefetch64-sse:  9035.000 MB/sec
Apr  9 07:32:06 AnotherMass kernel: [   10.308348]    generic_sse:  8511.000 MB/sec
Apr  9 07:32:06 AnotherMass kernel: [   10.308349] xor: using function: prefetch64-sse (9035.000 MB/sec)
Apr  9 07:32:06 AnotherMass kernel: [   10.445001] hid-generic 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:12.0-2/input0
Apr  9 07:32:06 AnotherMass kernel: [   10.500019] async_tx: api initialized (async)
Apr  9 07:32:06 AnotherMass kernel: [   10.527222] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 38:ea:a7:a3:2a:32
Apr  9 07:32:06 AnotherMass kernel: [   10.527224] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Apr  9 07:32:06 AnotherMass kernel: [   10.527226] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  9 07:32:06 AnotherMass kernel: [   10.527227] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  9 07:32:06 AnotherMass kernel: [   10.784343] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input3
Apr  9 07:32:06 AnotherMass kernel: [   10.842830] ata5: SATA link down (SStatus 0 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   10.902082] hid-generic 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:12.0-2/input1
Apr  9 07:32:06 AnotherMass kernel: [   10.967168] md: raid6 personality registered for level 6
Apr  9 07:32:06 AnotherMass kernel: [   11.026952] md: raid5 personality registered for level 5
Apr  9 07:32:06 AnotherMass kernel: [   11.085749] md: raid4 personality registered for level 4
Apr  9 07:32:06 AnotherMass kernel: [   11.116037] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116071] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116097] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116594] ata4.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116596] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.116603] ata3.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116604] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.116652] ata2.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116653] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.117153] ata4.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.117176] ata3.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.117185] ata2.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180005] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.180037] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.180469] ata6.00: ATA-9: SanDisk SDSSDRC032G, 3.0.0, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180471] ata6.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr  9 07:32:06 AnotherMass kernel: [   11.180576] ata1.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180578] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.181181] ata1.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.181327] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.181609] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.181610] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.181649] sd 0:0:0:0: [sda] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.181651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.181668] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182050] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182193] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182303] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182405] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182506] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182606] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182706] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182752] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182753] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182771] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182772] sd 2:0:0:0: [sdc] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182810] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182811] sd 1:0:0:0: [sdb] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182853] sd 3:0:0:0: [sdd] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182855] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182877] sd 2:0:0:0: [sdc] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182879] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182908] sd 3:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182947] sd 1:0:0:0: [sdb] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182949] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182958] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182995] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.184028] ata6.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.184136] scsi 5:0:0:0: Direct-Access     ATA      SanDisk SDSSDRC0 3.0. PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.184274] sd 5:0:0:0: Attached scsi generic sg4 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.184330] sd 5:0:0:0: [sde] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.184381] sd 5:0:0:0: [sde] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.184383] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.184399] sd 5:0:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.185475]  sde: sde1 sde2 < sde5 >
Apr  9 07:32:06 AnotherMass kernel: [   11.185829] sd 5:0:0:0: [sde] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.245378]  sdb: sdb1
Apr  9 07:32:06 AnotherMass kernel: [   11.245632] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.252015]  sda: sda1
Apr  9 07:32:06 AnotherMass kernel: [   11.252266] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.809616]  sdc: sdc1
Apr  9 07:32:06 AnotherMass kernel: [   11.809859] sd 2:0:0:0: [sdc] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.881694]  sdd: sdd1
Apr  9 07:32:06 AnotherMass kernel: [   11.881942] sd 3:0:0:0: [sdd] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   14.386338] [sched_delayed] sched: RT throttling activated
Apr  9 07:32:06 AnotherMass kernel: [   14.439531] md: raid10 personality registered for level 10
Apr  9 07:32:06 AnotherMass kernel: [   14.450149] random: nonblocking pool is initialized
Apr  9 07:32:06 AnotherMass kernel: [   14.551681] md: bind<sdd1>
Apr  9 07:32:06 AnotherMass kernel: [   14.560761] md: bind<sda1>
Apr  9 07:32:06 AnotherMass kernel: [   14.572103] md: bind<sdc1>
Apr  9 07:32:06 AnotherMass kernel: [   14.576350] md: bind<sdb1>
Apr  9 07:32:06 AnotherMass kernel: [   14.994158] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Apr  9 07:32:06 AnotherMass kernel: [   18.939514] Adding 6157308k swap on /dev/sde5.  Priority:-1 extents:1 across:6157308k SSFS
Apr  9 07:32:06 AnotherMass kernel: [   19.003988] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
Apr  9 07:32:06 AnotherMass kernel: [   19.974813] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 07:32:06 AnotherMass kernel: [   20.156713] lp: driver loaded but no devices found
Apr  9 07:32:06 AnotherMass kernel: [   20.168428] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  9 07:32:06 AnotherMass kernel: [   20.184769] ppdev: user-space parallel port driver
Apr  9 07:32:06 AnotherMass kernel: [   20.244673] [drm] Initialized drm 1.1.0 20060810
Apr  9 07:32:06 AnotherMass kernel: [   20.258936] type=1400 audit(1428561113.917:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.258945] type=1400 audit(1428561113.917:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.258950] type=1400 audit(1428561113.917:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259542] type=1400 audit(1428561113.921:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259549] type=1400 audit(1428561113.921:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259841] type=1400 audit(1428561113.921:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.310762] [drm] radeon kernel modesetting enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.310847] checking generic (f0000000 3d0000) vs hw (f0000000 8000000)
Apr  9 07:32:06 AnotherMass kernel: [   20.310849] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
Apr  9 07:32:06 AnotherMass kernel: [   20.310877] Console: switching to colour dummy device 80x25
Apr  9 07:32:06 AnotherMass kernel: [   20.312545] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
Apr  9 07:32:06 AnotherMass kernel: [   20.312563] [drm] register mmio base: 0xFE8F0000
Apr  9 07:32:06 AnotherMass kernel: [   20.312564] [drm] register mmio size: 65536
Apr  9 07:32:06 AnotherMass kernel: [   20.313289] ATOM BIOS: AMD_1407_150
Apr  9 07:32:06 AnotherMass kernel: [   20.313320] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
Apr  9 07:32:06 AnotherMass kernel: [   20.313322] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Apr  9 07:32:06 AnotherMass kernel: [   20.313327] [drm] Detected VRAM RAM=128M, BAR=128M
Apr  9 07:32:06 AnotherMass kernel: [   20.313329] [drm] RAM width 32bits DDR
Apr  9 07:32:06 AnotherMass kernel: [   20.313575] [TTM] Zone  kernel: Available graphics memory: 2991704 kiB
Apr  9 07:32:06 AnotherMass kernel: [   20.313576] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Apr  9 07:32:06 AnotherMass kernel: [   20.313578] [TTM] Initializing pool allocator
Apr  9 07:32:06 AnotherMass kernel: [   20.313583] [TTM] Initializing DMA pool allocator
Apr  9 07:32:06 AnotherMass kernel: [   20.313605] [drm] radeon: 128M of VRAM memory ready
Apr  9 07:32:06 AnotherMass kernel: [   20.313606] [drm] radeon: 512M of GTT memory ready.
Apr  9 07:32:06 AnotherMass kernel: [   20.313616] [drm] Loading RS780 Microcode
Apr  9 07:32:06 AnotherMass kernel: [   20.314490] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr  9 07:32:06 AnotherMass kernel: [   20.314568] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
Apr  9 07:32:06 AnotherMass kernel: [   20.316416] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Apr  9 07:32:06 AnotherMass kernel: [   20.316652] sp5100_tco: PCI Revision ID: 0x42
Apr  9 07:32:06 AnotherMass kernel: [   20.316705] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
Apr  9 07:32:06 AnotherMass kernel: [   20.316717] sp5100_tco: Last reboot was not triggered by watchdog.
Apr  9 07:32:06 AnotherMass kernel: [   20.316792] sp5100_tco: initialized (0xffffc90000c64b00). heartbeat=60 sec (nowayout=0)
Apr  9 07:32:06 AnotherMass kernel: [   20.332458] [drm] GART: num cpu pages 131072, num gpu pages 131072
Apr  9 07:32:06 AnotherMass kernel: [   20.344166] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Apr  9 07:32:06 AnotherMass kernel: [   20.344744] MCE: In-kernel MCE decoding enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.345128] radeon 0000:01:05.0: WB enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.345155] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880035b2cc00
Apr  9 07:32:06 AnotherMass kernel: [   20.345167] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880035b2cc0c
Apr  9 07:32:06 AnotherMass kernel: [   20.347320] EDAC MC: Ver: 3.0.0
Apr  9 07:32:06 AnotherMass kernel: [   20.347621] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  9 07:32:06 AnotherMass kernel: [   20.347624] [drm] Driver supports precise vblank timestamp query.
Apr  9 07:32:06 AnotherMass kernel: [   20.347628] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
Apr  9 07:32:06 AnotherMass kernel: [   20.347647] [drm] radeon: irq initialized.
Apr  9 07:32:06 AnotherMass kernel: [   20.351762] tg3 0000:02:00.0: irq 42 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [   20.354383] AMD64 EDAC driver v3.4.0
Apr  9 07:32:06 AnotherMass kernel: [   20.354423] EDAC amd64: DRAM ECC enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.354429] EDAC amd64: F10h detected (node 0).
Apr  9 07:32:06 AnotherMass kernel: [   20.354444] EDAC MC: DCT0 chip selects:
Apr  9 07:32:06 AnotherMass kernel: [   20.354446] EDAC amd64: MC: 0:  1024MB 1:  1024MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354448] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354449] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354450] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354452] EDAC MC: DCT1 chip selects:
Apr  9 07:32:06 AnotherMass kernel: [   20.354453] EDAC amd64: MC: 0:  2048MB 1:  2048MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354454] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354456] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354457] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354458] EDAC amd64: using x4 syndromes.
Apr  9 07:32:06 AnotherMass kernel: [   20.354460] EDAC amd64: MCT channel count: 2
Apr  9 07:32:06 AnotherMass kernel: [   20.354483] EDAC amd64: CS0: Unbuffered DDR3 RAM
Apr  9 07:32:06 AnotherMass kernel: [   20.354484] EDAC amd64: CS1: Unbuffered DDR3 RAM
Apr  9 07:32:06 AnotherMass kernel: [   20.357884] EDAC MC0: Giving out device to module amd64_edac controller F10h: DEV 0000:00:18.2 (INTERRUPT)
Apr  9 07:32:06 AnotherMass kernel: [   20.358660] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
Apr  9 07:32:06 AnotherMass kernel: [   20.456506] kvm: Nested Virtualization enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.456512] kvm: Nested Paging enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.578826] [drm] ring test on 0 succeeded in 1 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.578872] [drm] ring test on 3 succeeded in 2 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.579010] [drm] Enabling audio 0 support
Apr  9 07:32:06 AnotherMass kernel: [   20.579084] [drm] ib test on ring 0 succeeded in 0 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.579142] [drm] ib test on ring 3 succeeded in 0 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.582862] [drm] Radeon Display Connectors
Apr  9 07:32:06 AnotherMass kernel: [   20.582864] [drm] Connector 0:
Apr  9 07:32:06 AnotherMass kernel: [   20.582866] [drm]   VGA-1
Apr  9 07:32:06 AnotherMass kernel: [   20.582868] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Apr  9 07:32:06 AnotherMass kernel: [   20.582869] [drm]   Encoders:
Apr  9 07:32:06 AnotherMass kernel: [   20.582870] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Apr  9 07:32:06 AnotherMass kernel: [   20.582919] [drm] radeon: power management initialized
Apr  9 07:32:06 AnotherMass kernel: [   20.774447] [drm] fb mappable at 0xF0141000
Apr  9 07:32:06 AnotherMass kernel: [   20.774449] [drm] vram apper at 0xF0000000
Apr  9 07:32:06 AnotherMass kernel: [   20.774450] [drm] size 5324800
Apr  9 07:32:06 AnotherMass kernel: [   20.774451] [drm] fb depth is 24
Apr  9 07:32:06 AnotherMass kernel: [   20.774452] [drm]    pitch is 5888
Apr  9 07:32:06 AnotherMass kernel: [   20.775195] fbcon: radeondrmfb (fb0) is primary device
Apr  9 07:32:06 AnotherMass kernel: [   20.791924] Console: switching to colour frame buffer device 180x56
Apr  9 07:32:06 AnotherMass kernel: [   20.852674] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
Apr  9 07:32:06 AnotherMass kernel: [   20.852676] radeon 0000:01:05.0: registered panic notifier
Apr  9 07:32:06 AnotherMass kernel: [   20.852700] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0
Apr  9 07:32:06 AnotherMass kernel: [   21.126559] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 07:32:06 AnotherMass kernel: [   23.545161] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
Apr  9 07:32:06 AnotherMass kernel: [   23.545167] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
Apr  9 07:32:06 AnotherMass kernel: [   23.545189] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  9 07:32:06 AnotherMass kernel: [   33.035405] Bluetooth: Core ver 2.17
Apr  9 07:32:06 AnotherMass kernel: [   33.035433] NET: Registered protocol family 31
Apr  9 07:32:06 AnotherMass kernel: [   33.035435] Bluetooth: HCI device and connection manager initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035447] Bluetooth: HCI socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035450] Bluetooth: L2CAP socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035454] Bluetooth: SCO socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.067957] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  9 07:32:06 AnotherMass kernel: [   33.067962] Bluetooth: BNEP filters: protocol multicast
Apr  9 07:32:06 AnotherMass kernel: [   33.067973] Bluetooth: BNEP socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106535] Bluetooth: RFCOMM TTY layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106554] Bluetooth: RFCOMM socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106565] Bluetooth: RFCOMM ver 1.11
Apr  9 07:32:06 AnotherMass kernel: [   33.217119] type=1400 audit(1428561126.880:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1049 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   33.217129] type=1400 audit(1428561126.880:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1049 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   33.217719] type=1400 audit(1428561126.880:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1049 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349340] type=1400 audit(1428561127.012:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349352] type=1400 audit(1428561127.012:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349357] type=1400 audit(1428561127.012:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349920] type=1400 audit(1428561127.012:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349925] type=1400 audit(1428561127.012:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.357589] type=1400 audit(1428561127.020:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1110 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.357600] type=1400 audit(1428561127.020:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1110 comm="apparmor_parser"
Apr  9 07:56:43 AnotherMass kernel: [ 1508.776034] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr  9 07:56:43 AnotherMass kernel: [ 1508.796485] JFS: nTxBlock = 8192, nTxLock = 65536
Apr  9 07:56:43 AnotherMass kernel: [ 1508.817581] NTFS driver 2.1.30 [Flags: R/O MODULE].
Apr  9 07:56:43 AnotherMass kernel: [ 1508.859071] QNX4 filesystem 0.2.3 registered.
Apr  9 07:56:43 AnotherMass kernel: [ 1508.897801] bio: create slab <bio-1> at 1
Apr  9 07:56:43 AnotherMass kernel: [ 1508.907200] Btrfs loaded
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592166] audit_printk_skb: 132 callbacks suppressed
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592171] type=1400 audit(1428562623.954:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=21296 comm="apparmor_parser"
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592179] type=1400 audit(1428562623.954:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=21296 comm="apparmor_parser"
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592734] type=1400 audit(1428562623.954:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=21296 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.113813] type=1400 audit(1428605063.410:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince" pid=9463 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.129066] type=1400 audit(1428605063.426:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=9463 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.131537] type=1400 audit(1428605063.430:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-previewer" pid=9463 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.144447] type=1400 audit(1428605063.442:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=9463 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.146185] type=1400 audit(1428605063.442:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=9463 comm="apparmor_parser"
Apr  9 19:44:23 AnotherMass kernel: [43948.156474] type=1400 audit(1428605063.454:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=9463 comm="apparmor_parser"
Apr 10 00:36:14 AnotherMass kernel: [61450.355091] perf samples too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Apr 10 07:55:27 AnotherMass kernel: [87790.491236] type=1400 audit(1428648927.423:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=6908 comm="apparmor_parser"
Apr 10 07:55:27 AnotherMass kernel: [87790.491248] type=1400 audit(1428648927.423:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=6908 comm="apparmor_parser"
Apr 10 07:55:27 AnotherMass kernel: [87790.496429] type=1400 audit(1428648927.427:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=6908 comm="apparmor_parser"
Apr 11 07:46:23 AnotherMass kernel: [173604.537657] type=1400 audit(1428734783.821:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=9267 comm="apparmor_parser"
Apr 11 07:46:23 AnotherMass kernel: [173604.537669] type=1400 audit(1428734783.821:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=9267 comm="apparmor_parser"
Apr 11 07:46:23 AnotherMass kernel: [173604.538311] type=1400 audit(1428734783.821:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=9267 comm="apparmor_parser"
Apr 12 07:51:46 AnotherMass kernel: [260284.398752] type=1400 audit(1428821506.459:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=14286 comm="apparmor_parser"
Apr 12 07:51:46 AnotherMass kernel: [260284.398764] type=1400 audit(1428821506.459:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=14286 comm="apparmor_parser"
Apr 12 07:51:46 AnotherMass kernel: [260284.399405] type=1400 audit(1428821506.459:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=14286 comm="apparmor_parser"
Apr 13 07:54:07 AnotherMass kernel: [346782.983228] type=1400 audit(1428908047.733:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=18508 comm="apparmor_parser"
Apr 13 07:54:07 AnotherMass kernel: [346782.983240] type=1400 audit(1428908047.733:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18508 comm="apparmor_parser"
Apr 13 07:54:07 AnotherMass kernel: [346782.983871] type=1400 audit(1428908047.733:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18508 comm="apparmor_parser"

```

---

### Post by superandyjamieson on 2015-04-15
**&#8203;**[COLOR=#000000]Here's the output from [/COLOR]**syslog**

```
Apr  8 07:38:46 AnotherMass postfix/pickup[24015]: A091E405A4: uid=0 from=<root>
Apr  8 07:38:46 AnotherMass postfix/cleanup[25883]: A091E405A4: message-id=<20150408063846.A091E405A4@AnotherMass>
Apr  8 07:38:46 AnotherMass postfix/qmgr[9381]: A091E405A4: from=<root@AnotherMass>, size=814, nrcpt=1 (queue active)
Apr  8 07:38:46 AnotherMass postfix/local[25892]: A091E405A4: to=<root@AnotherMass>, orig_to=<root>, relay=local, delay=0.08, delays=0.05/0.02/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Apr  8 07:38:46 AnotherMass postfix/qmgr[9381]: A091E405A4: removed
Apr  8 07:39:20 AnotherMass anacron[24768]: Job `cron.daily' terminated
Apr  8 07:39:20 AnotherMass anacron[24768]: Normal exit (1 job run)
Apr  8 07:40:12 AnotherMass afpd[25992]: AFP3.3 Login by user
Apr  8 07:40:12 AnotherMass afpd[25992]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 07:45:59 AnotherMass afpd[25992]: AFP logout by user
Apr  8 07:45:59 AnotherMass afpd[25992]: AFP statistics: 474.52 KB read, 2877925.38 KB written
Apr  8 07:45:59 AnotherMass afpd[25992]: done
Apr  8 08:17:01 AnotherMass CRON[27109]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 09:01:55 AnotherMass dhclient: DHCPREQUEST of 192.168.2.6 on eth0 to 192.168.2.1 port 67 (xid=0x2405df4b)
Apr  8 09:01:55 AnotherMass dhclient: DHCPACK of 192.168.2.6 from 192.168.2.1
Apr  8 09:01:55 AnotherMass dhclient: bound to 192.168.2.6 -- renewal in 42979 seconds.
Apr  8 09:17:01 AnotherMass CRON[28903]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 10:17:01 AnotherMass CRON[30698]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 11:17:01 AnotherMass CRON[32477]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 12:17:01 AnotherMass CRON[1954]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 13:17:01 AnotherMass CRON[4241]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 14:17:01 AnotherMass CRON[6061]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 15:17:01 AnotherMass CRON[7818]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 16:17:01 AnotherMass CRON[9592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 17:17:01 AnotherMass CRON[11381]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 18:02:13 AnotherMass afpd[12751]: AFP3.3 Login by user
Apr  8 18:02:13 AnotherMass afpd[12751]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 18:17:01 AnotherMass CRON[13257]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 18:32:38 AnotherMass afpd[13732]: AFP3.3 Login by user
Apr  8 18:32:38 AnotherMass afpd[13732]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 19:05:30 AnotherMass afpd[12751]: AFP logout by user
Apr  8 19:05:30 AnotherMass afpd[12751]: AFP statistics: 1016.01 KB read, 3554.72 KB written
Apr  8 19:05:30 AnotherMass afpd[12751]: done
Apr  8 19:08:45 AnotherMass afpd[13732]: AFP logout by user
Apr  8 19:08:45 AnotherMass afpd[13732]: AFP statistics: 6387136.65 KB read, 712169.29 KB written
Apr  8 19:08:45 AnotherMass afpd[13732]: done
Apr  8 19:12:52 AnotherMass afpd[15168]: AFP3.3 Login by user
Apr  8 19:12:52 AnotherMass afpd[15168]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 19:14:52 AnotherMass afpd[15300]: AFP3.3 Login by user
Apr  8 19:14:52 AnotherMass afpd[15300]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 19:17:01 AnotherMass CRON[15403]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 20:17:01 AnotherMass CRON[18359]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 20:23:52 AnotherMass afpd[15300]: AFP logout by user
Apr  8 20:23:52 AnotherMass afpd[15300]: AFP statistics: 6698827.58 KB read, 1562738.41 KB written
Apr  8 20:23:52 AnotherMass afpd[15300]: done
Apr  8 20:23:53 AnotherMass afpd[18693]: AFP3.3 Login by user
Apr  8 20:23:53 AnotherMass afpd[18693]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 20:58:14 AnotherMass dhclient: DHCPREQUEST of 192.168.2.6 on eth0 to 192.168.2.1 port 67 (xid=0x2405df4b)
Apr  8 20:58:14 AnotherMass dhclient: DHCPACK of 192.168.2.6 from 192.168.2.1
Apr  8 20:58:14 AnotherMass dhclient: bound to 192.168.2.6 -- renewal in 34383 seconds.
Apr  8 21:17:01 AnotherMass CRON[21173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 21:37:04 AnotherMass afpd[18693]: AFP logout by user
Apr  8 21:37:04 AnotherMass afpd[18693]: AFP statistics: 531644.35 KB read, 3019485.35 KB written
Apr  8 21:37:04 AnotherMass afpd[18693]: done
Apr  8 22:17:01 AnotherMass CRON[24177]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 22:37:34 AnotherMass afpd[25136]: AFP3.3 Login by user
Apr  8 22:37:34 AnotherMass afpd[25136]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  8 22:45:42 AnotherMass afpd[15168]: deletecurdir: error deleting .AppleDouble in "€"
Apr  8 23:01:45 AnotherMass kernel: [2847383.320470] radeon 0000:01:05.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Apr  8 23:01:45 AnotherMass kernel: [2847383.320485] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  8 23:01:45 AnotherMass kernel: [2847383.320509] pci 0000:00:00.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320512] pci 0000:00:00.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320518] pci 0000:00:01.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320520] pci 0000:00:01.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320528] radeon 0000:01:05.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320530] radeon 0000:01:05.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320536] pcieport 0000:00:06.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320559] ahci 0000:00:11.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320561] ahci 0000:00:11.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320570] ohci-pci 0000:00:12.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320572] ohci-pci 0000:00:12.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320580] ehci-pci 0000:00:12.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320582] ehci-pci 0000:00:12.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320590] ohci-pci 0000:00:13.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320591] ohci-pci 0000:00:13.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320599] ehci-pci 0000:00:13.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320601] ehci-pci 0000:00:13.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320609] piix4_smbus 0000:00:14.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320610] piix4_smbus 0000:00:14.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320618] pci 0000:00:14.3: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320619] pci 0000:00:14.3: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320627] pci 0000:00:14.4: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320629] pci 0000:00:14.4: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320639] ohci-pci 0000:00:16.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320641] ohci-pci 0000:00:16.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320648] ehci-pci 0000:00:16.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320650] ehci-pci 0000:00:16.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320658] pci 0000:00:18.0: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320660] pci 0000:00:18.0: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320664] pci 0000:00:18.1: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320666] pci 0000:00:18.1: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320670] amd64_edac 0000:00:18.2: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320672] amd64_edac 0000:00:18.2: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320677] k10temp 0000:00:18.3: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320679] k10temp 0000:00:18.3: using default PCI settings
Apr  8 23:01:45 AnotherMass kernel: [2847383.320683] pci 0000:00:18.4: no hotplug settings from platform
Apr  8 23:01:45 AnotherMass kernel: [2847383.320684] pci 0000:00:18.4: using default PCI settings
Apr  8 23:41:52 AnotherMass rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="866" x-info="http://www.rsyslog.com"] start
Apr  8 23:41:52 AnotherMass rsyslogd: rsyslogd's groupid changed to 103
Apr  8 23:41:52 AnotherMass rsyslogd: rsyslogd's userid changed to 101
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Linux version 3.13.0-48-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 (Ubuntu 3.13.0-48.80-generic 3.13.11-ckt16)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] KERNEL supported cpus:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Intel GenuineIntel
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   AMD AuthenticAMD
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Centaur CentaurHauls
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d7f8ffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7f9e000-0x00000000d7f9ffff] type 9
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fa0000-0x00000000d7fadfff] ACPI data
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fae000-0x00000000d7fdffff] ACPI NVS
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fe0000-0x00000000d7ffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000019fffffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] SMBIOS 2.6 present.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR default type: uncachable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   00000-9FFFF write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   A0000-EFFFF uncachable
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] MTRR variable ranges enabled:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   3 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   4 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   5 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   6 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   7 disabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] TOM2: 00000001a0000000 aka 6656M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Using GB pages for direct mapping
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19fe00000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x19fe00000-0x19fffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19c000000-0x19fdfffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x19c000000-0x19fdfffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x180000000-0x19bffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x180000000-0x19bffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xd7f8ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0xc0000000-0xd7dfffff] page 2M
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0xd7e00000-0xd7f8ffff] page 4k
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [mem 0x100000000-0x17fffffff] page 1G
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] RAMDISK: [mem 0x35a4e000-0x36d1efff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: RSDP 00000000000f8f50 000024 (v02 HP    )
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: XSDT 00000000d7fa0100 00007C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: FACP 00000000d7fa0290 0000F4 (v03 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: DSDT 00000000d7fa0620 006947 (v01 HP     ProLiant 00000006 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: FACS 00000000d7fae000 000040
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: APIC 00000000d7fa0390 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: MCFG 00000000d7fa0410 00003C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: SPMI 00000000d7fa0450 000041 (v05 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: OEMB 00000000d7fae040 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HPET 00000000d7fab4e0 000038 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: EINJ 00000000d7fab520 000130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: BERT 00000000d7fab6b0 000030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: ERST 00000000d7fab6e0 0001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HEST 00000000d7fab890 0000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: SSDT 00000000d7fab940 00052A (v01 HP     ProLiant 00000001 AMD  00000001)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No NUMA configuration found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000019fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   NODE_DATA [mem 0x19fff9000-0x19fffdfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199800000-ffff88019f5fffff] on node 0
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Zone ranges:
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal   [mem 0x100000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Movable zone start for each node
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Early memory node ranges
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00100000-0xd7f8ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   node   0: [mem 0x100000000-0x19fffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] On node 0 totalpages: 1539885
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32 zone: 13759 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   DMA32 zone: 880528 pages, LIFO batch:31
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal zone: 10240 pages used for memmap
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]   Normal zone: 655360 pages, LIFO batch:31
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] nr_irqs_gsi: 40
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e1fff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e2000-0x000fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f90000-0xd7f9dfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f9e000-0xd7f9ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fa0000-0xd7fadfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fae000-0xd7fdffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fe0000-0xd7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xff9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] e820: [mem 0xf0000000-0xff9fffff] available for PCI devices
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s82368 r8192 d24128 u524288
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] pcpu-alloc: s82368 r8192 d24128 u524288 alloc=1*2097152
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1515801
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Policy zone: Normal
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Checking aperture...
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Node 0: aperture @ f1ba000000 size 32 MB
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] This costs you 64 MB of RAM
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc000000-0xcfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Memory: 5895336K/6159540K available (7385K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 264204K reserved)
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Hierarchical RCU implementation.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] console [tty0] enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] allocated 24641536 bytes of page_cgroup
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] hpet clockevent registered
Apr  8 23:41:52 AnotherMass kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Apr  8 23:41:52 AnotherMass kernel: [    0.004000] tsc: Detected 2196.381 MHz processor
Apr  8 23:41:52 AnotherMass kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4392.76 BogoMIPS (lpj=8785524)
Apr  8 23:41:52 AnotherMass kernel: [    0.000067] pid_max: default: 32768 minimum: 301
Apr  8 23:41:52 AnotherMass kernel: [    0.000133] Security Framework initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.000184] AppArmor: AppArmor initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.000215] Yama: becoming mindful.
Apr  8 23:41:52 AnotherMass kernel: [    0.000916] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.004859] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.006717] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.006763] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.007154] Initializing cgroup subsys memory
Apr  8 23:41:52 AnotherMass kernel: [    0.007197] Initializing cgroup subsys devices
Apr  8 23:41:52 AnotherMass kernel: [    0.007230] Initializing cgroup subsys freezer
Apr  8 23:41:52 AnotherMass kernel: [    0.007262] Initializing cgroup subsys blkio
Apr  8 23:41:52 AnotherMass kernel: [    0.007293] Initializing cgroup subsys perf_event
Apr  8 23:41:52 AnotherMass kernel: [    0.007326] Initializing cgroup subsys hugetlb
Apr  8 23:41:52 AnotherMass kernel: [    0.008014] tseg: 0000000000
Apr  8 23:41:52 AnotherMass kernel: [    0.008022] CPU: Physical Processor ID: 0
Apr  8 23:41:52 AnotherMass kernel: [    0.008053] CPU: Processor Core ID: 0
Apr  8 23:41:52 AnotherMass kernel: [    0.008084] mce: CPU supports 6 MCE banks
Apr  8 23:41:52 AnotherMass kernel: [    0.008121] LVT offset 0 assigned for vector 0xf9
Apr  8 23:41:52 AnotherMass kernel: [    0.008155] process: using AMD E400 aware idle routine
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
Apr  8 23:41:52 AnotherMass kernel: [    0.008188] tlb_flushall_shift: 4
Apr  8 23:41:52 AnotherMass kernel: [    0.008342] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Apr  8 23:41:52 AnotherMass kernel: [    0.009921] ACPI: Core revision 20131115
Apr  8 23:41:52 AnotherMass kernel: [    0.012479] ACPI: All ACPI Tables successfully acquired
Apr  8 23:41:52 AnotherMass kernel: [    0.014380] ftrace: allocating 28562 entries in 112 pages
Apr  8 23:41:52 AnotherMass kernel: [    0.029082] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  8 23:41:52 AnotherMass kernel: [    0.068789] smpboot: CPU0: AMD Turion(tm) II Neo N54L Dual-Core Processor (fam: 10, model: 06, stepping: 03)
Apr  8 23:41:52 AnotherMass kernel: [    0.175446] Performance Events: AMD PMU driver.
Apr  8 23:41:52 AnotherMass kernel: [    0.175508] ... version:                0
Apr  8 23:41:52 AnotherMass kernel: [    0.175539] ... bit width:              48
Apr  8 23:41:52 AnotherMass kernel: [    0.175569] ... generic registers:      4
Apr  8 23:41:52 AnotherMass kernel: [    0.175600] ... value mask:             0000ffffffffffff
Apr  8 23:41:52 AnotherMass kernel: [    0.175631] ... max period:             00007fffffffffff
Apr  8 23:41:52 AnotherMass kernel: [    0.175662] ... fixed-purpose events:   0
Apr  8 23:41:52 AnotherMass kernel: [    0.175693] ... event mask:             000000000000000f
Apr  8 23:41:52 AnotherMass kernel: [    0.177481] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  8 23:41:52 AnotherMass kernel: [    0.177608] x86: Booting SMP configuration:
Apr  8 23:41:52 AnotherMass kernel: [    0.177640] .... node  #0, CPUs:      #1
Apr  8 23:41:52 AnotherMass kernel: [    0.190774] x86: Booted up 1 node, 2 CPUs
Apr  8 23:41:52 AnotherMass kernel: [    0.190814] process: System has AMD C1E enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.190824] process: Switch to broadcast mode on CPU1
Apr  8 23:41:52 AnotherMass kernel: [    0.190898] smpboot: Total of 2 processors activated (8785.52 BogoMIPS)
Apr  8 23:41:52 AnotherMass kernel: [    0.191624] process: Switch to broadcast mode on CPU0
Apr  8 23:41:52 AnotherMass kernel: [    0.191798] devtmpfs: initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.197367] EVM: security.selinux
Apr  8 23:41:52 AnotherMass kernel: [    0.197398] EVM: security.SMACK64
Apr  8 23:41:52 AnotherMass kernel: [    0.197429] EVM: security.ima
Apr  8 23:41:52 AnotherMass kernel: [    0.197459] EVM: security.capability
Apr  8 23:41:52 AnotherMass kernel: [    0.198093] PM: Registering ACPI NVS region [mem 0xd7fae000-0xd7fdffff] (204800 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.199990] pinctrl core: initialized pinctrl subsystem
Apr  8 23:41:52 AnotherMass kernel: [    0.200109] regulator-dummy: no parameters
Apr  8 23:41:52 AnotherMass kernel: [    0.200170] RTC time: 22:41:39, date: 04/08/15
Apr  8 23:41:52 AnotherMass kernel: [    0.200253] NET: Registered protocol family 16
Apr  8 23:41:52 AnotherMass kernel: [    0.200422] cpuidle: using governor ladder
Apr  8 23:41:52 AnotherMass kernel: [    0.200454] cpuidle: using governor menu
Apr  8 23:41:52 AnotherMass kernel: [    0.200491] node 0 link 0: io port [1000, ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200494] TOM: 00000000e0000000 aka 3584M
Apr  8 23:41:52 AnotherMass kernel: [    0.200527] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200530] node 0 link 0: mmio [a0000, bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200533] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200536] node 0 link 0: mmio [f8000000, fe6fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200538] node 0 link 0: mmio [fe700000, fe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200540] node 0 link 0: mmio [fe900000, ffdfffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200541] TOM2: 00000001a0000000 aka 6656M
Apr  8 23:41:52 AnotherMass kernel: [    0.200575] bus: [bus 00-1f] on node 0 link 0
Apr  8 23:41:52 AnotherMass kernel: [    0.200577] bus: 00 [io  0x0000-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200578] bus: 00 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200580] bus: 00 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.200581] bus: 00 [mem 0x1a0000000-0xfcffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.201342] ACPI: bus type PCI registered
Apr  8 23:41:52 AnotherMass kernel: [    0.201376] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  8 23:41:52 AnotherMass kernel: [    0.201478] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  8 23:41:52 AnotherMass kernel: [    0.201515] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  8 23:41:52 AnotherMass kernel: [    0.212989] PCI: Using configuration type 1 for base access
Apr  8 23:41:52 AnotherMass kernel: [    0.213202] mtrr: your CPUs had inconsistent variable MTRR settings
Apr  8 23:41:52 AnotherMass kernel: [    0.213237] mtrr: probably your BIOS does not setup all CPUs.
Apr  8 23:41:52 AnotherMass kernel: [    0.213268] mtrr: corrected configuration.
Apr  8 23:41:52 AnotherMass kernel: [    0.214302] bio: create slab <bio-0> at 0
Apr  8 23:41:52 AnotherMass kernel: [    0.214644] ACPI: Added _OSI(Module Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.214680] ACPI: Added _OSI(Processor Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.214712] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  8 23:41:52 AnotherMass kernel: [    0.214744] ACPI: Added _OSI(Processor Aggregator Device)
Apr  8 23:41:52 AnotherMass kernel: [    0.216399] ACPI: Executed 2 blocks of module-level executable AML code
Apr  8 23:41:52 AnotherMass kernel: [    0.218320] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.218952] ACPI: OEMN 00000000d7faaeb0 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.219255] ACPI: Dynamic OEM Table Load:
Apr  8 23:41:52 AnotherMass kernel: [    0.219341] ACPI: OEMN           (null) 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  8 23:41:52 AnotherMass kernel: [    0.223007] \_SB_:_OSC evaluation returned wrong type
Apr  8 23:41:52 AnotherMass kernel: [    0.223012] _OSC request data:1 1f 
Apr  8 23:41:52 AnotherMass kernel: [    0.223169] ACPI: Interpreter enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.223212] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223302] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223392] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
Apr  8 23:41:52 AnotherMass kernel: [    0.223489] ACPI: (supports S0 S4 S5)
Apr  8 23:41:52 AnotherMass kernel: [    0.223520] ACPI: Using IOAPIC for interrupt routing
Apr  8 23:41:52 AnotherMass kernel: [    0.223739] HEST: Table parsing has been initialized.
Apr  8 23:41:52 AnotherMass kernel: [    0.223773] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  8 23:41:52 AnotherMass kernel: [    0.223911] ACPI: No dock devices found.
Apr  8 23:41:52 AnotherMass kernel: [    0.228498] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  8 23:41:52 AnotherMass kernel: [    0.228539] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  8 23:41:52 AnotherMass kernel: [    0.228835] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Apr  8 23:41:52 AnotherMass kernel: [    0.229316] acpi PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.229356] acpi PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xfebfffff] ignored
Apr  8 23:41:52 AnotherMass kernel: [    0.229399] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000dffff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff])
Apr  8 23:41:52 AnotherMass kernel: [    0.229658] PCI host bridge to bus 0000:00
Apr  8 23:41:52 AnotherMass kernel: [    0.229691] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229726] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.229762] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229796] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229831] pci_bus 0000:00: root bus resource [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229865] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.229908] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.230028] pci 0000:00:01.0: [103c:9602] type 01 class 0x060400
Apr  8 23:41:52 AnotherMass kernel: [    0.230128] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
Apr  8 23:41:52 AnotherMass kernel: [    0.230165] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  8 23:41:52 AnotherMass kernel: [    0.230216] pci 0000:00:06.0: System wakeup disabled by ACPI
Apr  8 23:41:52 AnotherMass kernel: [    0.230303] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Apr  8 23:41:52 AnotherMass kernel: [    0.230324] pci 0000:00:11.0: reg 0x10: [io  0xd000-0xd007]
Apr  8 23:41:52 AnotherMass kernel: [    0.230334] pci 0000:00:11.0: reg 0x14: [io  0xc000-0xc003]
Apr  8 23:41:52 AnotherMass kernel: [    0.230344] pci 0000:00:11.0: reg 0x18: [io  0xb000-0xb007]
Apr  8 23:41:52 AnotherMass kernel: [    0.230353] pci 0000:00:11.0: reg 0x1c: [io  0xa000-0xa003]
Apr  8 23:41:52 AnotherMass kernel: [    0.230362] pci 0000:00:11.0: reg 0x20: [io  0x9000-0x900f]
Apr  8 23:41:52 AnotherMass kernel: [    0.230372] pci 0000:00:11.0: reg 0x24: [mem 0xfe6ffc00-0xfe6fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230493] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.230507] pci 0000:00:12.0: reg 0x10: [mem 0xfe6fe000-0xfe6fefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230631] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.230650] pci 0000:00:12.2: reg 0x10: [mem 0xfe6ff800-0xfe6ff8ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230728] pci 0000:00:12.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.230730] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.230811] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.230828] pci 0000:00:13.0: reg 0x10: [mem 0xfe6fd000-0xfe6fdfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.230952] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.230970] pci 0000:00:13.2: reg 0x10: [mem 0xfe6ff400-0xfe6ff4ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231049] pci 0000:00:13.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.231050] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.231133] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Apr  8 23:41:52 AnotherMass kernel: [    0.231259] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Apr  8 23:41:52 AnotherMass kernel: [    0.231386] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Apr  8 23:41:52 AnotherMass kernel: [    0.231461] pci 0000:00:14.4: System wakeup disabled by ACPI
Apr  8 23:41:52 AnotherMass kernel: [    0.231525] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
Apr  8 23:41:52 AnotherMass kernel: [    0.231539] pci 0000:00:16.0: reg 0x10: [mem 0xfe6fc000-0xfe6fcfff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231662] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
Apr  8 23:41:52 AnotherMass kernel: [    0.231680] pci 0000:00:16.2: reg 0x10: [mem 0xfe6ff000-0xfe6ff0ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.231760] pci 0000:00:16.2: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.231761] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr  8 23:41:52 AnotherMass kernel: [    0.231840] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.231912] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.231980] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232047] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232117] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Apr  8 23:41:52 AnotherMass kernel: [    0.232238] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
Apr  8 23:41:52 AnotherMass kernel: [    0.232247] pci 0000:01:05.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.232252] pci 0000:01:05.0: reg 0x14: [io  0xe000-0xe0ff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232257] pci 0000:01:05.0: reg 0x18: [mem 0xfe8f0000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232268] pci 0000:01:05.0: reg 0x24: [mem 0xfe700000-0xfe7fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232287] pci 0000:01:05.0: supports D1 D2
Apr  8 23:41:52 AnotherMass kernel: [    0.232348] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  8 23:41:52 AnotherMass kernel: [    0.232382] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232385] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.232389] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.232451] pci 0000:02:00.0: [14e4:165b] type 00 class 0x020000
Apr  8 23:41:52 AnotherMass kernel: [    0.232470] pci 0000:02:00.0: reg 0x10: [mem 0xfe9f0000-0xfe9fffff 64bit]
Apr  8 23:41:52 AnotherMass kernel: [    0.232574] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  8 23:41:52 AnotherMass kernel: [    0.238882] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  8 23:41:52 AnotherMass kernel: [    0.238925] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.239024] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239064] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239066] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239069] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239071] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239073] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
Apr  8 23:41:52 AnotherMass kernel: [    0.239423] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.239761] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240096] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240430] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.240750] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241059] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241368] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.241677] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr  8 23:41:52 AnotherMass kernel: [    0.242076] ACPI: Enabled 4 GPEs in block 00 to 1F
Apr  8 23:41:52 AnotherMass kernel: [    0.242170] ACPI: \_SB_.PCI0: notify handler is installed
Apr  8 23:41:52 AnotherMass kernel: [    0.242204] Found 1 acpi root devices
Apr  8 23:41:52 AnotherMass kernel: [    0.242378] vgaarb: setting as boot device: PCI:0000:01:05.0
Apr  8 23:41:52 AnotherMass kernel: [    0.242411] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Apr  8 23:41:52 AnotherMass kernel: [    0.242446] vgaarb: loaded
Apr  8 23:41:52 AnotherMass kernel: [    0.242477] vgaarb: bridge control possible 0000:01:05.0
Apr  8 23:41:52 AnotherMass kernel: [    0.242704] SCSI subsystem initialized
Apr  8 23:41:52 AnotherMass kernel: [    0.242827] libata version 3.00 loaded.
Apr  8 23:41:52 AnotherMass kernel: [    0.242851] ACPI: bus type USB registered
Apr  8 23:41:52 AnotherMass kernel: [    0.242903] usbcore: registered new interface driver usbfs
Apr  8 23:41:52 AnotherMass kernel: [    0.242942] usbcore: registered new interface driver hub
Apr  8 23:41:52 AnotherMass kernel: [    0.243091] usbcore: registered new device driver usb
Apr  8 23:41:52 AnotherMass kernel: [    0.243333] PCI: Using ACPI for IRQ routing
Apr  8 23:41:52 AnotherMass kernel: [    0.251507] PCI: pci_cache_line_size set to 64 bytes
Apr  8 23:41:52 AnotherMass kernel: [    0.251553] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.251556] e820: reserve RAM buffer [mem 0xd7f90000-0xd7ffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.251665] NetLabel: Initializing
Apr  8 23:41:52 AnotherMass kernel: [    0.251696] NetLabel:  domain hash size = 128
Apr  8 23:41:52 AnotherMass kernel: [    0.251727] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  8 23:41:52 AnotherMass kernel: [    0.251771] NetLabel:  unlabeled traffic allowed by default
Apr  8 23:41:52 AnotherMass kernel: [    0.251922] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  8 23:41:52 AnotherMass kernel: [    0.252062] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr  8 23:41:52 AnotherMass kernel: [    0.254151] Switched to clocksource hpet
Apr  8 23:41:52 AnotherMass kernel: [    0.260344] AppArmor: AppArmor Filesystem Enabled
Apr  8 23:41:52 AnotherMass kernel: [    0.260417] pnp: PnP ACPI init
Apr  8 23:41:52 AnotherMass kernel: [    0.260465] ACPI: bus type PNP registered
Apr  8 23:41:52 AnotherMass kernel: [    0.260713] system 00:00: [mem 0xd8000000-0xdfffffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.260748] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260808] pnp 00:01: [dma 4]
Apr  8 23:41:52 AnotherMass kernel: [    0.260833] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260872] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260931] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.260961] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261002] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261096] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261130] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261163] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.261340] system 00:07: [io  0x04d0-0x04d1] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261373] system 00:07: [io  0x040b] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261405] system 00:07: [io  0x04d6] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261437] system 00:07: [io  0x0c00-0x0c01] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261470] system 00:07: [io  0x0c14] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261502] system 00:07: [io  0x0c50-0x0c51] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261534] system 00:07: [io  0x0c52] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261566] system 00:07: [io  0x0c6c] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261598] system 00:07: [io  0x0c6f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261630] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261662] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261695] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261727] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261759] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261792] system 00:07: [io  0x0800-0x089f] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261824] system 00:07: [io  0x0b00-0x0b1f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261857] system 00:07: [io  0x0b20-0x0b3f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261889] system 00:07: [io  0x0900-0x090f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261922] system 00:07: [io  0x0910-0x091f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261955] system 00:07: [io  0xfe00-0xfefe] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.261988] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262020] system 00:07: [mem 0xfec10000-0xfec1001f] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262053] system 00:07: [mem 0xfed80000-0xfed80fff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262087] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262167] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262201] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262321] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262355] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262388] system 00:09: [mem 0x00100000-0xd7ffffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262421] system 00:09: [mem 0xfec00000-0xffffffff] could not be reserved
Apr  8 23:41:52 AnotherMass kernel: [    0.262454] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr  8 23:41:52 AnotherMass kernel: [    0.262546] pnp: PnP ACPI: found 10 devices
Apr  8 23:41:52 AnotherMass kernel: [    0.262577] ACPI: bus type PNP unregistered
Apr  8 23:41:52 AnotherMass kernel: [    0.270959] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  8 23:41:52 AnotherMass kernel: [    0.270995] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271030] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271065] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.271108] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  8 23:41:52 AnotherMass kernel: [    0.271141] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271179] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  8 23:41:52 AnotherMass kernel: [    0.271223] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.271226] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271228] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271230] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271232] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271234] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271236] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271239] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  8 23:41:52 AnotherMass kernel: [    0.271241] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271244] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Apr  8 23:41:52 AnotherMass kernel: [    0.271246] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271248] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271250] pci_bus 0000:03: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271252] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xffffffff]
Apr  8 23:41:52 AnotherMass kernel: [    0.271294] NET: Registered protocol family 2
Apr  8 23:41:52 AnotherMass kernel: [    0.271605] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.271973] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.272518] TCP: Hash tables configured (established 65536 bind 65536)
Apr  8 23:41:52 AnotherMass kernel: [    0.272644] TCP: reno registered
Apr  8 23:41:52 AnotherMass kernel: [    0.272689] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.272814] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    0.273041] NET: Registered protocol family 1
Apr  8 23:41:52 AnotherMass kernel: [    0.273089] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Apr  8 23:41:52 AnotherMass kernel: [    1.250125] pci 0000:01:05.0: Video device with shadowed ROM
Apr  8 23:41:52 AnotherMass kernel: [    1.250134] PCI: CLS 64 bytes, default 64
Apr  8 23:41:52 AnotherMass kernel: [    1.250205] Trying to unpack rootfs image as initramfs...
Apr  8 23:41:52 AnotherMass kernel: [    1.625545] Freeing initrd memory: 19268K (ffff880035a4e000 - ffff880036d1f000)
Apr  8 23:41:52 AnotherMass kernel: [    1.625806] PCI-DMA: Disabling AGP.
Apr  8 23:41:52 AnotherMass kernel: [    1.625950] PCI-DMA: aperture base @ cc000000 size 65536 KB
Apr  8 23:41:52 AnotherMass kernel: [    1.625982] PCI-DMA: using GART IOMMU.
Apr  8 23:41:52 AnotherMass kernel: [    1.626015] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr  8 23:41:52 AnotherMass kernel: [    1.630263] LVT offset 1 assigned for vector 0x400
Apr  8 23:41:52 AnotherMass kernel: [    1.630310] IBS: LVT offset 1 assigned
Apr  8 23:41:52 AnotherMass kernel: [    1.630378] perf: AMD IBS detected (0x0000001f)
Apr  8 23:41:52 AnotherMass kernel: [    1.630474] microcode: CPU0: patch_level=0x010000c8
Apr  8 23:41:52 AnotherMass kernel: [    1.630515] microcode: CPU1: patch_level=0x010000c8
Apr  8 23:41:52 AnotherMass kernel: [    1.630641] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  8 23:41:52 AnotherMass kernel: [    1.630676] Scanning for low memory corruption every 60 seconds
Apr  8 23:41:52 AnotherMass kernel: [    1.631023] Initialise system trusted keyring
Apr  8 23:41:52 AnotherMass kernel: [    1.631109] audit: initializing netlink socket (disabled)
Apr  8 23:41:52 AnotherMass kernel: [    1.631154] type=2000 audit(1428532900.524:1): initialized
Apr  8 23:41:52 AnotherMass kernel: [    1.664697] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  8 23:41:52 AnotherMass kernel: [    1.666415] zbud: loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.666752] VFS: Disk quotas dquot_6.5.2
Apr  8 23:41:52 AnotherMass kernel: [    1.666846] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  8 23:41:52 AnotherMass kernel: [    1.667529] fuse init (API version 7.22)
Apr  8 23:41:52 AnotherMass kernel: [    1.667764] msgmni has been set to 11680
Apr  8 23:41:52 AnotherMass kernel: [    1.667873] Key type big_key registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668492] Key type asymmetric registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668529] Asymmetric key parser 'x509' registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668644] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Apr  8 23:41:52 AnotherMass kernel: [    1.668731] io scheduler noop registered
Apr  8 23:41:52 AnotherMass kernel: [    1.668765] io scheduler deadline registered (default)
Apr  8 23:41:52 AnotherMass kernel: [    1.668823] io scheduler cfq registered
Apr  8 23:41:52 AnotherMass kernel: [    1.669674] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    1.669752] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
Apr  8 23:41:52 AnotherMass kernel: [    1.669790] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Apr  8 23:41:52 AnotherMass kernel: [    1.669823] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.669835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  8 23:41:52 AnotherMass kernel: [    1.669879] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  8 23:41:52 AnotherMass kernel: [    1.669960] ipmi message handler version 39.2
Apr  8 23:41:52 AnotherMass kernel: [    1.670065] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr  8 23:41:52 AnotherMass kernel: [    1.670107] ACPI: Power Button [PWRB]
Apr  8 23:41:52 AnotherMass kernel: [    1.670174] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  8 23:41:52 AnotherMass kernel: [    1.670210] ACPI: Power Button [PWRF]
Apr  8 23:41:52 AnotherMass kernel: [    1.670313] ACPI: processor limited to max C-state 1
Apr  8 23:41:52 AnotherMass kernel: [    1.670575] ERST: Failed to get Error Log Address Range.
Apr  8 23:41:52 AnotherMass kernel: [    1.685666] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
Apr  8 23:41:52 AnotherMass kernel: [    1.685802] GHES: APEI firmware first mode is enabled by WHEA _OSC.
Apr  8 23:41:52 AnotherMass kernel: [    1.686033] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  8 23:41:52 AnotherMass kernel: [    1.688048] Linux agpgart interface v0.103
Apr  8 23:41:52 AnotherMass kernel: [    1.689945] brd: module loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.691303] loop: module loaded
Apr  8 23:41:52 AnotherMass kernel: [    1.691737] libphy: Fixed MDIO Bus: probed
Apr  8 23:41:52 AnotherMass kernel: [    1.691861] tun: Universal TUN/TAP device driver, 1.6
Apr  8 23:41:52 AnotherMass kernel: [    1.691896] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  8 23:41:52 AnotherMass kernel: [    1.692095] PPP generic driver version 2.4.2
Apr  8 23:41:52 AnotherMass kernel: [    1.692221] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  8 23:41:52 AnotherMass kernel: [    1.692262] ehci-pci: EHCI PCI platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.692448] QUIRK: Enable AMD PLL fix
Apr  8 23:41:52 AnotherMass kernel: [    1.692471] ehci-pci 0000:00:12.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.692507] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr  8 23:41:52 AnotherMass kernel: [    1.692545] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.692589] ehci-pci 0000:00:12.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.692666] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe6ff800
Apr  8 23:41:52 AnotherMass kernel: [    1.701543] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.701665] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.701699] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.701733] usb usb1: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.701765] usb usb1: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.701797] usb usb1: SerialNumber: 0000:00:12.2
Apr  8 23:41:52 AnotherMass kernel: [    1.702000] hub 1-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.702037] hub 1-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.702348] ehci-pci 0000:00:13.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.702385] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr  8 23:41:52 AnotherMass kernel: [    1.702421] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.702466] ehci-pci 0000:00:13.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.702529] ehci-pci 0000:00:13.2: irq 17, io mem 0xfe6ff400
Apr  8 23:41:52 AnotherMass kernel: [    1.713542] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.713648] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.713682] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.713719] usb usb2: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.713753] usb usb2: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.713786] usb usb2: SerialNumber: 0000:00:13.2
Apr  8 23:41:52 AnotherMass kernel: [    1.714011] hub 2-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.714050] hub 2-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.714381] ehci-pci 0000:00:16.2: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.714419] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr  8 23:41:52 AnotherMass kernel: [    1.714460] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  8 23:41:52 AnotherMass kernel: [    1.714509] ehci-pci 0000:00:16.2: debug port 1
Apr  8 23:41:52 AnotherMass kernel: [    1.714579] ehci-pci 0000:00:16.2: irq 17, io mem 0xfe6ff000
Apr  8 23:41:52 AnotherMass kernel: [    1.725526] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr  8 23:41:52 AnotherMass kernel: [    1.725617] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Apr  8 23:41:52 AnotherMass kernel: [    1.725650] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.725685] usb usb3: Product: EHCI Host Controller
Apr  8 23:41:52 AnotherMass kernel: [    1.725716] usb usb3: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.725748] usb usb3: SerialNumber: 0000:00:16.2
Apr  8 23:41:52 AnotherMass kernel: [    1.725949] hub 3-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.725985] hub 3-0:1.0: 4 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.726129] ehci-platform: EHCI generic platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726204] ohci-pci: OHCI PCI platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.726395] ohci-pci 0000:00:12.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.726432] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr  8 23:41:52 AnotherMass kernel: [    1.726492] ohci-pci 0000:00:12.0: irq 18, io mem 0xfe6fe000
Apr  8 23:41:52 AnotherMass kernel: [    1.785534] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.785572] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.785606] usb usb4: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.785639] usb usb4: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.785670] usb usb4: SerialNumber: 0000:00:12.0
Apr  8 23:41:52 AnotherMass kernel: [    1.785874] hub 4-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.785913] hub 4-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.786200] ohci-pci 0000:00:13.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.786237] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr  8 23:41:52 AnotherMass kernel: [    1.786286] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe6fd000
Apr  8 23:41:52 AnotherMass kernel: [    1.845506] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.845544] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.845579] usb usb5: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.845610] usb usb5: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.845642] usb usb5: SerialNumber: 0000:00:13.0
Apr  8 23:41:52 AnotherMass kernel: [    1.845845] hub 5-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.845885] hub 5-0:1.0: 5 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.846166] ohci-pci 0000:00:16.0: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.846204] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 6
Apr  8 23:41:52 AnotherMass kernel: [    1.846254] ohci-pci 0000:00:16.0: irq 18, io mem 0xfe6fc000
Apr  8 23:41:52 AnotherMass kernel: [    1.905484] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Apr  8 23:41:52 AnotherMass kernel: [    1.905523] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  8 23:41:52 AnotherMass kernel: [    1.905558] usb usb6: Product: OHCI PCI host controller
Apr  8 23:41:52 AnotherMass kernel: [    1.905590] usb usb6: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  8 23:41:52 AnotherMass kernel: [    1.905622] usb usb6: SerialNumber: 0000:00:16.0
Apr  8 23:41:52 AnotherMass kernel: [    1.905839] hub 6-0:1.0: USB hub found
Apr  8 23:41:52 AnotherMass kernel: [    1.905881] hub 6-0:1.0: 4 ports detected
Apr  8 23:41:52 AnotherMass kernel: [    1.906018] ohci-platform: OHCI generic platform driver
Apr  8 23:41:52 AnotherMass kernel: [    1.906061] uhci_hcd: USB Universal Host Controller Interface driver
Apr  8 23:41:52 AnotherMass kernel: [    1.906154] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr  8 23:41:52 AnotherMass kernel: [    2.629042] tsc: Refined TSC clocksource calibration: 2196.341 MHz
Apr  8 23:41:52 AnotherMass kernel: [    2.927855] i8042: No controller found
Apr  8 23:41:52 AnotherMass kernel: [    2.928142] mousedev: PS/2 mouse device common for all mice
Apr  8 23:41:52 AnotherMass kernel: [    2.928359] rtc_cmos 00:02: RTC can wake from S4
Apr  8 23:41:52 AnotherMass kernel: [    2.928547] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Apr  8 23:41:52 AnotherMass kernel: [    2.928607] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  8 23:41:52 AnotherMass kernel: [    2.928723] device-mapper: uevent: version 1.0.3
Apr  8 23:41:52 AnotherMass kernel: [    2.928895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Apr  8 23:41:52 AnotherMass kernel: [    2.928953] ledtrig-cpu: registered to indicate activity on CPUs
Apr  8 23:41:52 AnotherMass kernel: [    2.929109] TCP: cubic registered
Apr  8 23:41:52 AnotherMass kernel: [    2.929247] NET: Registered protocol family 10
Apr  8 23:41:52 AnotherMass kernel: [    2.929469] NET: Registered protocol family 17
Apr  8 23:41:52 AnotherMass kernel: [    2.929513] Key type dns_resolver registered
Apr  8 23:41:52 AnotherMass kernel: [    2.929868] Loading compiled-in X.509 certificates
Apr  8 23:41:52 AnotherMass kernel: [    2.931146] Loaded X.509 cert 'Magrathea: Glacier signing key: 4eb2de249917cbf39cb85692e54cebade594d680'
Apr  8 23:41:52 AnotherMass kernel: [    2.931228] registered taskstats version 1
Apr  8 23:41:52 AnotherMass kernel: [    2.933921] Key type trusted registered
Apr  8 23:41:52 AnotherMass kernel: [    2.938733] Key type encrypted registered
Apr  8 23:41:52 AnotherMass kernel: [    2.938776] AppArmor: AppArmor sha1 policy hashing enabled
Apr  8 23:41:52 AnotherMass kernel: [    2.938814] IMA: No TPM chip found, activating TPM-bypass!
Apr  8 23:41:52 AnotherMass kernel: [    2.939346] regulator-dummy: disabling
Apr  8 23:41:52 AnotherMass kernel: [    2.939444]   Magic number: 11:56:704
Apr  8 23:41:52 AnotherMass kernel: [    2.939534] event_source cpu: hash matches
Apr  8 23:41:52 AnotherMass kernel: [    2.939611]  cpu: hash matches
Apr  8 23:41:52 AnotherMass kernel: [    2.939684] rtc_cmos 00:02: setting system clock to 2015-04-08 22:41:42 UTC (1428532902)
Apr  8 23:41:52 AnotherMass kernel: [    2.939911] acpi-cpufreq: overriding BIOS provided _PSD data
Apr  8 23:41:52 AnotherMass kernel: [    2.940025] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  8 23:41:52 AnotherMass kernel: [    2.940057] EDD information not available.
Apr  8 23:41:52 AnotherMass kernel: [    2.940122] PM: Hibernation image not present or could not be loaded.
Apr  8 23:41:52 AnotherMass kernel: [    2.941950] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Apr  8 23:41:52 AnotherMass kernel: [    2.942029] Write protecting the kernel read-only data: 12288k
Apr  8 23:41:52 AnotherMass kernel: [    2.944793] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
Apr  8 23:41:52 AnotherMass kernel: [    2.947148] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
Apr  8 23:41:52 AnotherMass kernel: [    2.968074] systemd-udevd[103]: starting version 204
Apr  8 23:41:52 AnotherMass kernel: [    2.987058] pps_core: LinuxPPS API ver. 1 registered
Apr  8 23:41:52 AnotherMass kernel: [    2.987104] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Apr  8 23:41:52 AnotherMass kernel: [    2.988719] PTP clock support registered
Apr  8 23:41:52 AnotherMass kernel: [    2.995380] md: linear personality registered for level -1
Apr  8 23:41:52 AnotherMass kernel: [    2.996298] ahci 0000:00:11.0: version 3.0
Apr  8 23:41:52 AnotherMass kernel: [    2.996506] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    2.996617] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Apr  8 23:41:52 AnotherMass kernel: [    2.996657] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
Apr  8 23:41:52 AnotherMass kernel: [    2.997876] scsi0 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998000] scsi1 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998093] scsi2 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998185] scsi3 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998747] scsi4 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998837] scsi5 : ahci
Apr  8 23:41:52 AnotherMass kernel: [    2.998984] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999027] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999068] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999108] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999709] ata5: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff00 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    2.999746] ata6: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff80 irq 41
Apr  8 23:41:52 AnotherMass kernel: [    3.002621] md: multipath personality registered for level -4
Apr  8 23:41:52 AnotherMass kernel: [    3.008105] md: raid0 personality registered for level 0
Apr  8 23:41:52 AnotherMass kernel: [    3.008906] tg3.c:v3.134 (Sep 16, 2013)
Apr  8 23:41:52 AnotherMass kernel: [    3.013095] md: raid1 personality registered for level 1
Apr  8 23:41:52 AnotherMass kernel: [    3.084822] raid6: sse2x1    3072 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.152785] raid6: sse2x2    4612 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.220743] raid6: sse2x4    5533 MB/s
Apr  8 23:41:52 AnotherMass kernel: [    3.220777] raid6: using algorithm sse2x4 (5533 MB/s)
Apr  8 23:41:52 AnotherMass kernel: [    3.220812] raid6: using intx1 recovery algorithm
Apr  8 23:41:52 AnotherMass kernel: [    3.222668] xor: measuring software checksum speed
Apr  8 23:41:52 AnotherMass kernel: [    3.260713]    prefetch64-sse:  8984.000 MB/sec
Apr  8 23:41:52 AnotherMass kernel: [    3.300693]    generic_sse:  8418.000 MB/sec
Apr  8 23:41:52 AnotherMass kernel: [    3.300727] xor: using function: prefetch64-sse (8984.000 MB/sec)
Apr  8 23:41:52 AnotherMass kernel: [    3.302372] async_tx: api initialized (async)
Apr  8 23:41:52 AnotherMass kernel: [    3.311135] md: raid6 personality registered for level 6
Apr  8 23:41:52 AnotherMass kernel: [    3.311170] md: raid5 personality registered for level 5
Apr  8 23:41:52 AnotherMass kernel: [    3.311202] md: raid4 personality registered for level 4
Apr  8 23:41:52 AnotherMass kernel: [    3.319858] md: raid10 personality registered for level 10
Apr  8 23:41:52 AnotherMass kernel: [    3.328772] ata5: SATA link down (SStatus 0 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.357838] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 38:ea:a7:a3:2a:32
Apr  8 23:41:52 AnotherMass kernel: [    3.357887] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Apr  8 23:41:52 AnotherMass kernel: [    3.357925] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  8 23:41:52 AnotherMass kernel: [    3.357960] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  8 23:41:52 AnotherMass kernel: [    3.360759] usb 4-2: new low-speed USB device number 2 using ohci-pci
Apr  8 23:41:52 AnotherMass kernel: [    3.496677] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.497320] ata1.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.497359] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.498021] ata1.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.498383] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.498739] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.498777] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.498840] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.499005] sd 0:0:0:0: [sda] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.499054] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.499099] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.504672] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.504738] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.504807] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.505208] ata6.00: ATA-9: SanDisk SDSSDRC032G, 3.0.0, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505254] ata6.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr  8 23:41:52 AnotherMass kernel: [    3.505356] ata3.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505397] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.505497] ata4.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.505535] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.506011] ata3.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.506192] ata6.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.506249] ata4.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.508656] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 23:41:52 AnotherMass kernel: [    3.509268] ata2.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.509306] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  8 23:41:52 AnotherMass kernel: [    3.509938] ata2.00: configured for UDMA/133
Apr  8 23:41:52 AnotherMass kernel: [    3.510232] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.510479] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.510515] sd 1:0:0:0: [sdb] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.510575] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.510703] sd 1:0:0:0: [sdb] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.510742] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.510765] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.510776] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.510905] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.510941] sd 2:0:0:0: [sdc] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.511001] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.511084] sd 2:0:0:0: [sdc] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.511124] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.511145] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.511431] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.511591] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.511608] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.511659] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Apr  8 23:41:52 AnotherMass kernel: [    3.511775] scsi 5:0:0:0: Direct-Access     ATA      SanDisk SDSSDRC0 3.0. PQ: 0 ANSI: 5
Apr  8 23:41:52 AnotherMass kernel: [    3.511924] sd 5:0:0:0: [sde] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
Apr  8 23:41:52 AnotherMass kernel: [    3.511970] sd 3:0:0:0: [sdd] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.512006] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.512029] sd 3:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.512050] sd 5:0:0:0: [sde] Write Protect is off
Apr  8 23:41:52 AnotherMass kernel: [    3.512052] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Apr  8 23:41:52 AnotherMass kernel: [    3.512073] sd 5:0:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 23:41:52 AnotherMass kernel: [    3.512176] sd 5:0:0:0: Attached scsi generic sg4 type 0
Apr  8 23:41:52 AnotherMass kernel: [    3.513222]  sde: sde1 sde2 < sde5 >
Apr  8 23:41:52 AnotherMass kernel: [    3.513909] sd 5:0:0:0: [sde] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.524620] usb 4-2: New USB device found, idVendor=04f3, idProduct=0103
Apr  8 23:41:52 AnotherMass kernel: [    3.524664] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  8 23:41:52 AnotherMass kernel: [    3.531479] hidraw: raw HID events driver (C) Jiri Kosina
Apr  8 23:41:52 AnotherMass kernel: [    3.544838] usbcore: registered new interface driver usbhid
Apr  8 23:41:52 AnotherMass kernel: [    3.544877] usbhid: USB HID core driver
Apr  8 23:41:52 AnotherMass kernel: [    3.547072] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input2
Apr  8 23:41:52 AnotherMass kernel: [    3.547208] hid-generic 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:12.0-2/input0
Apr  8 23:41:52 AnotherMass kernel: [    3.550768] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input3
Apr  8 23:41:52 AnotherMass kernel: [    3.550908] hid-generic 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:12.0-2/input1
Apr  8 23:41:52 AnotherMass kernel: [    3.565040]  sda: sda1
Apr  8 23:41:52 AnotherMass kernel: [    3.565520] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.583160]  sdb: sdb1
Apr  8 23:41:52 AnotherMass kernel: [    3.583561] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.589338]  sdd: sdd1
Apr  8 23:41:52 AnotherMass kernel: [    3.589743] sd 3:0:0:0: [sdd] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    3.628689] Switched to clocksource tsc
Apr  8 23:41:52 AnotherMass kernel: [    4.125996]  sdc: sdc1
Apr  8 23:41:52 AnotherMass kernel: [    4.126825] sd 2:0:0:0: [sdc] Attached SCSI disk
Apr  8 23:41:52 AnotherMass kernel: [    4.198003] random: nonblocking pool is initialized
Apr  8 23:41:52 AnotherMass kernel: [    4.201351] md: bind<sdd1>
Apr  8 23:41:52 AnotherMass kernel: [    4.203508] md: bind<sda1>
Apr  8 23:41:52 AnotherMass kernel: [    4.205769] md: bind<sdb1>
Apr  8 23:41:52 AnotherMass kernel: [    4.212392] EXT4-fs (sde1): INFO: recovery required on readonly filesystem
Apr  8 23:41:52 AnotherMass kernel: [    4.212440] EXT4-fs (sde1): write access will be enabled during recovery
Apr  8 23:41:52 AnotherMass kernel: [    4.221732] md: bind<sdc1>
Apr  8 23:41:52 AnotherMass kernel: [    4.379378] EXT4-fs (sde1): recovery complete
Apr  8 23:41:52 AnotherMass kernel: [    4.380855] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Apr  8 23:41:52 AnotherMass kernel: [    4.697240] init: plymouth-upstart-bridge main process (195) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.697288] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.704035] init: plymouth-upstart-bridge main process (205) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.704087] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.710408] init: plymouth-upstart-bridge main process (208) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.710457] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.715271] init: plymouth-upstart-bridge main process (210) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.715325] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.722310] init: plymouth-upstart-bridge main process (212) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.722359] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.734807] init: plymouth-upstart-bridge main process (215) terminated with status 1
Apr  8 23:41:52 AnotherMass kernel: [    4.734862] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:52 AnotherMass kernel: [    4.927269] Adding 6157308k swap on /dev/sde5.  Priority:-1 extents:1 across:6157308k SSFS
Apr  8 23:41:52 AnotherMass kernel: [    4.976940] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
Apr  8 23:41:52 AnotherMass kernel: [    6.081717] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 23:41:52 AnotherMass kernel: [    6.152999] systemd-udevd[378]: starting version 204
Apr  8 23:41:52 AnotherMass kernel: [    6.261744] lp: driver loaded but no devices found
Apr  8 23:41:52 AnotherMass kernel: [    6.286540] ppdev: user-space parallel port driver
Apr  8 23:41:52 AnotherMass kernel: [    6.302772] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  8 23:41:52 AnotherMass kernel: [    6.381174] [drm] Initialized drm 1.1.0 20060810
Apr  8 23:41:52 AnotherMass kernel: [    6.402747] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr  8 23:41:52 AnotherMass kernel: [    6.402816] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
Apr  8 23:41:52 AnotherMass kernel: [    6.409855] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Apr  8 23:41:52 AnotherMass kernel: [    6.409940] sp5100_tco: PCI Revision ID: 0x42
Apr  8 23:41:52 AnotherMass kernel: [    6.409983] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
Apr  8 23:41:52 AnotherMass kernel: [    6.409995] sp5100_tco: Last reboot was not triggered by watchdog.
Apr  8 23:41:52 AnotherMass kernel: [    6.410108] sp5100_tco: initialized (0xffffc90000c7ab00). heartbeat=60 sec (nowayout=0)
Apr  8 23:41:52 AnotherMass kernel: [    6.412412] type=1400 audit(1428532905.972:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412421] type=1400 audit(1428532905.972:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412427] type=1400 audit(1428532905.972:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412993] type=1400 audit(1428532905.972:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.412999] type=1400 audit(1428532905.972:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.413314] type=1400 audit(1428532905.972:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [    6.417952] MCE: In-kernel MCE decoding enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.445213] EDAC MC: Ver: 3.0.0
Apr  8 23:41:52 AnotherMass kernel: [    6.457119] AMD64 EDAC driver v3.4.0
Apr  8 23:41:52 AnotherMass kernel: [    6.457158] EDAC amd64: DRAM ECC enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.457164] EDAC amd64: F10h detected (node 0).
Apr  8 23:41:52 AnotherMass kernel: [    6.457179] EDAC MC: DCT0 chip selects:
Apr  8 23:41:52 AnotherMass kernel: [    6.457181] EDAC amd64: MC: 0:  1024MB 1:  1024MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457183] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457184] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457186] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457187] EDAC MC: DCT1 chip selects:
Apr  8 23:41:52 AnotherMass kernel: [    6.457189] EDAC amd64: MC: 0:  2048MB 1:  2048MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457190] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457191] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457193] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  8 23:41:52 AnotherMass kernel: [    6.457194] EDAC amd64: using x4 syndromes.
Apr  8 23:41:52 AnotherMass kernel: [    6.457195] EDAC amd64: MCT channel count: 2
Apr  8 23:41:52 AnotherMass kernel: [    6.457218] EDAC amd64: CS0: Unbuffered DDR3 RAM
Apr  8 23:41:52 AnotherMass kernel: [    6.457219] EDAC amd64: CS1: Unbuffered DDR3 RAM
Apr  8 23:41:52 AnotherMass kernel: [    6.461574] EDAC MC0: Giving out device to module amd64_edac controller F10h: DEV 0000:00:18.2 (INTERRUPT)
Apr  8 23:41:52 AnotherMass kernel: [    6.461632] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
Apr  8 23:41:52 AnotherMass kernel: [    6.555086] kvm: Nested Virtualization enabled
Apr  8 23:41:52 AnotherMass kernel: [    6.555093] kvm: Nested Paging enabled
Apr  8 23:41:52 AnotherMass kernel: [    6.566152] [drm] radeon kernel modesetting enabled.
Apr  8 23:41:52 AnotherMass kernel: [    6.566389] tg3 0000:02:00.0: irq 42 for MSI/MSI-X
Apr  8 23:41:52 AnotherMass kernel: [    6.707053] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
Apr  8 23:41:52 AnotherMass kernel: [    6.707072] [drm] register mmio base: 0xFE8F0000
Apr  8 23:41:52 AnotherMass kernel: [    6.707074] [drm] register mmio size: 65536
Apr  8 23:41:52 AnotherMass kernel: [    6.707777] ATOM BIOS: AMD_1407_150
Apr  8 23:41:52 AnotherMass kernel: [    6.707844] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
Apr  8 23:41:52 AnotherMass kernel: [    6.707847] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Apr  8 23:41:52 AnotherMass kernel: [    6.707893] [drm] Detected VRAM RAM=128M, BAR=128M
Apr  8 23:41:52 AnotherMass kernel: [    6.707895] [drm] RAM width 32bits DDR
Apr  8 23:41:52 AnotherMass kernel: [    6.707967] [TTM] Zone  kernel: Available graphics memory: 2991704 kiB
Apr  8 23:41:52 AnotherMass kernel: [    6.707969] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Apr  8 23:41:52 AnotherMass kernel: [    6.707970] [TTM] Initializing pool allocator
Apr  8 23:41:52 AnotherMass kernel: [    6.707976] [TTM] Initializing DMA pool allocator
Apr  8 23:41:52 AnotherMass kernel: [    6.707994] [drm] radeon: 128M of VRAM memory ready
Apr  8 23:41:52 AnotherMass kernel: [    6.707996] [drm] radeon: 512M of GTT memory ready.
Apr  8 23:41:52 AnotherMass kernel: [    6.708004] [drm] Loading RS780 Microcode
Apr  8 23:41:52 AnotherMass kernel: [    7.341172] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 23:41:52 AnotherMass kernel: [    7.429443] [drm] GART: num cpu pages 131072, num gpu pages 131072
Apr  8 23:41:52 AnotherMass kernel: [    7.524270] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Apr  8 23:41:52 AnotherMass kernel: [    7.524357] radeon 0000:01:05.0: WB enabled
Apr  8 23:41:52 AnotherMass kernel: [    7.524361] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff8800d6763c00
Apr  8 23:41:52 AnotherMass kernel: [    7.524364] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff8800d6763c0c
Apr  8 23:41:52 AnotherMass kernel: [    7.524367] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  8 23:41:52 AnotherMass kernel: [    7.524368] [drm] Driver supports precise vblank timestamp query.
Apr  8 23:41:52 AnotherMass kernel: [    7.524370] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
Apr  8 23:41:52 AnotherMass kernel: [    7.524389] [drm] radeon: irq initialized.
Apr  8 23:41:52 AnotherMass kernel: [    7.563940] [drm] ring test on 0 succeeded in 1 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.563952] [drm] ring test on 3 succeeded in 2 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564097] [drm] Enabling audio 0 support
Apr  8 23:41:52 AnotherMass kernel: [    7.564118] [drm] ib test on ring 0 succeeded in 0 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564132] [drm] ib test on ring 3 succeeded in 0 usecs
Apr  8 23:41:52 AnotherMass kernel: [    7.564349] [drm] Radeon Display Connectors
Apr  8 23:41:52 AnotherMass kernel: [    7.564351] [drm] Connector 0:
Apr  8 23:41:52 AnotherMass kernel: [    7.564352] [drm]   VGA-1
Apr  8 23:41:52 AnotherMass kernel: [    7.564354] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Apr  8 23:41:52 AnotherMass kernel: [    7.564355] [drm]   Encoders:
Apr  8 23:41:52 AnotherMass kernel: [    7.564357] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Apr  8 23:41:52 AnotherMass kernel: [    7.564376] [drm] radeon: power management initialized
Apr  8 23:41:52 AnotherMass kernel: [    7.614107] [drm] fb mappable at 0xF0141000
Apr  8 23:41:52 AnotherMass kernel: [    7.614112] [drm] vram apper at 0xF0000000
Apr  8 23:41:52 AnotherMass kernel: [    7.614114] [drm] size 5324800
Apr  8 23:41:52 AnotherMass kernel: [    7.614115] [drm] fb depth is 24
Apr  8 23:41:52 AnotherMass kernel: [    7.614117] [drm]    pitch is 5888
Apr  8 23:41:52 AnotherMass kernel: [    7.614197] fbcon: radeondrmfb (fb0) is primary device
Apr  8 23:41:52 AnotherMass kernel: [    7.644860] Console: switching to colour frame buffer device 180x56
Apr  8 23:41:52 AnotherMass kernel: [    7.658769] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
Apr  8 23:41:52 AnotherMass kernel: [    7.658772] radeon 0000:01:05.0: registered panic notifier
Apr  8 23:41:52 AnotherMass kernel: [    7.658788] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0
Apr  8 23:41:52 AnotherMass kernel: [    9.904798] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
Apr  8 23:41:52 AnotherMass kernel: [    9.904803] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
Apr  8 23:41:52 AnotherMass kernel: [    9.904825] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  8 23:41:52 AnotherMass kernel: [   12.773555] Bluetooth: Core ver 2.17
Apr  8 23:41:52 AnotherMass kernel: [   12.773584] NET: Registered protocol family 31
Apr  8 23:41:52 AnotherMass kernel: [   12.773586] Bluetooth: HCI device and connection manager initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773599] Bluetooth: HCI socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773602] Bluetooth: L2CAP socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.773607] Bluetooth: SCO socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793804] Bluetooth: RFCOMM TTY layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793821] Bluetooth: RFCOMM socket layer initialized
Apr  8 23:41:52 AnotherMass kernel: [   12.793829] Bluetooth: RFCOMM ver 1.11
Apr  8 23:41:52 AnotherMass kernel: [   12.795083] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  8 23:41:52 AnotherMass kernel: [   12.795088] Bluetooth: BNEP filters: protocol multicast
Apr  8 23:41:52 AnotherMass kernel: [   12.795100] Bluetooth: BNEP socket layer initialized
Apr  8 23:41:52 AnotherMass rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Found user 'avahi' (UID 108) and group 'avahi' (GID 120).
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Successfully dropped root privileges.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: avahi-daemon 0.6.31 starting up.
Apr  8 23:41:52 AnotherMass kernel: [   12.828129] type=1400 audit(1428532912.392:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=864 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [   12.828140] type=1400 audit(1428532912.392:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass kernel: [   12.828691] type=1400 audit(1428532912.392:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Successfully called chroot().
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Successfully dropped remaining capabilities.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Loading service file /services/afpd.service.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Loading service file /services/udisks.service.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::3aea:a7ff:fea3:2a32.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: New relevant interface eth0.IPv6 for mDNS.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Network interface enumeration completed.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Registering new address record for fe80::3aea:a7ff:fea3:2a32 on eth0.*.
Apr  8 23:41:52 AnotherMass avahi-daemon[872]: Registering HINFO record with values 'X86_64'/'LINUX'.
Apr  8 23:41:52 AnotherMass kernel: [   12.848213] init: cups main process (877) killed by HUP signal
Apr  8 23:41:52 AnotherMass kernel: [   12.848227] init: cups main process ended, respawning
Apr  8 23:41:53 AnotherMass avahi-daemon[872]: Server startup complete. Host name is AnotherMass.local. Local service cookie is 513952672.
Apr  8 23:41:54 AnotherMass avahi-daemon[872]: Service "AnotherMass" (/services/udisks.service) successfully established.
Apr  8 23:41:54 AnotherMass avahi-daemon[872]: Service "AnotherMass" (/services/afpd.service) successfully established.
Apr  8 23:41:57 AnotherMass dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x5e6afe07)
Apr  8 23:41:57 AnotherMass dhclient: DHCPREQUEST of 192.168.2.6 on eth0 to 255.255.255.255 port 67 (xid=0x5e6afe07)
Apr  8 23:41:57 AnotherMass dhclient: DHCPOFFER of 192.168.2.6 from 192.168.2.1
Apr  8 23:41:57 AnotherMass dhclient: DHCPACK of 192.168.2.6 from 192.168.2.1
Apr  8 23:41:57 AnotherMass avahi-daemon[872]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.6.
Apr  8 23:41:57 AnotherMass avahi-daemon[872]: New relevant interface eth0.IPv4 for mDNS.
Apr  8 23:41:57 AnotherMass avahi-daemon[872]: Registering new address record for 192.168.2.6 on eth0.IPv4.
Apr  8 23:41:57 AnotherMass dhclient: bound to 192.168.2.6 -- renewal in 36164 seconds.
Apr  8 23:41:57 AnotherMass kernel: [   17.914274] init: failsafe main process (764) killed by TERM signal
Apr  8 23:41:57 AnotherMass ModemManager[1051]: <info>  ModemManager (version 1.0.0) starting...
Apr  8 23:41:57 AnotherMass kernel: [   18.114632] type=1400 audit(1428532917.680:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.114643] type=1400 audit(1428532917.680:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.114649] type=1400 audit(1428532917.680:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115213] type=1400 audit(1428532917.680:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115218] type=1400 audit(1428532917.680:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.115537] type=1400 audit(1428532917.680:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1113 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134026] type=1400 audit(1428532917.700:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134036] type=1400 audit(1428532917.700:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass kernel: [   18.134393] type=1400 audit(1428532917.700:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1112 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> NetworkManager (version 0.9.8.8) is starting...
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> WEXT support is enabled
Apr  8 23:41:57 AnotherMass kernel: [   18.171058] type=1400 audit(1428532917.736:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=1116 comm="apparmor_parser"
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> DNS: loaded plugin dnsmasq
Apr  8 23:41:57 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Apr  8 23:41:57 AnotherMass polkitd[1124]: started daemon version 0.105 using authority implementation `local' version `0.105'
Apr  8 23:41:57 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: init!
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: update_system_hostname
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:       interface-parser: parsing file /etc/network/interfaces
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:       interface-parser: finished parsing file /etc/network/interfaces
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: adding eth0 to connections
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: adding iface eth0 to eni_ifaces
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: autoconnect
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPluginIfupdown: management mode: unmanaged
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth0, iface: eth0)
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPluginIfupdown: locking wired connection setting
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: end _init.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ofono: init!
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ofono: end _init.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> Loaded plugin (null): (null)
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    Ifupdown: get unmanaged devices count: 1
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: (31240976) ... get_connections.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ifupdown: (31240976) ... get_connections (managed=false): return empty list.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    keyfile: parsing Wired connection ... 
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    keyfile:     read connection 'Wired connection'
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ofono: (469778800) ... get_connections.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    SCPlugin-Ofono: (469778800) connections count: 0
Apr  8 23:41:57 AnotherMass NetworkManager[1117]:    Ifupdown: get unmanaged devices count: 1
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> Networking is disabled by state file
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <warn> failed to allocate link cache: (-12) Object not found
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> (eth0): carrier is ON
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> urfkill disappeared from the bus
Apr  8 23:41:57 AnotherMass NetworkManager[1117]: <info> ModemManager available in the bus
Apr  8 23:41:58 AnotherMass anacron[1259]: Anacron 2.3 started on 2015-04-08
Apr  8 23:41:58 AnotherMass anacron[1259]: Normal exit (0 jobs run)
Apr  8 23:41:58 AnotherMass acpid: starting up with netlink and the input layer
Apr  8 23:41:58 AnotherMass cron[1186]: (CRON) INFO (pidfile fd = 3)
Apr  8 23:41:58 AnotherMass acpid: 9 rules loaded
Apr  8 23:41:58 AnotherMass acpid: waiting for events: event logging is off
Apr  8 23:41:58 AnotherMass whoopsie[1240]: whoopsie 0.2.24.6 starting up.
Apr  8 23:41:58 AnotherMass whoopsie[1240]: Using lock path: /var/lock/whoopsie/lock
Apr  8 23:41:58 AnotherMass kernel: [   18.811355] init: plexmediaserver main process (1028) terminated with status 255
Apr  8 23:41:58 AnotherMass kernel: [   18.811366] init: plexmediaserver main process ended, respawning
Apr  8 23:41:58 AnotherMass cron[1271]: (CRON) STARTUP (fork ok)
Apr  8 23:41:58 AnotherMass cron[1271]: (CRON) INFO (Running @reboot jobs)
Apr  8 23:41:58 AnotherMass NetworkManager[1117]: <info> NetworkManager state is now ASLEEP
Apr  8 23:41:58 AnotherMass whoopsie[1295]: offline
Apr  8 23:41:58 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Apr  8 23:41:58 AnotherMass accounts-daemon[1352]: started daemon version 0.6.35
Apr  8 23:41:58 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.Accounts'
Apr  8 23:41:59 AnotherMass kernel: [   19.774602] init: plymouth-upstart-bridge main process ended, respawning
Apr  8 23:41:59 AnotherMass ModemManager[1051]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0': not supported by any plugin
Apr  8 23:42:00 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Apr  8 23:42:00 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.UPower'
Apr  8 23:42:00 AnotherMass gnome-session[1580]: WARNING: Could not parse desktop file gwibber.desktop or it references a not found TryExec binary
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.systemd1'
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Successfully called chroot.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Successfully dropped privileges.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Successfully limited resources.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Running.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Watchdog thread running.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Canary thread running.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Successfully made thread 1857 of process 1857 (n/a) owned by '1000' high priority at nice level -11.
Apr  8 23:42:01 AnotherMass rtkit-daemon[1877]: Supervising 1 threads of 1 processes of 1 users.
Apr  8 23:42:01 AnotherMass anacron[1992]: Anacron 2.3 started on 2015-04-08
Apr  8 23:42:01 AnotherMass anacron[1992]: Normal exit (0 jobs run)
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Apr  8 23:42:01 AnotherMass colord: Using config file /etc/colord.conf
Apr  8 23:42:01 AnotherMass colord: Using mapping database file /var/lib/colord/mapping.db
Apr  8 23:42:01 AnotherMass colord: Using device database file /var/lib/colord/storage.db
Apr  8 23:42:01 AnotherMass colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Apr  8 23:42:01 AnotherMass colord: loaded plugin libcd_plugin_scanner.so
Apr  8 23:42:01 AnotherMass colord: loaded plugin libcd_plugin_camera.so
Apr  8 23:42:01 AnotherMass colord: Daemon ready for requests
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Apr  8 23:42:01 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.locale1'
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Apr  8 23:42:01 AnotherMass colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Apr  8 23:42:02 AnotherMass postfix/master[2098]: daemon started -- version 2.11.0, configuration /etc/postfix
Apr  8 23:42:02 AnotherMass rtkit-daemon[1877]: Successfully made thread 2102 of process 2102 (n/a) owned by '1000' high priority at nice level -11.
Apr  8 23:42:02 AnotherMass rtkit-daemon[1877]: Supervising 2 threads of 2 processes of 1 users.
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Apr  8 23:42:02 AnotherMass pulseaudio[2102]: [pulseaudio] pid.c: Daemon already running.
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Apr  8 23:42:02 AnotherMass colord: Device added: xrandr-HannStar Display Corp-HW191-135GH3LY0164
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-6d2c6f5342110436ff327e67f932b6aa
Apr  8 23:42:02 AnotherMass colord: Automatic metadata add icc-bb5b30cc367783c64108a4dc12b2b60f to xrandr-HannStar Display Corp-HW191-135GH3LY0164
Apr  8 23:42:02 AnotherMass colord: Profile added: icc-bb5b30cc367783c64108a4dc12b2b60f
Apr  8 23:42:03 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Apr  8 23:42:03 AnotherMass udisksd[2245]: udisks daemon version 2.1.3 starting
Apr  8 23:42:03 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Apr  8 23:42:03 AnotherMass udisksd[2245]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Apr  8 23:42:03 AnotherMass udisksd[2245]: Cleaning up mount point /media/user/Ted (device 259:0 no longer exist)
Apr  8 23:42:03 AnotherMass mdadm[2300]: DeviceDisappeared event detected on md device /dev/md/0
Apr  8 23:42:03 AnotherMass afpd[2320]: AFP/TCP started, advertising 192.168.2.6:548 (2.2.2)
Apr  8 23:42:38 AnotherMass ntpdate[1021]: step time server 91.189.89.199 offset 34.917333 sec
Apr  8 23:42:42 AnotherMass NetworkManager[1117]: <info> WiFi hardware radio set enabled
Apr  8 23:42:43 AnotherMass kernel: [   29.147672] init: plymouth-stop pre-start process (2554) terminated with status 1
Apr  8 23:42:57 AnotherMass kernel: [   42.940594] audit_printk_skb: 123 callbacks suppressed
Apr  8 23:42:57 AnotherMass kernel: [   42.940599] type=1400 audit(1428532977.430:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2764 comm="apparmor_parser"
Apr  8 23:42:57 AnotherMass kernel: [   42.940608] type=1400 audit(1428532977.430:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2764 comm="apparmor_parser"
Apr  8 23:42:57 AnotherMass kernel: [   42.941215] type=1400 audit(1428532977.434:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2764 comm="apparmor_parser"
Apr  8 23:43:07 AnotherMass gnome-session[1580]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Apr  9 00:03:48 AnotherMass afpd[3473]: AFP3.3 Login by user
Apr  9 00:03:48 AnotherMass afpd[3473]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  9 00:03:48 AnotherMass afpd[3473]: AFP logout by user
Apr  9 00:03:48 AnotherMass afpd[3473]: dsi_stream_read: len:0, unexpected EOF
Apr  9 00:03:48 AnotherMass afpd[3473]: afp_over_dsi: client logged out, terminating DSI session
Apr  9 00:03:48 AnotherMass afpd[3473]: AFP statistics: 0.61 KB read, 0.45 KB written
Apr  9 00:17:01 AnotherMass CRON[3853]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 00:20:44 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr  9 00:20:44 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr  9 00:20:44 AnotherMass kernel: [ 2308.919279] systemd-hostnamed[3985]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Apr  9 00:22:18 AnotherMass afpd[4194]: AFP3.3 Login by user
Apr  9 00:22:18 AnotherMass afpd[4194]: Duplicate volume name, check AppleVolumes files: previous: "Home Directory", new: "Home Directory"
Apr  9 00:22:21 AnotherMass afpd[4194]: AFP logout by user
Apr  9 00:22:21 AnotherMass afpd[4194]: dsi_stream_read: len:0, unexpected EOF
Apr  9 00:22:21 AnotherMass afpd[4194]: afp_over_dsi: client logged out, terminating DSI session
Apr  9 00:22:21 AnotherMass afpd[4194]: AFP statistics: 0.68 KB read, 0.54 KB written
Apr  9 00:22:27 AnotherMass colord: device removed: xrandr-HannStar Display Corp-HW191-135GH3LY0164
Apr  9 00:22:27 AnotherMass colord: Profile removed: icc-6d2c6f5342110436ff327e67f932b6aa
Apr  9 00:22:27 AnotherMass colord: Profile removed: icc-bb5b30cc367783c64108a4dc12b2b60f
Apr  9 00:22:27 AnotherMass dbus[790]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Apr  9 00:22:27 AnotherMass dbus[790]: [system] Successfully activated service 'org.freedesktop.systemd1'
Apr  9 00:22:27 AnotherMass rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="866" x-info="http://www.rsyslog.com"] exiting on signal 15.
Apr  9 07:32:06 AnotherMass rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1040" x-info="http://www.rsyslog.com"] start
Apr  9 07:32:06 AnotherMass rsyslogd: rsyslogd's groupid changed to 103
Apr  9 07:32:06 AnotherMass rsyslogd: rsyslogd's userid changed to 101
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Linux version 3.13.0-48-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 (Ubuntu 3.13.0-48.80-generic 3.13.11-ckt16)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] KERNEL supported cpus:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Intel GenuineIntel
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   AMD AuthenticAMD
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Centaur CentaurHauls
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d7f8ffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7f9e000-0x00000000d7f9ffff] type 9
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fa0000-0x00000000d7fadfff] ACPI data
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fae000-0x00000000d7fdffff] ACPI NVS
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7fe0000-0x00000000d7ffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000019fffffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] SMBIOS 2.6 present.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR default type: uncachable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   00000-9FFFF write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   A0000-EFFFF uncachable
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] MTRR variable ranges enabled:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   3 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   4 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   5 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   6 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   7 disabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] TOM2: 00000001a0000000 aka 6656M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Using GB pages for direct mapping
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19fe00000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x19fe00000-0x19fffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x19c000000-0x19fdfffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x19c000000-0x19fdfffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x180000000-0x19bffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x180000000-0x19bffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xd7f8ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0xc0000000-0xd7dfffff] page 2M
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0xd7e00000-0xd7f8ffff] page 4k
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [mem 0x100000000-0x17fffffff] page 1G
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] RAMDISK: [mem 0x35a4e000-0x36d1efff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: RSDP 00000000000f8f50 000024 (v02 HP    )
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: XSDT 00000000d7fa0100 00007C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: FACP 00000000d7fa0290 0000F4 (v03 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: DSDT 00000000d7fa0620 006947 (v01 HP     ProLiant 00000006 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: FACS 00000000d7fae000 000040
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: APIC 00000000d7fa0390 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: MCFG 00000000d7fa0410 00003C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: SPMI 00000000d7fa0450 000041 (v05 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: OEMB 00000000d7fae040 000072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HPET 00000000d7fab4e0 000038 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: EINJ 00000000d7fab520 000130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: BERT 00000000d7fab6b0 000030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: ERST 00000000d7fab6e0 0001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HEST 00000000d7fab890 0000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: SSDT 00000000d7fab940 00052A (v01 HP     ProLiant 00000001 AMD  00000001)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No NUMA configuration found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000019fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   NODE_DATA [mem 0x19fff9000-0x19fffdfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199800000-ffff88019f5fffff] on node 0
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Zone ranges:
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal   [mem 0x100000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Movable zone start for each node
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Early memory node ranges
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x00100000-0xd7f8ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   node   0: [mem 0x100000000-0x19fffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] On node 0 totalpages: 1539885
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32 zone: 13759 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   DMA32 zone: 880528 pages, LIFO batch:31
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal zone: 10240 pages used for memmap
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]   Normal zone: 655360 pages, LIFO batch:31
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] nr_irqs_gsi: 40
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e1fff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e2000-0x000fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f90000-0xd7f9dfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7f9e000-0xd7f9ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fa0000-0xd7fadfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fae000-0xd7fdffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7fe0000-0xd7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xff9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] e820: [mem 0xf0000000-0xff9fffff] available for PCI devices
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s82368 r8192 d24128 u524288
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] pcpu-alloc: s82368 r8192 d24128 u524288 alloc=1*2097152
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1515801
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Policy zone: Normal
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-generic root=UUID=eb422a72-f822-4922-9d7f-67990b8b12de ro nomdmonddf nomdmonisw nomdmonddf nomdmonisw
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Checking aperture...
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] No AGP bridge found
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Node 0: aperture @ fdfc000000 size 32 MB
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] This costs you 64 MB of RAM
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc000000-0xcfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Memory: 5895336K/6159540K available (7385K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 264204K reserved)
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Hierarchical RCU implementation.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] Console: colour dummy device 80x25
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] console [tty0] enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] allocated 24641536 bytes of page_cgroup
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] hpet clockevent registered
Apr  9 07:32:06 AnotherMass kernel: [    0.000000] tsc: Fast TSC calibration failed
Apr  9 07:32:06 AnotherMass kernel: [    0.012000] tsc: PIT calibration matches HPET. 2 loops
Apr  9 07:32:06 AnotherMass kernel: [    0.012000] tsc: Detected 2196.352 MHz processor
Apr  9 07:32:06 AnotherMass kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4392.70 BogoMIPS (lpj=8785408)
Apr  9 07:32:06 AnotherMass kernel: [    0.000011] pid_max: default: 32768 minimum: 301
Apr  9 07:32:06 AnotherMass kernel: [    0.000048] Security Framework initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.000070] AppArmor: AppArmor initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.000072] Yama: becoming mindful.
Apr  9 07:32:06 AnotherMass kernel: [    0.000758] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.004705] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006589] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006607] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.006975] Initializing cgroup subsys memory
Apr  9 07:32:06 AnotherMass kernel: [    0.006986] Initializing cgroup subsys devices
Apr  9 07:32:06 AnotherMass kernel: [    0.006989] Initializing cgroup subsys freezer
Apr  9 07:32:06 AnotherMass kernel: [    0.006992] Initializing cgroup subsys blkio
Apr  9 07:32:06 AnotherMass kernel: [    0.006995] Initializing cgroup subsys perf_event
Apr  9 07:32:06 AnotherMass kernel: [    0.007000] Initializing cgroup subsys hugetlb
Apr  9 07:32:06 AnotherMass kernel: [    0.007024] tseg: 0000000000
Apr  9 07:32:06 AnotherMass kernel: [    0.007032] CPU: Physical Processor ID: 0
Apr  9 07:32:06 AnotherMass kernel: [    0.007035] CPU: Processor Core ID: 0
Apr  9 07:32:06 AnotherMass kernel: [    0.007038] mce: CPU supports 6 MCE banks
Apr  9 07:32:06 AnotherMass kernel: [    0.007046] LVT offset 0 assigned for vector 0xf9
Apr  9 07:32:06 AnotherMass kernel: [    0.007051] process: using AMD E400 aware idle routine
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
Apr  9 07:32:06 AnotherMass kernel: [    0.007056] tlb_flushall_shift: 4
Apr  9 07:32:06 AnotherMass kernel: [    0.007178] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Apr  9 07:32:06 AnotherMass kernel: [    0.008119] ACPI: Core revision 20131115
Apr  9 07:32:06 AnotherMass kernel: [    0.011272] ACPI: All ACPI Tables successfully acquired
Apr  9 07:32:06 AnotherMass kernel: [    0.013039] ftrace: allocating 28562 entries in 112 pages
Apr  9 07:32:06 AnotherMass kernel: [    0.027635] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  9 07:32:06 AnotherMass kernel: [    0.068088] smpboot: CPU0: AMD Turion(tm) II Neo N54L Dual-Core Processor (fam: 10, model: 06, stepping: 03)
Apr  9 07:32:06 AnotherMass kernel: [    0.173246] Performance Events: AMD PMU driver.
Apr  9 07:32:06 AnotherMass kernel: [    0.173252] ... version:                0
Apr  9 07:32:06 AnotherMass kernel: [    0.173254] ... bit width:              48
Apr  9 07:32:06 AnotherMass kernel: [    0.173257] ... generic registers:      4
Apr  9 07:32:06 AnotherMass kernel: [    0.173259] ... value mask:             0000ffffffffffff
Apr  9 07:32:06 AnotherMass kernel: [    0.173261] ... max period:             00007fffffffffff
Apr  9 07:32:06 AnotherMass kernel: [    0.173263] ... fixed-purpose events:   0
Apr  9 07:32:06 AnotherMass kernel: [    0.173265] ... event mask:             000000000000000f
Apr  9 07:32:06 AnotherMass kernel: [    0.175041] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  9 07:32:06 AnotherMass kernel: [    0.175140] x86: Booting SMP configuration:
Apr  9 07:32:06 AnotherMass kernel: [    0.175144] .... node  #0, CPUs:      #1
Apr  9 07:32:06 AnotherMass kernel: [    0.188204] x86: Booted up 1 node, 2 CPUs
Apr  9 07:32:06 AnotherMass kernel: [    0.188208] smpboot: Total of 2 processors activated (8785.40 BogoMIPS)
Apr  9 07:32:06 AnotherMass kernel: [    0.188249] process: System has AMD C1E enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.188268] process: Switch to broadcast mode on CPU1
Apr  9 07:32:06 AnotherMass kernel: [    0.188922] process: Switch to broadcast mode on CPU0
Apr  9 07:32:06 AnotherMass kernel: [    0.189033] devtmpfs: initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.194229] EVM: security.selinux
Apr  9 07:32:06 AnotherMass kernel: [    0.194232] EVM: security.SMACK64
Apr  9 07:32:06 AnotherMass kernel: [    0.194234] EVM: security.ima
Apr  9 07:32:06 AnotherMass kernel: [    0.194236] EVM: security.capability
Apr  9 07:32:06 AnotherMass kernel: [    0.194326] PM: Registering ACPI NVS region [mem 0xd7fae000-0xd7fdffff] (204800 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.195482] pinctrl core: initialized pinctrl subsystem
Apr  9 07:32:06 AnotherMass kernel: [    0.195572] regulator-dummy: no parameters
Apr  9 07:32:06 AnotherMass kernel: [    0.195606] RTC time:  6:31:33, date: 04/09/15
Apr  9 07:32:06 AnotherMass kernel: [    0.195658] NET: Registered protocol family 16
Apr  9 07:32:06 AnotherMass kernel: [    0.195791] cpuidle: using governor ladder
Apr  9 07:32:06 AnotherMass kernel: [    0.195795] cpuidle: using governor menu
Apr  9 07:32:06 AnotherMass kernel: [    0.195801] node 0 link 0: io port [1000, ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195804] TOM: 00000000e0000000 aka 3584M
Apr  9 07:32:06 AnotherMass kernel: [    0.195807] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195810] node 0 link 0: mmio [a0000, bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195813] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195816] node 0 link 0: mmio [f8000000, fe6fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195818] node 0 link 0: mmio [fe700000, fe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195820] node 0 link 0: mmio [fe900000, ffdfffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195821] TOM2: 00000001a0000000 aka 6656M
Apr  9 07:32:06 AnotherMass kernel: [    0.195824] bus: [bus 00-1f] on node 0 link 0
Apr  9 07:32:06 AnotherMass kernel: [    0.195826] bus: 00 [io  0x0000-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195827] bus: 00 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195829] bus: 00 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195830] bus: 00 [mem 0x1a0000000-0xfcffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.195892] ACPI: bus type PCI registered
Apr  9 07:32:06 AnotherMass kernel: [    0.195895] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  9 07:32:06 AnotherMass kernel: [    0.195961] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  9 07:32:06 AnotherMass kernel: [    0.195966] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  9 07:32:06 AnotherMass kernel: [    0.208048] PCI: Using configuration type 1 for base access
Apr  9 07:32:06 AnotherMass kernel: [    0.208241] mtrr: your CPUs had inconsistent variable MTRR settings
Apr  9 07:32:06 AnotherMass kernel: [    0.208244] mtrr: probably your BIOS does not setup all CPUs.
Apr  9 07:32:06 AnotherMass kernel: [    0.208246] mtrr: corrected configuration.
Apr  9 07:32:06 AnotherMass kernel: [    0.209208] bio: create slab <bio-0> at 0
Apr  9 07:32:06 AnotherMass kernel: [    0.209528] ACPI: Added _OSI(Module Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.209535] ACPI: Added _OSI(Processor Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.209538] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  9 07:32:06 AnotherMass kernel: [    0.209541] ACPI: Added _OSI(Processor Aggregator Device)
Apr  9 07:32:06 AnotherMass kernel: [    0.211138] ACPI: Executed 2 blocks of module-level executable AML code
Apr  9 07:32:06 AnotherMass kernel: [    0.212995] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.216396] ACPI: OEMN 00000000d7faaeb0 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.216614] ACPI: Dynamic OEM Table Load:
Apr  9 07:32:06 AnotherMass kernel: [    0.216618] ACPI: OEMN           (null) 000624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 07:32:06 AnotherMass kernel: [    0.220457] \_SB_:_OSC evaluation returned wrong type
Apr  9 07:32:06 AnotherMass kernel: [    0.220463] _OSC request data:1 1f 
Apr  9 07:32:06 AnotherMass kernel: [    0.220622] ACPI: Interpreter enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.220633] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220640] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220646] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
Apr  9 07:32:06 AnotherMass kernel: [    0.220660] ACPI: (supports S0 S4 S5)
Apr  9 07:32:06 AnotherMass kernel: [    0.220663] ACPI: Using IOAPIC for interrupt routing
Apr  9 07:32:06 AnotherMass kernel: [    0.220858] HEST: Table parsing has been initialized.
Apr  9 07:32:06 AnotherMass kernel: [    0.220863] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  9 07:32:06 AnotherMass kernel: [    0.220971] ACPI: No dock devices found.
Apr  9 07:32:06 AnotherMass kernel: [    0.225530] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  9 07:32:06 AnotherMass kernel: [    0.225539] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  9 07:32:06 AnotherMass kernel: [    0.225802] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Apr  9 07:32:06 AnotherMass kernel: [    0.226249] acpi PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.226254] acpi PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xfebfffff] ignored
Apr  9 07:32:06 AnotherMass kernel: [    0.226261] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000dffff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff])
Apr  9 07:32:06 AnotherMass kernel: [    0.226485] PCI host bridge to bus 0000:00
Apr  9 07:32:06 AnotherMass kernel: [    0.226489] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226493] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.226496] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226500] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226505] pci_bus 0000:00: root bus resource [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226509] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.226522] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.226639] pci 0000:00:01.0: [103c:9602] type 01 class 0x060400
Apr  9 07:32:06 AnotherMass kernel: [    0.226737] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
Apr  9 07:32:06 AnotherMass kernel: [    0.226773] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  9 07:32:06 AnotherMass kernel: [    0.226823] pci 0000:00:06.0: System wakeup disabled by ACPI
Apr  9 07:32:06 AnotherMass kernel: [    0.226873] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Apr  9 07:32:06 AnotherMass kernel: [    0.226894] pci 0000:00:11.0: reg 0x10: [io  0xd000-0xd007]
Apr  9 07:32:06 AnotherMass kernel: [    0.226904] pci 0000:00:11.0: reg 0x14: [io  0xc000-0xc003]
Apr  9 07:32:06 AnotherMass kernel: [    0.226913] pci 0000:00:11.0: reg 0x18: [io  0xb000-0xb007]
Apr  9 07:32:06 AnotherMass kernel: [    0.226923] pci 0000:00:11.0: reg 0x1c: [io  0xa000-0xa003]
Apr  9 07:32:06 AnotherMass kernel: [    0.226932] pci 0000:00:11.0: reg 0x20: [io  0x9000-0x900f]
Apr  9 07:32:06 AnotherMass kernel: [    0.226942] pci 0000:00:11.0: reg 0x24: [mem 0xfe6ffc00-0xfe6fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227065] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.227078] pci 0000:00:12.0: reg 0x10: [mem 0xfe6fe000-0xfe6fefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227201] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.227220] pci 0000:00:12.2: reg 0x10: [mem 0xfe6ff800-0xfe6ff8ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227299] pci 0000:00:12.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.227301] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.227384] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.227397] pci 0000:00:13.0: reg 0x10: [mem 0xfe6fd000-0xfe6fdfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227520] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.227539] pci 0000:00:13.2: reg 0x10: [mem 0xfe6ff400-0xfe6ff4ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.227617] pci 0000:00:13.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.227619] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.227699] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Apr  9 07:32:06 AnotherMass kernel: [    0.227828] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Apr  9 07:32:06 AnotherMass kernel: [    0.227957] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Apr  9 07:32:06 AnotherMass kernel: [    0.228031] pci 0000:00:14.4: System wakeup disabled by ACPI
Apr  9 07:32:06 AnotherMass kernel: [    0.228068] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
Apr  9 07:32:06 AnotherMass kernel: [    0.228081] pci 0000:00:16.0: reg 0x10: [mem 0xfe6fc000-0xfe6fcfff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228205] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
Apr  9 07:32:06 AnotherMass kernel: [    0.228224] pci 0000:00:16.2: reg 0x10: [mem 0xfe6ff000-0xfe6ff0ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228307] pci 0000:00:16.2: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.228309] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr  9 07:32:06 AnotherMass kernel: [    0.228388] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228459] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228527] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228595] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228665] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Apr  9 07:32:06 AnotherMass kernel: [    0.228785] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
Apr  9 07:32:06 AnotherMass kernel: [    0.228794] pci 0000:01:05.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.228799] pci 0000:01:05.0: reg 0x14: [io  0xe000-0xe0ff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228804] pci 0000:01:05.0: reg 0x18: [mem 0xfe8f0000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228815] pci 0000:01:05.0: reg 0x24: [mem 0xfe700000-0xfe7fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228834] pci 0000:01:05.0: supports D1 D2
Apr  9 07:32:06 AnotherMass kernel: [    0.228893] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  9 07:32:06 AnotherMass kernel: [    0.228898] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228901] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.228905] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.228966] pci 0000:02:00.0: [14e4:165b] type 00 class 0x020000
Apr  9 07:32:06 AnotherMass kernel: [    0.228985] pci 0000:02:00.0: reg 0x10: [mem 0xfe9f0000-0xfe9fffff 64bit]
Apr  9 07:32:06 AnotherMass kernel: [    0.229089] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  9 07:32:06 AnotherMass kernel: [    0.236326] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  9 07:32:06 AnotherMass kernel: [    0.236341] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.236441] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236452] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236455] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236457] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236459] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.236461] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
Apr  9 07:32:06 AnotherMass kernel: [    0.237436] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237508] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237578] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237644] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237698] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237742] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237785] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237829] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr  9 07:32:06 AnotherMass kernel: [    0.237955] ACPI: Enabled 4 GPEs in block 00 to 1F
Apr  9 07:32:06 AnotherMass kernel: [    0.237963] ACPI: \_SB_.PCI0: notify handler is installed
Apr  9 07:32:06 AnotherMass kernel: [    0.237997] Found 1 acpi root devices
Apr  9 07:32:06 AnotherMass kernel: [    0.238162] vgaarb: setting as boot device: PCI:0000:01:05.0
Apr  9 07:32:06 AnotherMass kernel: [    0.238166] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Apr  9 07:32:06 AnotherMass kernel: [    0.238169] vgaarb: loaded
Apr  9 07:32:06 AnotherMass kernel: [    0.238172] vgaarb: bridge control possible 0000:01:05.0
Apr  9 07:32:06 AnotherMass kernel: [    0.238370] SCSI subsystem initialized
Apr  9 07:32:06 AnotherMass kernel: [    0.238449] libata version 3.00 loaded.
Apr  9 07:32:06 AnotherMass kernel: [    0.238471] ACPI: bus type USB registered
Apr  9 07:32:06 AnotherMass kernel: [    0.238491] usbcore: registered new interface driver usbfs
Apr  9 07:32:06 AnotherMass kernel: [    0.238500] usbcore: registered new interface driver hub
Apr  9 07:32:06 AnotherMass kernel: [    0.238602] usbcore: registered new device driver usb
Apr  9 07:32:06 AnotherMass kernel: [    0.238796] PCI: Using ACPI for IRQ routing
Apr  9 07:32:06 AnotherMass kernel: [    0.246925] PCI: pci_cache_line_size set to 64 bytes
Apr  9 07:32:06 AnotherMass kernel: [    0.246970] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.246973] e820: reserve RAM buffer [mem 0xd7f90000-0xd7ffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.247076] NetLabel: Initializing
Apr  9 07:32:06 AnotherMass kernel: [    0.247079] NetLabel:  domain hash size = 128
Apr  9 07:32:06 AnotherMass kernel: [    0.247081] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  9 07:32:06 AnotherMass kernel: [    0.247094] NetLabel:  unlabeled traffic allowed by default
Apr  9 07:32:06 AnotherMass kernel: [    0.247213] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  9 07:32:06 AnotherMass kernel: [    0.247219] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr  9 07:32:06 AnotherMass kernel: [    0.249286] Switched to clocksource hpet
Apr  9 07:32:06 AnotherMass kernel: [    0.255191] AppArmor: AppArmor Filesystem Enabled
Apr  9 07:32:06 AnotherMass kernel: [    0.255236] pnp: PnP ACPI init
Apr  9 07:32:06 AnotherMass kernel: [    0.255256] ACPI: bus type PNP registered
Apr  9 07:32:06 AnotherMass kernel: [    0.255478] system 00:00: [mem 0xd8000000-0xdfffffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255485] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255545] pnp 00:01: [dma 4]
Apr  9 07:32:06 AnotherMass kernel: [    0.255568] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255602] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255663] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255688] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255729] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.255823] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255827] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.255831] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256008] system 00:07: [io  0x04d0-0x04d1] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256012] system 00:07: [io  0x040b] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256015] system 00:07: [io  0x04d6] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256019] system 00:07: [io  0x0c00-0x0c01] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256023] system 00:07: [io  0x0c14] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256026] system 00:07: [io  0x0c50-0x0c51] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256029] system 00:07: [io  0x0c52] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256033] system 00:07: [io  0x0c6c] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256036] system 00:07: [io  0x0c6f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256040] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256048] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256052] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256056] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256059] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256063] system 00:07: [io  0x0800-0x089f] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256066] system 00:07: [io  0x0b00-0x0b1f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256070] system 00:07: [io  0x0b20-0x0b3f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256073] system 00:07: [io  0x0900-0x090f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256077] system 00:07: [io  0x0910-0x091f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256081] system 00:07: [io  0xfe00-0xfefe] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256085] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256089] system 00:07: [mem 0xfec10000-0xfec1001f] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256093] system 00:07: [mem 0xfed80000-0xfed80fff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256097] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256160] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256165] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256283] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256288] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256292] system 00:09: [mem 0x00100000-0xd7ffffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256296] system 00:09: [mem 0xfec00000-0xffffffff] could not be reserved
Apr  9 07:32:06 AnotherMass kernel: [    0.256300] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr  9 07:32:06 AnotherMass kernel: [    0.256391] pnp: PnP ACPI: found 10 devices
Apr  9 07:32:06 AnotherMass kernel: [    0.256394] ACPI: bus type PNP unregistered
Apr  9 07:32:06 AnotherMass kernel: [    0.263537] pci 0000:00:01.0: PCI bridge to [bus 01]
Apr  9 07:32:06 AnotherMass kernel: [    0.263542] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263547] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263552] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.263558] pci 0000:00:06.0: PCI bridge to [bus 02]
Apr  9 07:32:06 AnotherMass kernel: [    0.263562] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263568] pci 0000:00:14.4: PCI bridge to [bus 03]
Apr  9 07:32:06 AnotherMass kernel: [    0.263581] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.263584] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263586] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263588] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263590] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263593] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263595] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263597] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 07:32:06 AnotherMass kernel: [    0.263600] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263602] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Apr  9 07:32:06 AnotherMass kernel: [    0.263604] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263606] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263608] pci_bus 0000:03: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263611] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xffffffff]
Apr  9 07:32:06 AnotherMass kernel: [    0.263647] NET: Registered protocol family 2
Apr  9 07:32:06 AnotherMass kernel: [    0.263912] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264211] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264647] TCP: Hash tables configured (established 65536 bind 65536)
Apr  9 07:32:06 AnotherMass kernel: [    0.264725] TCP: reno registered
Apr  9 07:32:06 AnotherMass kernel: [    0.264744] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264826] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    0.264992] NET: Registered protocol family 1
Apr  9 07:32:06 AnotherMass kernel: [    0.265009] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Apr  9 07:32:06 AnotherMass kernel: [    1.245263] pci 0000:01:05.0: Video device with shadowed ROM
Apr  9 07:32:06 AnotherMass kernel: [    1.245271] PCI: CLS 64 bytes, default 64
Apr  9 07:32:06 AnotherMass kernel: [    1.245354] Trying to unpack rootfs image as initramfs...
Apr  9 07:32:06 AnotherMass kernel: [    1.621606] Freeing initrd memory: 19268K (ffff880035a4e000 - ffff880036d1f000)
Apr  9 07:32:06 AnotherMass kernel: [    1.621853] PCI-DMA: Disabling AGP.
Apr  9 07:32:06 AnotherMass kernel: [    1.621971] PCI-DMA: aperture base @ cc000000 size 65536 KB
Apr  9 07:32:06 AnotherMass kernel: [    1.621975] PCI-DMA: using GART IOMMU.
Apr  9 07:32:06 AnotherMass kernel: [    1.621979] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr  9 07:32:06 AnotherMass kernel: [    1.626021] LVT offset 1 assigned for vector 0x400
Apr  9 07:32:06 AnotherMass kernel: [    1.626040] IBS: LVT offset 1 assigned
Apr  9 07:32:06 AnotherMass kernel: [    1.626077] perf: AMD IBS detected (0x0000001f)
Apr  9 07:32:06 AnotherMass kernel: [    1.626148] microcode: CPU0: patch_level=0x010000c8
Apr  9 07:32:06 AnotherMass kernel: [    1.626161] microcode: CPU1: patch_level=0x010000c8
Apr  9 07:32:06 AnotherMass kernel: [    1.626252] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  9 07:32:06 AnotherMass kernel: [    1.626257] Scanning for low memory corruption every 60 seconds
Apr  9 07:32:06 AnotherMass kernel: [    1.626540] Initialise system trusted keyring
Apr  9 07:32:06 AnotherMass kernel: [    1.626597] audit: initializing netlink socket (disabled)
Apr  9 07:32:06 AnotherMass kernel: [    1.626615] type=2000 audit(1428561094.528:1): initialized
Apr  9 07:32:06 AnotherMass kernel: [    1.660089] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  9 07:32:06 AnotherMass kernel: [    1.661755] zbud: loaded
Apr  9 07:32:06 AnotherMass kernel: [    1.662058] VFS: Disk quotas dquot_6.5.2
Apr  9 07:32:06 AnotherMass kernel: [    1.662126] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  9 07:32:06 AnotherMass kernel: [    1.662778] fuse init (API version 7.22)
Apr  9 07:32:06 AnotherMass kernel: [    1.662960] msgmni has been set to 11680
Apr  9 07:32:06 AnotherMass kernel: [    1.663035] Key type big_key registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663638] Key type asymmetric registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663641] Asymmetric key parser 'x509' registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663678] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Apr  9 07:32:06 AnotherMass kernel: [    1.663727] io scheduler noop registered
Apr  9 07:32:06 AnotherMass kernel: [    1.663730] io scheduler deadline registered (default)
Apr  9 07:32:06 AnotherMass kernel: [    1.663759] io scheduler cfq registered
Apr  9 07:32:06 AnotherMass kernel: [    1.664031] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [    1.664105] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
Apr  9 07:32:06 AnotherMass kernel: [    1.664110] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Apr  9 07:32:06 AnotherMass kernel: [    1.664114] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
Apr  9 07:32:06 AnotherMass kernel: [    1.664127] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  9 07:32:06 AnotherMass kernel: [    1.664143] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  9 07:32:06 AnotherMass kernel: [    1.664182] vesafb: mode is 1152x864x32, linelength=4608, pages=0
Apr  9 07:32:06 AnotherMass kernel: [    1.664185] vesafb: scrolling: redraw
Apr  9 07:32:06 AnotherMass kernel: [    1.664188] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Apr  9 07:32:06 AnotherMass kernel: [    1.664379] vesafb: framebuffer at 0xf0000000, mapped to 0xffffc90010e80000, using 3904k, total 3904k
Apr  9 07:32:06 AnotherMass kernel: [    1.819607] Console: switching to colour frame buffer device 144x54
Apr  9 07:32:06 AnotherMass kernel: [    1.976152] fb0: VESA VGA frame buffer device
Apr  9 07:32:06 AnotherMass kernel: [    1.977219] ipmi message handler version 39.2
Apr  9 07:32:06 AnotherMass kernel: [    1.978288] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr  9 07:32:06 AnotherMass kernel: [    1.980166] ACPI: Power Button [PWRB]
Apr  9 07:32:06 AnotherMass kernel: [    1.981085] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  9 07:32:06 AnotherMass kernel: [    1.982768] ACPI: Power Button [PWRF]
Apr  9 07:32:06 AnotherMass kernel: [    1.983666] ACPI: processor limited to max C-state 1
Apr  9 07:32:06 AnotherMass kernel: [    1.984913] ERST: Failed to get Error Log Address Range.
Apr  9 07:32:06 AnotherMass kernel: [    2.000633] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
Apr  9 07:32:06 AnotherMass kernel: [    2.002842] GHES: APEI firmware first mode is enabled by WHEA _OSC.
Apr  9 07:32:06 AnotherMass kernel: [    2.004472] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  9 07:32:06 AnotherMass kernel: [    2.007814] Linux agpgart interface v0.103
Apr  9 07:32:06 AnotherMass kernel: [    2.010850] brd: module loaded
Apr  9 07:32:06 AnotherMass kernel: [    2.012951] loop: module loaded
Apr  9 07:32:06 AnotherMass kernel: [    2.014073] libphy: Fixed MDIO Bus: probed
Apr  9 07:32:06 AnotherMass kernel: [    2.015101] tun: Universal TUN/TAP device driver, 1.6
Apr  9 07:32:06 AnotherMass kernel: [    2.016259] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  9 07:32:06 AnotherMass kernel: [    2.017828] PPP generic driver version 2.4.2
Apr  9 07:32:06 AnotherMass kernel: [    2.018947] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  9 07:32:06 AnotherMass kernel: [    2.020484] ehci-pci: EHCI PCI platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.021692] QUIRK: Enable AMD PLL fix
Apr  9 07:32:06 AnotherMass kernel: [    2.021715] ehci-pci 0000:00:12.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.022908] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr  9 07:32:06 AnotherMass kernel: [    2.024637] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.026646] ehci-pci 0000:00:12.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.027763] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe6ff800
Apr  9 07:32:06 AnotherMass kernel: [    2.040505] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.041894] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.043439] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.045124] usb usb1: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.101215] usb usb1: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.157623] usb usb1: SerialNumber: 0000:00:12.2
Apr  9 07:32:06 AnotherMass kernel: [    2.213611] hub 1-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.269347] hub 1-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.324358] ehci-pci 0000:00:13.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.379222] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr  9 07:32:06 AnotherMass kernel: [    2.434911] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.491516] ehci-pci 0000:00:13.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.547909] ehci-pci 0000:00:13.2: irq 17, io mem 0xfe6ff400
Apr  9 07:32:06 AnotherMass kernel: [    2.616221] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.672146] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.728161] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.784912] usb usb2: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.841679] usb usb2: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.898910] usb usb2: SerialNumber: 0000:00:13.2
Apr  9 07:32:06 AnotherMass kernel: [    2.955230] tsc: Refined TSC clocksource calibration: 2196.341 MHz
Apr  9 07:32:06 AnotherMass kernel: [    2.956190] hub 2-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.956198] hub 2-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.956500] ehci-pci 0000:00:16.2: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.956505] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr  9 07:32:06 AnotherMass kernel: [    2.956508] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 07:32:06 AnotherMass kernel: [    2.956524] ehci-pci 0000:00:16.2: debug port 1
Apr  9 07:32:06 AnotherMass kernel: [    2.956571] ehci-pci 0000:00:16.2: irq 17, io mem 0xfe6ff000
Apr  9 07:32:06 AnotherMass kernel: [    2.964061] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr  9 07:32:06 AnotherMass kernel: [    2.964121] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Apr  9 07:32:06 AnotherMass kernel: [    2.964123] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    2.964124] usb usb3: Product: EHCI Host Controller
Apr  9 07:32:06 AnotherMass kernel: [    2.964125] usb usb3: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    2.964126] usb usb3: SerialNumber: 0000:00:16.2
Apr  9 07:32:06 AnotherMass kernel: [    2.964251] hub 3-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    2.964258] hub 3-0:1.0: 4 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    2.964382] ehci-platform: EHCI generic platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964396] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964396] ohci-pci: OHCI PCI platform driver
Apr  9 07:32:06 AnotherMass kernel: [    2.964569] ohci-pci 0000:00:12.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    2.964575] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr  9 07:32:06 AnotherMass kernel: [    2.964605] ohci-pci 0000:00:12.0: irq 18, io mem 0xfe6fe000
Apr  9 07:32:06 AnotherMass kernel: [    3.024076] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    3.024077] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    3.024079] usb usb4: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    3.024080] usb usb4: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    3.024081] usb usb4: SerialNumber: 0000:00:12.0
Apr  9 07:32:06 AnotherMass kernel: [    3.024212] hub 4-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    3.024227] hub 4-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    3.024511] ohci-pci 0000:00:13.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    3.024516] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr  9 07:32:06 AnotherMass kernel: [    3.024538] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe6fd000
Apr  9 07:32:06 AnotherMass kernel: [    4.635306] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    4.684552] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    4.734316] usb usb5: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    4.784777] usb usb5: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    4.834651] usb usb5: SerialNumber: 0000:00:13.0
Apr  9 07:32:06 AnotherMass kernel: [    4.884203] hub 5-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    4.895117] usb 4-2: new low-speed USB device number 2 using ohci-pci
Apr  9 07:32:06 AnotherMass kernel: [    4.982982] hub 5-0:1.0: 5 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    5.032667] ohci-pci 0000:00:16.0: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    5.082623] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 6
Apr  9 07:32:06 AnotherMass kernel: [    5.104121] usb 4-2: New USB device found, idVendor=04f3, idProduct=0103
Apr  9 07:32:06 AnotherMass kernel: [    5.104123] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  9 07:32:06 AnotherMass kernel: [    5.235932] ohci-pci 0000:00:16.0: irq 18, io mem 0xfe6fc000
Apr  9 07:32:06 AnotherMass kernel: [    5.346916] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Apr  9 07:32:06 AnotherMass kernel: [    5.397902] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  9 07:32:06 AnotherMass kernel: [    5.449519] usb usb6: Product: OHCI PCI host controller
Apr  9 07:32:06 AnotherMass kernel: [    5.501535] usb usb6: Manufacturer: Linux 3.13.0-48-generic ohci_hcd
Apr  9 07:32:06 AnotherMass kernel: [    5.553470] usb usb6: SerialNumber: 0000:00:16.0
Apr  9 07:32:06 AnotherMass kernel: [    5.605094] hub 6-0:1.0: USB hub found
Apr  9 07:32:06 AnotherMass kernel: [    5.655801] hub 6-0:1.0: 4 ports detected
Apr  9 07:32:06 AnotherMass kernel: [    5.706177] Switched to clocksource tsc
Apr  9 07:32:06 AnotherMass kernel: [    5.706249] ohci-platform: OHCI generic platform driver
Apr  9 07:32:06 AnotherMass kernel: [    5.706263] uhci_hcd: USB Universal Host Controller Interface driver
Apr  9 07:32:06 AnotherMass kernel: [    5.706329] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr  9 07:32:06 AnotherMass kernel: [    6.730619] i8042: No controller found
Apr  9 07:32:06 AnotherMass kernel: [    6.781411] mousedev: PS/2 mouse device common for all mice
Apr  9 07:32:06 AnotherMass kernel: [    6.833174] rtc_cmos 00:02: RTC can wake from S4
Apr  9 07:32:06 AnotherMass kernel: [    6.884178] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Apr  9 07:32:06 AnotherMass kernel: [    6.934800] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  9 07:32:06 AnotherMass kernel: [    6.986399] device-mapper: uevent: version 1.0.3
Apr  9 07:32:06 AnotherMass kernel: [    7.038139] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Apr  9 07:32:06 AnotherMass kernel: [    7.090830] ledtrig-cpu: registered to indicate activity on CPUs
Apr  9 07:32:06 AnotherMass kernel: [    7.143821] TCP: cubic registered
Apr  9 07:32:06 AnotherMass kernel: [    7.196068] NET: Registered protocol family 10
Apr  9 07:32:06 AnotherMass kernel: [    7.248431] NET: Registered protocol family 17
Apr  9 07:32:06 AnotherMass kernel: [    7.299969] Key type dns_resolver registered
Apr  9 07:32:06 AnotherMass kernel: [    7.351855] Loading compiled-in X.509 certificates
Apr  9 07:32:06 AnotherMass kernel: [    7.405274] Loaded X.509 cert 'Magrathea: Glacier signing key: 4eb2de249917cbf39cb85692e54cebade594d680'
Apr  9 07:32:06 AnotherMass kernel: [    7.459440] registered taskstats version 1
Apr  9 07:32:06 AnotherMass kernel: [    7.515805] Key type trusted registered
Apr  9 07:32:06 AnotherMass kernel: [    7.573196] Key type encrypted registered
Apr  9 07:32:06 AnotherMass kernel: [    7.626460] AppArmor: AppArmor sha1 policy hashing enabled
Apr  9 07:32:06 AnotherMass kernel: [    7.680578] IMA: No TPM chip found, activating TPM-bypass!
Apr  9 07:32:06 AnotherMass kernel: [    7.735314] regulator-dummy: disabling
Apr  9 07:32:06 AnotherMass kernel: [    7.788932]   Magic number: 11:773:518
Apr  9 07:32:06 AnotherMass kernel: [    7.842426] rtc_cmos 00:02: setting system clock to 2015-04-09 06:31:41 UTC (1428561101)
Apr  9 07:32:06 AnotherMass kernel: [    7.896864] acpi-cpufreq: overriding BIOS provided _PSD data
Apr  9 07:32:06 AnotherMass kernel: [    7.951310] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  9 07:32:06 AnotherMass kernel: [    8.006537] EDD information not available.
Apr  9 07:32:06 AnotherMass kernel: [    8.061721] PM: Hibernation image not present or could not be loaded.
Apr  9 07:32:06 AnotherMass kernel: [    8.063444] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Apr  9 07:32:06 AnotherMass kernel: [    8.120603] Write protecting the kernel read-only data: 12288k
Apr  9 07:32:06 AnotherMass kernel: [    8.180573] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
Apr  9 07:32:06 AnotherMass kernel: [    8.240618] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
Apr  9 07:32:06 AnotherMass kernel: [    8.374245] systemd-udevd[105]: starting version 204
Apr  9 07:32:06 AnotherMass kernel: [    8.436246] md: linear personality registered for level -1
Apr  9 07:32:06 AnotherMass kernel: [    8.494666] pps_core: LinuxPPS API ver. 1 registered
Apr  9 07:32:06 AnotherMass kernel: [    8.553087] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Apr  9 07:32:06 AnotherMass kernel: [    8.615703] md: multipath personality registered for level -4
Apr  9 07:32:06 AnotherMass kernel: [    8.684730] hidraw: raw HID events driver (C) Jiri Kosina
Apr  9 07:32:06 AnotherMass kernel: [    8.751775] md: raid0 personality registered for level 0
Apr  9 07:32:06 AnotherMass kernel: [    8.811959] PTP clock support registered
Apr  9 07:32:06 AnotherMass kernel: [    8.874981] ahci 0000:00:11.0: version 3.0
Apr  9 07:32:06 AnotherMass kernel: [    8.875220] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [    8.875330] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Apr  9 07:32:06 AnotherMass kernel: [    8.936619] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
Apr  9 07:32:06 AnotherMass kernel: [    8.997795] tg3.c:v3.134 (Sep 16, 2013)
Apr  9 07:32:06 AnotherMass kernel: [    9.058490] md: raid1 personality registered for level 1
Apr  9 07:32:06 AnotherMass kernel: [    9.124996] scsi0 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.185051] scsi1 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.188909] raid6: sse2x1    2994 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.256870] raid6: sse2x2    4707 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.324840] raid6: sse2x4    5532 MB/s
Apr  9 07:32:06 AnotherMass kernel: [    9.324841] raid6: using algorithm sse2x4 (5532 MB/s)
Apr  9 07:32:06 AnotherMass kernel: [    9.324842] raid6: using intx1 recovery algorithm
Apr  9 07:32:06 AnotherMass kernel: [    9.531779] scsi2 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589106] xor: measuring software checksum speed
Apr  9 07:32:06 AnotherMass kernel: [    9.589329] scsi3 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589404] scsi4 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589477] scsi5 : ahci
Apr  9 07:32:06 AnotherMass kernel: [    9.589519] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589522] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589525] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589528] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589531] ata5: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff00 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.589533] ata6: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6fff80 irq 41
Apr  9 07:32:06 AnotherMass kernel: [    9.593108] usbcore: registered new interface driver usbhid
Apr  9 07:32:06 AnotherMass kernel: [    9.593110] usbhid: USB HID core driver
Apr  9 07:32:06 AnotherMass kernel: [   10.234490] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input2
Apr  9 07:32:06 AnotherMass kernel: [   10.268367]    prefetch64-sse:  9035.000 MB/sec
Apr  9 07:32:06 AnotherMass kernel: [   10.308348]    generic_sse:  8511.000 MB/sec
Apr  9 07:32:06 AnotherMass kernel: [   10.308349] xor: using function: prefetch64-sse (9035.000 MB/sec)
Apr  9 07:32:06 AnotherMass kernel: [   10.445001] hid-generic 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:12.0-2/input0
Apr  9 07:32:06 AnotherMass kernel: [   10.500019] async_tx: api initialized (async)
Apr  9 07:32:06 AnotherMass kernel: [   10.527222] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 38:ea:a7:a3:2a:32
Apr  9 07:32:06 AnotherMass kernel: [   10.527224] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Apr  9 07:32:06 AnotherMass kernel: [   10.527226] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  9 07:32:06 AnotherMass kernel: [   10.527227] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  9 07:32:06 AnotherMass kernel: [   10.784343] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input3
Apr  9 07:32:06 AnotherMass kernel: [   10.842830] ata5: SATA link down (SStatus 0 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   10.902082] hid-generic 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:12.0-2/input1
Apr  9 07:32:06 AnotherMass kernel: [   10.967168] md: raid6 personality registered for level 6
Apr  9 07:32:06 AnotherMass kernel: [   11.026952] md: raid5 personality registered for level 5
Apr  9 07:32:06 AnotherMass kernel: [   11.085749] md: raid4 personality registered for level 4
Apr  9 07:32:06 AnotherMass kernel: [   11.116037] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116071] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116097] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.116594] ata4.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116596] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.116603] ata3.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116604] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.116652] ata2.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.116653] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.117153] ata4.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.117176] ata3.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.117185] ata2.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180005] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.180037] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 07:32:06 AnotherMass kernel: [   11.180469] ata6.00: ATA-9: SanDisk SDSSDRC032G, 3.0.0, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180471] ata6.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr  9 07:32:06 AnotherMass kernel: [   11.180576] ata1.00: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.180578] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 07:32:06 AnotherMass kernel: [   11.181181] ata1.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.181327] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.181609] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.181610] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.181649] sd 0:0:0:0: [sda] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.181651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.181668] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182050] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182193] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182303] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182405] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182506] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182606] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.182706] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.182752] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182753] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182771] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182772] sd 2:0:0:0: [sdc] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182810] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.182811] sd 1:0:0:0: [sdb] 4096-byte physical blocks
Apr  9 07:32:06 AnotherMass kernel: [   11.182853] sd 3:0:0:0: [sdd] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182855] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182877] sd 2:0:0:0: [sdc] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182879] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182908] sd 3:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182947] sd 1:0:0:0: [sdb] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.182949] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.182958] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.182995] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.184028] ata6.00: configured for UDMA/133
Apr  9 07:32:06 AnotherMass kernel: [   11.184136] scsi 5:0:0:0: Direct-Access     ATA      SanDisk SDSSDRC0 3.0. PQ: 0 ANSI: 5
Apr  9 07:32:06 AnotherMass kernel: [   11.184274] sd 5:0:0:0: Attached scsi generic sg4 type 0
Apr  9 07:32:06 AnotherMass kernel: [   11.184330] sd 5:0:0:0: [sde] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
Apr  9 07:32:06 AnotherMass kernel: [   11.184381] sd 5:0:0:0: [sde] Write Protect is off
Apr  9 07:32:06 AnotherMass kernel: [   11.184383] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Apr  9 07:32:06 AnotherMass kernel: [   11.184399] sd 5:0:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 07:32:06 AnotherMass kernel: [   11.185475]  sde: sde1 sde2 < sde5 >
Apr  9 07:32:06 AnotherMass kernel: [   11.185829] sd 5:0:0:0: [sde] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.245378]  sdb: sdb1
Apr  9 07:32:06 AnotherMass kernel: [   11.245632] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.252015]  sda: sda1
Apr  9 07:32:06 AnotherMass kernel: [   11.252266] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.809616]  sdc: sdc1
Apr  9 07:32:06 AnotherMass kernel: [   11.809859] sd 2:0:0:0: [sdc] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   11.881694]  sdd: sdd1
Apr  9 07:32:06 AnotherMass kernel: [   11.881942] sd 3:0:0:0: [sdd] Attached SCSI disk
Apr  9 07:32:06 AnotherMass kernel: [   14.386338] [sched_delayed] sched: RT throttling activated
Apr  9 07:32:06 AnotherMass kernel: [   14.439531] md: raid10 personality registered for level 10
Apr  9 07:32:06 AnotherMass kernel: [   14.450149] random: nonblocking pool is initialized
Apr  9 07:32:06 AnotherMass kernel: [   14.551681] md: bind<sdd1>
Apr  9 07:32:06 AnotherMass kernel: [   14.560761] md: bind<sda1>
Apr  9 07:32:06 AnotherMass kernel: [   14.572103] md: bind<sdc1>
Apr  9 07:32:06 AnotherMass kernel: [   14.576350] md: bind<sdb1>
Apr  9 07:32:06 AnotherMass kernel: [   14.994158] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Apr  9 07:32:06 AnotherMass kernel: [   15.604900] init: plymouth-upstart-bridge main process (195) terminated with status 1
Apr  9 07:32:06 AnotherMass kernel: [   15.659228] init: plymouth-upstart-bridge main process ended, respawning
Apr  9 07:32:06 AnotherMass kernel: [   15.719771] init: plymouth-upstart-bridge main process (205) terminated with status 1
Apr  9 07:32:06 AnotherMass kernel: [   15.773842] init: plymouth-upstart-bridge main process ended, respawning
Apr  9 07:32:06 AnotherMass kernel: [   15.832275] init: plymouth-upstart-bridge main process (208) terminated with status 1
Apr  9 07:32:06 AnotherMass kernel: [   15.884796] init: plymouth-upstart-bridge main process ended, respawning
Apr  9 07:32:06 AnotherMass kernel: [   18.939514] Adding 6157308k swap on /dev/sde5.  Priority:-1 extents:1 across:6157308k SSFS
Apr  9 07:32:06 AnotherMass kernel: [   19.003988] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
Apr  9 07:32:06 AnotherMass kernel: [   19.974813] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 07:32:06 AnotherMass kernel: [   20.059212] systemd-udevd[404]: starting version 204
Apr  9 07:32:06 AnotherMass kernel: [   20.156713] lp: driver loaded but no devices found
Apr  9 07:32:06 AnotherMass kernel: [   20.168428] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  9 07:32:06 AnotherMass kernel: [   20.184769] ppdev: user-space parallel port driver
Apr  9 07:32:06 AnotherMass kernel: [   20.244673] [drm] Initialized drm 1.1.0 20060810
Apr  9 07:32:06 AnotherMass kernel: [   20.258936] type=1400 audit(1428561113.917:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.258945] type=1400 audit(1428561113.917:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.258950] type=1400 audit(1428561113.917:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259542] type=1400 audit(1428561113.921:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259549] type=1400 audit(1428561113.921:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.259841] type=1400 audit(1428561113.921:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   20.310762] [drm] radeon kernel modesetting enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.310847] checking generic (f0000000 3d0000) vs hw (f0000000 8000000)
Apr  9 07:32:06 AnotherMass kernel: [   20.310849] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
Apr  9 07:32:06 AnotherMass kernel: [   20.310877] Console: switching to colour dummy device 80x25
Apr  9 07:32:06 AnotherMass kernel: [   20.312545] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
Apr  9 07:32:06 AnotherMass kernel: [   20.312563] [drm] register mmio base: 0xFE8F0000
Apr  9 07:32:06 AnotherMass kernel: [   20.312564] [drm] register mmio size: 65536
Apr  9 07:32:06 AnotherMass kernel: [   20.313289] ATOM BIOS: AMD_1407_150
Apr  9 07:32:06 AnotherMass kernel: [   20.313320] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
Apr  9 07:32:06 AnotherMass kernel: [   20.313322] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Apr  9 07:32:06 AnotherMass kernel: [   20.313327] [drm] Detected VRAM RAM=128M, BAR=128M
Apr  9 07:32:06 AnotherMass kernel: [   20.313329] [drm] RAM width 32bits DDR
Apr  9 07:32:06 AnotherMass kernel: [   20.313575] [TTM] Zone  kernel: Available graphics memory: 2991704 kiB
Apr  9 07:32:06 AnotherMass kernel: [   20.313576] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Apr  9 07:32:06 AnotherMass kernel: [   20.313578] [TTM] Initializing pool allocator
Apr  9 07:32:06 AnotherMass kernel: [   20.313583] [TTM] Initializing DMA pool allocator
Apr  9 07:32:06 AnotherMass kernel: [   20.313605] [drm] radeon: 128M of VRAM memory ready
Apr  9 07:32:06 AnotherMass kernel: [   20.313606] [drm] radeon: 512M of GTT memory ready.
Apr  9 07:32:06 AnotherMass kernel: [   20.313616] [drm] Loading RS780 Microcode
Apr  9 07:32:06 AnotherMass kernel: [   20.314490] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr  9 07:32:06 AnotherMass kernel: [   20.314568] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
Apr  9 07:32:06 AnotherMass kernel: [   20.316416] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Apr  9 07:32:06 AnotherMass kernel: [   20.316652] sp5100_tco: PCI Revision ID: 0x42
Apr  9 07:32:06 AnotherMass kernel: [   20.316705] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
Apr  9 07:32:06 AnotherMass kernel: [   20.316717] sp5100_tco: Last reboot was not triggered by watchdog.
Apr  9 07:32:06 AnotherMass kernel: [   20.316792] sp5100_tco: initialized (0xffffc90000c64b00). heartbeat=60 sec (nowayout=0)
Apr  9 07:32:06 AnotherMass kernel: [   20.332458] [drm] GART: num cpu pages 131072, num gpu pages 131072
Apr  9 07:32:06 AnotherMass kernel: [   20.344166] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Apr  9 07:32:06 AnotherMass kernel: [   20.344744] MCE: In-kernel MCE decoding enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.345128] radeon 0000:01:05.0: WB enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.345155] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880035b2cc00
Apr  9 07:32:06 AnotherMass kernel: [   20.345167] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880035b2cc0c
Apr  9 07:32:06 AnotherMass kernel: [   20.347320] EDAC MC: Ver: 3.0.0
Apr  9 07:32:06 AnotherMass kernel: [   20.347621] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  9 07:32:06 AnotherMass kernel: [   20.347624] [drm] Driver supports precise vblank timestamp query.
Apr  9 07:32:06 AnotherMass kernel: [   20.347628] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
Apr  9 07:32:06 AnotherMass kernel: [   20.347647] [drm] radeon: irq initialized.
Apr  9 07:32:06 AnotherMass kernel: [   20.351762] tg3 0000:02:00.0: irq 42 for MSI/MSI-X
Apr  9 07:32:06 AnotherMass kernel: [   20.354383] AMD64 EDAC driver v3.4.0
Apr  9 07:32:06 AnotherMass kernel: [   20.354423] EDAC amd64: DRAM ECC enabled.
Apr  9 07:32:06 AnotherMass kernel: [   20.354429] EDAC amd64: F10h detected (node 0).
Apr  9 07:32:06 AnotherMass kernel: [   20.354444] EDAC MC: DCT0 chip selects:
Apr  9 07:32:06 AnotherMass kernel: [   20.354446] EDAC amd64: MC: 0:  1024MB 1:  1024MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354448] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354449] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354450] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354452] EDAC MC: DCT1 chip selects:
Apr  9 07:32:06 AnotherMass kernel: [   20.354453] EDAC amd64: MC: 0:  2048MB 1:  2048MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354454] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354456] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354457] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 07:32:06 AnotherMass kernel: [   20.354458] EDAC amd64: using x4 syndromes.
Apr  9 07:32:06 AnotherMass kernel: [   20.354460] EDAC amd64: MCT channel count: 2
Apr  9 07:32:06 AnotherMass kernel: [   20.354483] EDAC amd64: CS0: Unbuffered DDR3 RAM
Apr  9 07:32:06 AnotherMass kernel: [   20.354484] EDAC amd64: CS1: Unbuffered DDR3 RAM
Apr  9 07:32:06 AnotherMass kernel: [   20.357884] EDAC MC0: Giving out device to module amd64_edac controller F10h: DEV 0000:00:18.2 (INTERRUPT)
Apr  9 07:32:06 AnotherMass kernel: [   20.358660] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
Apr  9 07:32:06 AnotherMass kernel: [   20.456506] kvm: Nested Virtualization enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.456512] kvm: Nested Paging enabled
Apr  9 07:32:06 AnotherMass kernel: [   20.578826] [drm] ring test on 0 succeeded in 1 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.578872] [drm] ring test on 3 succeeded in 2 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.579010] [drm] Enabling audio 0 support
Apr  9 07:32:06 AnotherMass kernel: [   20.579084] [drm] ib test on ring 0 succeeded in 0 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.579142] [drm] ib test on ring 3 succeeded in 0 usecs
Apr  9 07:32:06 AnotherMass kernel: [   20.582862] [drm] Radeon Display Connectors
Apr  9 07:32:06 AnotherMass kernel: [   20.582864] [drm] Connector 0:
Apr  9 07:32:06 AnotherMass kernel: [   20.582866] [drm]   VGA-1
Apr  9 07:32:06 AnotherMass kernel: [   20.582868] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Apr  9 07:32:06 AnotherMass kernel: [   20.582869] [drm]   Encoders:
Apr  9 07:32:06 AnotherMass kernel: [   20.582870] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Apr  9 07:32:06 AnotherMass kernel: [   20.582919] [drm] radeon: power management initialized
Apr  9 07:32:06 AnotherMass kernel: [   20.774447] [drm] fb mappable at 0xF0141000
Apr  9 07:32:06 AnotherMass kernel: [   20.774449] [drm] vram apper at 0xF0000000
Apr  9 07:32:06 AnotherMass kernel: [   20.774450] [drm] size 5324800
Apr  9 07:32:06 AnotherMass kernel: [   20.774451] [drm] fb depth is 24
Apr  9 07:32:06 AnotherMass kernel: [   20.774452] [drm]    pitch is 5888
Apr  9 07:32:06 AnotherMass kernel: [   20.775195] fbcon: radeondrmfb (fb0) is primary device
Apr  9 07:32:06 AnotherMass kernel: [   20.791924] Console: switching to colour frame buffer device 180x56
Apr  9 07:32:06 AnotherMass kernel: [   20.852674] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
Apr  9 07:32:06 AnotherMass kernel: [   20.852676] radeon 0000:01:05.0: registered panic notifier
Apr  9 07:32:06 AnotherMass kernel: [   20.852700] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0
Apr  9 07:32:06 AnotherMass kernel: [   21.126559] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 07:32:06 AnotherMass kernel: [   23.545161] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
Apr  9 07:32:06 AnotherMass kernel: [   23.545167] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
Apr  9 07:32:06 AnotherMass kernel: [   23.545189] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  9 07:32:06 AnotherMass kernel: [   32.893814] init: failsafe main process (906) killed by TERM signal
Apr  9 07:32:06 AnotherMass kernel: [   33.035405] Bluetooth: Core ver 2.17
Apr  9 07:32:06 AnotherMass kernel: [   33.035433] NET: Registered protocol family 31
Apr  9 07:32:06 AnotherMass kernel: [   33.035435] Bluetooth: HCI device and connection manager initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035447] Bluetooth: HCI socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035450] Bluetooth: L2CAP socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.035454] Bluetooth: SCO socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.067957] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  9 07:32:06 AnotherMass kernel: [   33.067962] Bluetooth: BNEP filters: protocol multicast
Apr  9 07:32:06 AnotherMass kernel: [   33.067973] Bluetooth: BNEP socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106535] Bluetooth: RFCOMM TTY layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106554] Bluetooth: RFCOMM socket layer initialized
Apr  9 07:32:06 AnotherMass kernel: [   33.106565] Bluetooth: RFCOMM ver 1.11
Apr  9 07:32:06 AnotherMass rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Apr  9 07:32:06 AnotherMass NetworkManager[1015]:    keyfile:     read connection 'Wired connection'
Apr  9 07:32:06 AnotherMass NetworkManager[1015]:    SCPlugin-Ofono: (536887584) ... get_connections.
Apr  9 07:32:06 AnotherMass NetworkManager[1015]:    SCPlugin-Ofono: (536887584) connections count: 0
Apr  9 07:32:06 AnotherMass NetworkManager[1015]:    Ifupdown: get unmanaged devices count: 1
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  9 07:32:06 AnotherMass kernel: [   33.217119] type=1400 audit(1428561126.880:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1049 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   33.217129] type=1400 audit(1428561126.880:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1049 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   33.217719] type=1400 audit(1428561126.880:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1049 comm="apparmor_parser"
Apr  9 07:32:06 AnotherMass kernel: [   33.218489] init: plexmediaserver main process (923) terminated with status 255
Apr  9 07:32:06 AnotherMass kernel: [   33.218501] init: plexmediaserver main process ended, respawning
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> Networking is disabled by state file
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <warn> failed to allocate link cache: (-12) Object not found
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> (eth0): carrier is ON
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> urfkill disappeared from the bus
Apr  9 07:32:06 AnotherMass NetworkManager[1015]: <info> ModemManager available in the bus
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Found user 'avahi' (UID 108) and group 'avahi' (GID 120).
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Successfully dropped root privileges.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: avahi-daemon 0.6.31 starting up.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Successfully called chroot().
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Successfully dropped remaining capabilities.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Loading service file /services/afpd.service.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Loading service file /services/udisks.service.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::3aea:a7ff:fea3:2a32.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: New relevant interface eth0.IPv6 for mDNS.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.6.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: New relevant interface eth0.IPv4 for mDNS.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Network interface enumeration completed.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Registering new address record for fe80::3aea:a7ff:fea3:2a32 on eth0.*.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Registering new address record for 192.168.2.6 on eth0.IPv4.
Apr  9 07:32:06 AnotherMass avahi-daemon[1060]: Registering HINFO record with values 'X86_64'/'LINUX'.
Apr  9 07:32:07 AnotherMass kernel: [   33.349340] type=1400 audit(1428561127.012:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349352] type=1400 audit(1428561127.012:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349357] type=1400 audit(1428561127.012:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349920] type=1400 audit(1428561127.012:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.349925] type=1400 audit(1428561127.012:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.357589] type=1400 audit(1428561127.020:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1110 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass kernel: [   33.357600] type=1400 audit(1428561127.020:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1110 comm="apparmor_parser"
Apr  9 07:32:07 AnotherMass anacron[1255]: Anacron 2.3 started on 2015-04-09
Apr  9 07:32:07 AnotherMass anacron[1255]: Will run job `cron.daily' in 5 min.
Apr  9 07:32:07 AnotherMass anacron[1255]: Will run job `cron.weekly' in 10 min.
Apr  9 07:32:07 AnotherMass anacron[1255]: Jobs will be executed sequentially
Apr  9 07:32:07 AnotherMass acpid: starting up with netlink and the input layer
Apr  9 07:32:07 AnotherMass cron[1181]: (CRON) INFO (pidfile fd = 3)
Apr  9 07:32:07 AnotherMass acpid: 9 rules loaded
Apr  9 07:32:07 AnotherMass acpid: waiting for events: event logging is off
Apr  9 07:32:07 AnotherMass whoopsie[1236]: whoopsie 0.2.24.6 starting up.
Apr  9 07:32:07 AnotherMass whoopsie[1236]: Using lock path: /var/lock/whoopsie/lock
Apr  9 07:32:07 AnotherMass cron[1258]: (CRON) STARTUP (fork ok)
Apr  9 07:32:07 AnotherMass cron[1258]: (CRON) INFO (Running @reboot jobs)
Apr  9 07:32:07 AnotherMass avahi-daemon[1060]: Server startup complete. Host name is AnotherMass.local. Local service cookie is 2275309450.
Apr  9 07:32:07 AnotherMass NetworkManager[1015]: <info> NetworkManager state is now ASLEEP
Apr  9 07:32:07 AnotherMass whoopsie[1270]: offline
Apr  9 07:32:07 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Apr  9 07:32:07 AnotherMass accounts-daemon[1329]: started daemon version 0.6.35
Apr  9 07:32:07 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.Accounts'
Apr  9 07:32:08 AnotherMass kernel: [   34.592789] init: plymouth-upstart-bridge main process (211) killed by TERM signal
Apr  9 07:32:08 AnotherMass avahi-daemon[1060]: Service "AnotherMass" (/services/udisks.service) successfully established.
Apr  9 07:32:08 AnotherMass avahi-daemon[1060]: Service "AnotherMass" (/services/afpd.service) successfully established.
Apr  9 07:32:08 AnotherMass ModemManager[980]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0': not supported by any plugin
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.UPower'
Apr  9 07:32:09 AnotherMass gnome-session[1561]: WARNING: Could not parse desktop file gwibber.desktop or it references a not found TryExec binary
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Successfully called chroot.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Successfully dropped privileges.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Successfully limited resources.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Running.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Successfully made thread 1743 of process 1743 (n/a) owned by '1000' high priority at nice level -11.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Supervising 1 threads of 1 processes of 1 users.
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.systemd1'
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Watchdog thread running.
Apr  9 07:32:09 AnotherMass rtkit-daemon[1748]: Canary thread running.
Apr  9 07:32:09 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Apr  9 07:32:10 AnotherMass colord: Using config file /etc/colord.conf
Apr  9 07:32:10 AnotherMass colord: Using mapping database file /var/lib/colord/mapping.db
Apr  9 07:32:10 AnotherMass colord: Using device database file /var/lib/colord/storage.db
Apr  9 07:32:10 AnotherMass colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Apr  9 07:32:10 AnotherMass colord: loaded plugin libcd_plugin_scanner.so
Apr  9 07:32:10 AnotherMass colord: loaded plugin libcd_plugin_camera.so
Apr  9 07:32:10 AnotherMass colord: Daemon ready for requests
Apr  9 07:32:10 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Apr  9 07:32:10 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Apr  9 07:32:10 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.locale1'
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Apr  9 07:32:10 AnotherMass rtkit-daemon[1748]: Successfully made thread 1979 of process 1979 (n/a) owned by '1000' high priority at nice level -11.
Apr  9 07:32:10 AnotherMass rtkit-daemon[1748]: Supervising 2 threads of 2 processes of 1 users.
Apr  9 07:32:10 AnotherMass pulseaudio[1979]: [pulseaudio] pid.c: Daemon already running.
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Apr  9 07:32:10 AnotherMass colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Apr  9 07:32:10 AnotherMass postfix/master[2126]: daemon started -- version 2.11.0, configuration /etc/postfix
Apr  9 07:32:11 AnotherMass colord: Device added: xrandr-HannStar Display Corp-HW191-135GH3LY0164
Apr  9 07:32:11 AnotherMass colord: Profile added: icc-6d2c6f5342110436ff327e67f932b6aa
Apr  9 07:32:11 AnotherMass colord: Automatic metadata add icc-bb5b30cc367783c64108a4dc12b2b60f to xrandr-HannStar Display Corp-HW191-135GH3LY0164
Apr  9 07:32:11 AnotherMass colord: Profile added: icc-bb5b30cc367783c64108a4dc12b2b60f
Apr  9 07:32:11 AnotherMass mdadm[2250]: DeviceDisappeared event detected on md device /dev/md/0
Apr  9 07:32:11 AnotherMass afpd[2263]: AFP/TCP started, advertising 192.168.2.6:548 (2.2.2)
Apr  9 07:32:11 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Apr  9 07:32:11 AnotherMass udisksd[2297]: udisks daemon version 2.1.3 starting
Apr  9 07:32:12 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Apr  9 07:32:12 AnotherMass udisksd[2297]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Apr  9 07:32:13 AnotherMass ntpdate[1021]: adjust time server 91.189.89.199 offset -0.025625 sec
Apr  9 07:32:15 AnotherMass kernel: [   42.295697] init: plymouth-stop pre-start process (2505) terminated with status 1
Apr  9 07:32:16 AnotherMass NetworkManager[1015]: <info> WiFi hardware radio set enabled
Apr  9 07:32:41 AnotherMass gnome-session[1561]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Apr  9 07:32:49 AnotherMass dbus[879]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr  9 07:32:49 AnotherMass dbus[879]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr  9 07:32:49 AnotherMass kernel: [   75.399728] systemd-hostnamed[2699]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Apr  9 07:33:08 AnotherMass postfix/pickup[2130]: 917BC46D18: uid=1000 from=<user>
Apr  9 07:33:08 AnotherMass postfix/cleanup[2724]: 917BC46D18: message-id=<20150409063308.917BC46D18@AnotherMass>
Apr  9 07:33:08 AnotherMass postfix/qmgr[2131]: 917BC46D18: from=<user@AnotherMass>, size=514, nrcpt=1 (queue active)
Apr  9 07:33:08 AnotherMass postfix/local[2726]: 917BC46D18: to=<root@AnotherMass>, orig_to=<root>, relay=local, delay=0.05, delays=0.02/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Apr  9 07:33:08 AnotherMass postfix/qmgr[2131]: 917BC46D18: removed
Apr  9 07:34:20 AnotherMass dbus[879]: [system] Activating service name='org.debian.apt' (using servicehelper)
Apr  9 07:34:21 AnotherMass AptDaemon: INFO: Initializing daemon
Apr  9 07:34:21 AnotherMass dbus[879]: [system] Successfully activated service 'org.debian.apt'
Apr  9 07:34:21 AnotherMass AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Apr  9 07:34:21 AnotherMass AptDaemon: INFO: UpdateCache() was called
Apr  9 07:34:21 AnotherMass AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/0f7791ba71874af7879a9d0eb40a8feb
Apr  9 07:34:21 AnotherMass AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/0f7791ba71874af7879a9d0eb40a8feb
Apr  9 07:34:21 AnotherMass AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/0f7791ba71874af7879a9d0eb40a8feb
Apr  9 07:34:22 AnotherMass AptDaemon.Worker: INFO: Updating cache
Apr  9 07:35:49 AnotherMass AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0f7791ba71874af7879a9d0eb40a8feb
Apr  9 07:37:07 AnotherMass anacron[1255]: Job `cron.daily' started
Apr  9 07:37:07 AnotherMass anacron[3407]: Updated timestamp for job `cron.daily' to 2015-04-09
Apr  9 07:46:21 AnotherMass AptDaemon: INFO: Quitting due to inactivity
Apr  9 07:46:21 AnotherMass AptDaemon: INFO: Quitting was requested
Apr  9 07:55:57 AnotherMass NetworkManager[1015]: <info> kernel firmware directory '/lib/firmware' changed
Apr  9 07:56:43 AnotherMass kernel: [ 1508.776034] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr  9 07:56:43 AnotherMass kernel: [ 1508.796485] JFS: nTxBlock = 8192, nTxLock = 65536
Apr  9 07:56:43 AnotherMass kernel: [ 1508.817581] NTFS driver 2.1.30 [Flags: R/O MODULE].
Apr  9 07:56:43 AnotherMass kernel: [ 1508.859071] QNX4 filesystem 0.2.3 registered.
Apr  9 07:56:43 AnotherMass kernel: [ 1508.897801] bio: create slab <bio-1> at 1
Apr  9 07:56:43 AnotherMass kernel: [ 1508.907200] Btrfs loaded
Apr  9 07:56:43 AnotherMass os-prober: debug: /dev/sda1: part of software raid array
Apr  9 07:56:43 AnotherMass os-prober: debug: /dev/sdb1: part of software raid array
Apr  9 07:56:43 AnotherMass os-prober: debug: /dev/sdc1: part of software raid array
Apr  9 07:56:43 AnotherMass os-prober: debug: /dev/sdd1: part of software raid array
Apr  9 07:56:43 AnotherMass os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sde2
Apr  9 07:56:43 AnotherMass 50mounted-tests: debug: /dev/sde2 type not recognised; skipping
Apr  9 07:56:43 AnotherMass os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr  9 07:56:43 AnotherMass os-prober: debug: /dev/sde5: is active swap
Apr  9 07:57:00 AnotherMass os-prober: debug: /dev/sda1: part of software raid array
Apr  9 07:57:00 AnotherMass os-prober: debug: /dev/sdb1: part of software raid array
Apr  9 07:57:00 AnotherMass os-prober: debug: /dev/sdc1: part of software raid array
Apr  9 07:57:00 AnotherMass os-prober: debug: /dev/sdd1: part of software raid array
Apr  9 07:57:00 AnotherMass os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sde2
Apr  9 07:57:00 AnotherMass 50mounted-tests: debug: /dev/sde2 type not recognised; skipping
Apr  9 07:57:00 AnotherMass os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr  9 07:57:00 AnotherMass os-prober: debug: /dev/sde5: is active swap
Apr  9 07:57:03 AnotherMass cracklib: no dictionary update necessary.
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592166] audit_printk_skb: 132 callbacks suppressed
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592171] type=1400 audit(1428562623.954:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=21296 comm="apparmor_parser"
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592179] type=1400 audit(1428562623.954:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=21296 comm="apparmor_parser"
Apr  9 07:57:03 AnotherMass kernel: [ 1529.592734] type=1400 audit(1428562623.954:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=21296 comm="apparmor_parser"
Apr  9 07:57:14 AnotherMass rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1040" x-info="http://www.rsyslog.com"] rsyslogd was HUPed

```

---

### Post by superandyjamieson on 2015-04-15
I think the crash was around midnight on April 8th

---

### Post by tgalati4 on 2015-04-15
Interesting entry for rsyslogd at the time of the reboot.  Not sure what that means.  If you initiated the reboot because you thought the system was frozen, then perhaps there was a long write taking place that got corrupted.  It's possible that the machine was not frozen, but just slow to respond.  It's also possible that the kernel was waiting for I/O, normally that does not trigger a syslog error.  A slow or failing RAID could cause an I/O wait.  

Normally you would try to log in with another machine using ssh.  If you are able to log in, then you can shut down normally.  If you can't then use the Magic Keys to reboot.  Otherwise, the log files don't indicate any problems.  Not sure how to rebuild a RAID5 if *mdadm* thinks that there are two bad disks.

Try to assemble again and then immediately check:

```
cat /proc/mdstat
```

---

### Post by superandyjamieson on 2015-04-20
```
user@AnotherMass:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
user@AnotherMass:~$ sudo mdadm --assemble -v --scan --uuid=1c13268a:028b8e7e:306b74ea:4cb00f81
mdadm: looking for devices for /dev/md/0
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sde5
mdadm: no RAID superblock on /dev/sde2
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sda1 is identified as a member of /dev/md/0, slot 0.
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: added /dev/sdc1 to /dev/md/0 as 2 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md/0 as 3
mdadm: added /dev/sda1 to /dev/md/0 as 0
mdadm: /dev/md/0 assembled from 3 drives - not enough to start the array while not clean - consider --force.

```

Interesting that /dev/sdc1 pops up with that message, could that be the drive that failed? I have spare drives waiting in the wings to replace anything.

Or should I --force assemble the array first?

---

### Post by superandyjamieson on 2015-04-21
> **tgalati4 said:**
> Interesting entry for rsyslogd at the time of the reboot.  Not sure what that means.  If you initiated the reboot because you thought the system was frozen, then perhaps there was a long write taking place that got corrupted.  It's possible that the machine was not frozen, but just slow to respond.  It's also possible that the kernel was waiting for I/O, normally that does not trigger a syslog error.  A slow or failing RAID could cause an I/O wait.  

Normally you would try to log in with another machine using ssh.  If you are able to log in, then you can shut down normally.  If you can't then use the Magic Keys to reboot.  Otherwise, the log files don't indicate any problems.  Not sure how to rebuild a RAID5 if *mdadm* thinks that there are two bad disks.

Try to assemble again and then immediately check:

```
cat /proc/mdstat
```

Here's what Terminal spat out

```
user@AnotherMass:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdd1[4](S) sdc1[2](S) sdb1[1](S)
     7813529600 blocks super 1.2


unused devices: <none>
```

---

### Post by superandyjamieson on 2015-04-28
One small bump for this thread.
One giant plea for help!

---

### Post by tgalati4 on 2015-05-05
Here's a similar thread with similar procedures that you can try:  [http://ubuntuforums.org/showthread.php?t=2276699](http://ubuntuforums.org/showthread.php?t=2276699)

Try the --force assemble and see what happens.  It's possible that /dev/sdc had a problem (or hiccup) and that caused the *mdadm* to fail because it's RAID striping is slightly out-of-date.  /dev/sdc was not the drive with the longest spinup time.

I notice that all of your drives are "Green" drives and that "Green" and RAID is not normally used in the same sentence.  Also, your drives have between 500K and 600K load cycles.  It's possible that "Green" drives are only rated to 600K to 1.2M load cycles.  You can research that.  There are utilities to reduce the load cycles.  Basically, every time the drive parks its heads, it increments the load cycle.  "Green" drives tend to park frequently (to save power), but that runs counter to RAID5 operation which requires all drives to be spinning all the time to stripe the data correctly across all of the drives.

Excessive load cycle count is an indication of drive head mechanical wear and that can cause premature drive failure.

---

