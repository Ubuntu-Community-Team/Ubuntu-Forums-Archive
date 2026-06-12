---
title: "Disk Utility reporting internal drive about to fail"
date: 2013-04-16
forum: Hardware
---

### Post by Steve Francis on 2013-04-16
I am using Ubuntu 10.04.

Disk Utility recently popped up with an error message that one of my hard drives was about to fail. This drive contains all my media files. It is Hitachi Model HDS721075KLA330

Panicked, I replaced the drive and copied all the files across.

I then transferred the "failing" drive to a Windows p.c. and ran it through HGST (Hitachi Global Storage Technologies) Drive Fitness Test and then Western Digital's Data Lifeguard Diagnostic Test. Both tests were extended tests and lasted 2-3 hours.

The drive passed both Windows tests.

Is there something I am missing? Any tests worth trying to detect why the drive is being reported as about to fail by Ubuntu?

Thanks for your help.

---

### Post by ajgreeny on 2013-04-16
I seem to recall the false positives were a bit of a bug in some earlier versions of palimpset, the disk utility.

Perhaps that is how the reports appeared on your machine.

---

### Post by tgalati4 on 2013-04-16
What is the SMART readout?

```
sudo smartctl -a /dev/sdb
```

There is a reason they are called Hitachi Death Stars.

---

### Post by Steve Francis on 2013-04-24
> **tgalati4 said:**
> What is the SMART readout?

```
sudo smartctl -a /dev/sdb
```

There is a reason they are called Hitachi Death Stars.

Apologies for delay - I had to reinstall the faulty drive to carry out your suggestion.

Disk Utility is reporting the SMART status as *Disk has a few bad sectors*

This is the output from [FONT=courier new]sudo smartctl -a /dev/sdb[/FONT]
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K1000
Device Model:     Hitachi HDS721075KLA330
Serial Number:    GTF200P8GAKR5F
Firmware Version: GK8OA70M
User Capacity:    750,156,374,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Wed Apr 24 14:20:26 2013 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (11471) seconds.
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
recommended polling time:      ( 191) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   130   130   054    Pre-fail  Offline      -       151
  3 Spin_Up_Time            0x0007   115   115   024    Pre-fail  Always       -       550 (Average 491)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       2223
  5 Reallocated_Sector_Ct   0x0033   067   067   005    Pre-fail  Always       -       173
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   132   132   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       13629
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2223
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       2622
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       2622
194 Temperature_Celsius     0x0002   187   187   000    Old_age   Always       -       32 (Lifetime Min/Max 14/75)
196 Reallocated_Event_Count 0x0032   098   098   000    Old_age   Always       -       200
197 Current_Pending_Sector  0x0022   077   077   000    Old_age   Always       -       560
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 434 (device log contains only the most recent five errors)
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

