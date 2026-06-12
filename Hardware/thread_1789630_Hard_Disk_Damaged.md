---
title: "Hard Disk Damaged"
date: 2011-06-24
forum: Hardware
---

### Post by Iqbal_ on 2011-06-24
Hi,
I have a 500 GB HDD on a laptop. The laptop is dual boot with Vista and Karmic.
I upgraded to Natty. After one day the disk crashed. Now I can not install neither Vista nor ubuntu on it. 

Normally Vista takes 30-45 minutes to install on a normal laptop. When I tried on this hard disk- it took 4 hours to expand 65% files. Therefore, I aborted the operation. Vista also informed that disk is faulty and needs replacement.

I deleted all partitions finally there is only one partiton of 465 GB. I tried to install Natty. At the time of copying files - it says that installer crashed. During the installation process the the massage keeps popping that a disk is reporting health problems. The same (installer crashed) happened earlier also.

There is no physical damage to the HDD.

Question are:
1- How to ensure that hard disk is damaged?
2- Is there a way to correct it?

---

### Post by pjd99 on 2011-06-24
If you are able to connect it to another computer you can use the S.M.A.R.T. monitoring tools to run a scan of the disk. A full scan will take quite a while. gsmartcontrol is a nice graphical frontend for smartmontools.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by Bucky Ball on 2011-06-24
You could perhaps download Gparted ISO, make a CD, boot from that, make the entire disk free space, attempt to create a partition (do all this running from the Gparted disk).

See how far you get with that but does sound like the HDD is at end of life. S.M.A.R.T, as mentioned previously, will tell you what you need to know straight away. You might be able to run smartmontools from CD also which would save juggling drives around.

PS: This page suggests you can boot smartmontools as *part* of an ISO:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Download](http://sourceforge.net/apps/trac/smartmontools/wiki/Download)

If you click here it is the list linked from that page of those ISOs:

[Run smartmontools from Live-system]("http://sourceforge.net/apps/trac/smartmontools/wiki/Download#RunsmartmontoolsfromLive-system")

---

### Post by Iqbal_ on 2011-06-24
Hi,
I used disk utility and ran tests available there, the utility reports that the disk is going to fail.

---

### Post by Bucky Ball on 2011-06-24
In that case, please mark thread as 'Solved' and mourn appropriately. ;)

---

### Post by Iqbal_ on 2011-06-25
Hi,
As suggested in the previous post, I installed smartmontools and ran. The results of this test is given below:

smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%      1265         -
# 2  Conveyance offline  Completed: unknown failure    90%      1208         -
# 3  Extended offline    Completed: unknown failure    90%      1208         -
# 4  Short offline       Completed: unknown failure    90%      1208         -
# 5  Short offline       Completed: unknown failure    90%      1208         -
# 6  Extended offline    Completed: unknown failure    90%      1195         -
# 7  Short offline       Completed: unknown failure    90%      1195         -
# 8  Conveyance offline  Completed without error       00%         0         -

smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA family
Device Model:     WDC WD5000BEVT-00A0RT0
Serial Number:    WD-WXN0A99C1592
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jun 25 06:32:49 2011 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
Total time to complete Offline 
data collection:          (15180) seconds.
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
recommended polling time:      ( 176) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       2
  3 Spin_Up_Time            0x0027   185   179   021    Pre-fail  Always       -       1733
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1466
  5 Reallocated_Sector_Ct   0x0033   129   129   140    Pre-fail  Always   FAILING_NOW 561
  7 Seek_Error_Rate         0x002e   200   199   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1265
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1464
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       272
193 Load_Cycle_Count        0x0032   197   197   000    Old_age   Always       -       10144
194 Temperature_Celsius     0x0022   096   091   000    Old_age   Always       -       51
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       561
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0
254 Free_Fall_Sensor        0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
Warning: ATA error count 7983 inconsistent with error log pointer 5

ATA Error Count: 7983 (device log contains only the most recent five errors)
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

Error 7983 occurred at disk power-on lifetime: 1255 hours (52 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 00      00:08:54.550  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:08:54.548  IDENTIFY DEVICE
  ef 90 03 00 00 00 a0 00      00:08:23.622  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 00      00:08:23.621  IDENTIFY DEVICE

Error 7982 occurred at disk power-on lifetime: 1255 hours (52 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 03 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 90 03 00 00 00 a0 00      00:08:23.622  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 00      00:08:23.621  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:08:23.621  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:08:23.618  IDENTIFY DEVICE

Error 7981 occurred at disk power-on lifetime: 1255 hours (52 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00      00:08:23.621  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:08:23.618  IDENTIFY DEVICE
  ef 90 03 00 00 00 a0 00      00:07:52.552  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 00      00:07:52.550  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%      1265         -
# 2  Conveyance offline  Completed: unknown failure    90%      1208         -
# 3  Extended offline    Completed: unknown failure    90%      1208         -
# 4  Short offline       Completed: unknown failure    90%      1208         -
# 5  Short offline       Completed: unknown failure    90%      1208         -
# 6  Extended offline    Completed: unknown failure    90%      1195         -
# 7  Short offline       Completed: unknown failure    90%      1195         -
# 8  Conveyance offline  Completed without error       00%         0         -

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

---

### Post by Yellow Pasque on 2011-06-25
"It's dead, Jim."

---

### Post by createdcreature on 2011-06-25
Its probably dead, but try the S.M.A.R.T tools in the BIOS, and there might be a self test in there too, but I think it is dead.

---

### Post by Ranko Kohime on 2011-06-25
It's a goner.

[http://www.youtube.com/watch?v=28sdV_DXSrU]("http://www.youtube.com/watch?v=28sdV_DXSrU")

---

### Post by Bucky Ball on 2011-06-27
> SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.

That's about the size of it ...

---

### Post by Iqbal_ on 2011-06-27
Hi,
Finally, I am going to purchase new hard disk.

Thank you all:)

---

### Post by Iqbal_ on 2011-06-27
Hi,

Finally, I am going to get new hard disk.

Thank you all

---