Error 434 occurred at disk power-on lifetime: 13584 hours (566 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 59 01 d9 16 5e e0  Error: UNC at LBA = 0x005e16d9 = 6166233

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 00 01 d9 16 5e e0 00      01:44:06.400  READ MULTIPLE EXT
  29 00 01 00 00 00 e0 00      01:44:06.400  READ MULTIPLE EXT
  29 00 01 d8 16 5e e0 00      01:44:02.300  READ MULTIPLE EXT
  29 00 01 d7 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT
  29 00 01 d6 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT

Error 433 occurred at disk power-on lifetime: 13584 hours (566 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 59 01 d7 16 5e e0  Error: UNC at LBA = 0x005e16d7 = 6166231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 00 01 d7 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT
  29 00 01 d6 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT
  29 00 01 d5 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT
  29 00 01 d4 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT
  29 00 01 d3 16 5e e0 00      01:43:57.500  READ MULTIPLE EXT

Error 432 occurred at disk power-on lifetime: 13584 hours (566 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 59 29 d7 16 5e e0  Error: UNC at LBA = 0x005e16d7 = 6166231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 03 00 00 16 5e e0 00      01:43:52.100  READ MULTIPLE EXT
  29 03 00 00 15 5e e0 00      01:43:52.000  READ MULTIPLE EXT
  29 03 00 00 14 5e e0 00      01:43:52.000  READ MULTIPLE EXT
  29 03 00 00 13 5e e0 00      01:43:51.800  READ MULTIPLE EXT
  29 03 00 00 12 5e e0 00      01:43:51.700  READ MULTIPLE EXT

Error 431 occurred at disk power-on lifetime: 13584 hours (566 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ff 00 5e e0  Error: UNC 1 sectors at LBA = 0x005e00ff = 6160639

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 01 ff 00 5e e0 00      01:42:01.800  READ DMA EXT
  25 03 01 fe 00 5e e0 00      01:42:01.700  READ DMA EXT
  25 03 01 fd 00 5e e0 00      01:42:01.400  READ DMA EXT
  25 03 01 fc 00 5e e0 00      01:42:01.200  READ DMA EXT
  25 03 01 fb 00 5e e0 00      01:42:01.200  READ DMA EXT

Error 430 occurred at disk power-on lifetime: 13573 hours (565 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 d7 16 5e e0  Error: UNC 8 sectors at LBA = 0x005e16d7 = 6166231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 d7 16 5e e0 00      00:01:13.100  READ DMA EXT
  25 00 08 cf 16 5e e0 00      00:01:13.100  READ DMA EXT
  25 00 08 c7 16 5e e0 00      00:01:13.100  READ DMA EXT
  25 00 08 bf 16 5e e0 00      00:01:13.100  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:01:13.100  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     13588         -
# 2  Short offline       Completed without error       00%     13584         -

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

### Post by ahallubuntu on 2013-04-24
~

---

### Post by tgalati4 on 2013-04-24
Your drive has 13K hours on it.  Most drives are rated to 50K hours or 50,000 hrs for Mean Time Before Failure--whatever that means.  This line is also a clue:

  5 Reallocated_Sector_Ct   0x0033   067   067   005    Pre-fail  Always       -       173

When your reallocated sector count exceeds the space allowed then you have a serious problem.  I don't know how many relocated sectors are provisioned for in modern drives, but 173 sounds like more than I would be comfortable with.

So your drive is still functioning, but has some issues.  Put it in a USB enclosure and use it for static storage.  After backing up your data to a newer drive try running some short and long tests using smartctl:

```
sudo smartctl -t short /dev/sdb
sudo smartctl -t long /dev/sdb
```

To read the results use the previous status command, as the results are stored in the SMART parameters.

You might have some luck with a low-level format using the manufacturer's utility, but again at 13K hours, this disk has seen some service.

---

### Post by Steve Francis on 2013-04-24
> **ahallubuntu said:**
> If you have any files on the drive you care  about, try to copy them as soon as you can.  Then, you can use this  drive as a paperweight or a doorstop - and get a replacement.  560  sectors unable to be read makes it almost useless.

Reallocated_Event_Count = 200 :sad:

My other three drives have zero for both Current_Pending_Sector and Reallocated_Event_Count :smile:

> **tgalati4 said:**
> Your drive has 13K hours on it.  Most drives are rated to 50K hours or 50,000 hrs for Mean Time Before Failure--whatever that means.  This line is also a clue:

  5 Reallocated_Sector_Ct   0x0033   067   067   005    Pre-fail  Always       -       173

When your reallocated sector count exceeds the space allowed then you have a serious problem.  I don't know how many relocated sectors are provisioned for in modern drives, but 173 sounds like more than I would be comfortable with.

So your drive is still functioning, but has some issues.  Put it in a USB enclosure and use it for static storage.  After backing up your data to a newer drive try running some short and long tests using smartctl:

```
sudo smartctl -t short /dev/sdb
sudo smartctl -t long /dev/sdb
```

To read the results use the previous status command, as the results are stored in the SMART parameters.

You might have some luck with a low-level format using the manufacturer's utility, but again at 13K hours, this disk has seen some service.

Thank you for your comment. What's an acceptable number of hours service, please? (13500 hours is 1½ years. Previously, I've had several disks running (not continuously) without failure for longer than that.)

---

### Post by ahallubuntu on 2013-04-24
~

---

### Post by Steve Francis on 2013-04-24
> **ahallubuntu said:**
> I forgot to mention: check to see if it's still under warranty; if so, get it replaced.

Drives do fail without obvious reason all the time, sometimes early in their lives, sometimes not.  I accept it as a fact of life, backup often, and monitor S.M.A.R.T. regularly.  I buy storage drives in pairs and sync one to the other one regularly (not a RAID) so when one fails, I have another presumably good drive that I hope will live until I can get a replacement and make another copy of the data.

I used the [HGST warranty verification tool]("http://www.hgst.com/portal/site/en/support/warranty/") to check my drive. The warranty expired 2010-12-31!

Perhaps I've been a little naïve in believing that hard drives were built to last :D

I was considering a RAID-1 NAS box for storing files so was intrigued that you sync manually instead (perhaps to overcome the 2TB limit).

---

### Post by ahallubuntu on 2013-04-24
~

---

### Post by tgalati4 on 2013-04-25
I have some small drives (20GB, 2001 vintage) that have been running continuously since June 2006.  I've had some Hitachi Death Stars fail in a year.  It's a crapshoot.  The capacity has increased, but I feel the quality/reliability has decreased.  Google did a study a few years back--and they go through a lot of disk drives.  After 3 years of 24/7, you are taking your chances.

---

