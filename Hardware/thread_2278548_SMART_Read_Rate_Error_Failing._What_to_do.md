---
title: "SMART: Read Rate Error Failing. What to do?"
date: 2015-05-17
forum: Hardware
---

### Post by pendechosen on 2015-05-17
Hi, 
Some days ago I was using windows and the whole OS freezed when I was copying certain folders...
So I expect there is something wrong in the Windows Partition on my hard drive currently.
I googled and checked the SMART status and basically the results are as follow with only the first test failed.
[ATTACH=CONFIG]262036[/ATTACH]
(well, this sucks cuz it has run only for less than 2 years.)

Questions:
1 What does the threshold value mean and is it significant?
2 Does read rate error indicate bad sectors, or else are there any repair I can make?
3 Will the read error problem expend to other partitions?
4 How can I detect such read error problems in all partitions, and to know where it exactly happens on the drive?

I am using a laptop, I think the only ways to backup are to use an external hard disk or through online >_>
Thank you for advanced for demystifying my doubts.

---

### Post by weatherman2 on 2015-05-17
Looks like your hard drive is about to fail.  You will need to replace the hard drive and probably re-install the OS from scratch.  (In some situations you can clone your old drive to the new one, but it appears you may not have much luck doing that with this failing drive.)

More urgently, you should try to backup any important files on that drive that you don't have copies of - they may already be irretrievable.

---

### Post by tgalati4 on 2015-05-18
Each hard drive manufacturer defines their own SMART attributes.  Question 1:  Generally Threshold is % of Life Remaining.  Your read error rate is supposed to be flagged when you reach 51% of the life (half-life in this case) of the drive.  You are at 1% Life Remaining.  This is to give you some time to grab your important data before the drive fails completely.

Q2: Read error rate could be many things, but there are correctable and uncorrectable (UNC) read errors.  Bad sectors are noted when the same sector repeatedly has problems--and this is noted as either Pending Bad Sectors or Reallocated Sectors.  Read errors can come from worn head mechanisms, vibration, controller issues, hard to tell.  Do you use this laptop every day on a bus?  Consumer laptop drives are usually rated for 3 years.  So at 2 years to have problems is not unusual if you use it daily in a harsh environment.

Q3:  Read error rates, if mechanical, could happen on all partitions.  Bad sectors tend to be confined to one partition, and can be worked around by repartitioning around the block of bad sectors.  I have done this successfully on some drives--as an exercise--I would not use such a drive for daily use.

Q4: Post the full output of SMART.  In linux:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

---

### Post by pendechosen on 2015-05-19
> **tgalati4 said:**
> Each hard drive manufacturer defines their own SMART attributes.  Question 1:  Generally Threshold is % of Life Remaining.  Your read error rate is supposed to be flagged when you reach 51% of the life (half-life in this case) of the drive.  You are at 1% Life Remaining.  This is to give you some time to grab your important data before the drive fails completely.

Q2: Read error rate could be many things, but there are correctable and uncorrectable (UNC) read errors.  Bad sectors are noted when the same sector repeatedly has problems--and this is noted as either Pending Bad Sectors or Reallocated Sectors.  Read errors can come from worn head mechanisms, vibration, controller issues, hard to tell.  Do you use this laptop every day on a bus?  Consumer laptop drives are usually rated for 3 years.  So at 2 years to have problems is not unusual if you use it daily in a harsh environment.

Q3:  Read error rates, if mechanical, could happen on all partitions.  Bad sectors tend to be confined to one partition, and can be worked around by repartitioning around the block of bad sectors.  I have done this successfully on some drives--as an exercise--I would not use such a drive for daily use.

Q4: Post the full output of SMART.  In linux:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

Thanks for the detailed explanation mate, if there were a vote function I would probably vote this as the best answer.
Here is the output of SMART:
```

smartctl 6.2 2013-07-26 r3841 [i686-linux-3.13.0-45-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus SpinPoint M8 (AF)
Device Model:     ST1000LM024 HN-M101MBB
Serial Number:    S2WZJ90C728321
LU WWN Device Id: 5 0004cf 208104fa7
Firmware Version: 2AR20003
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue May 19 21:45:00 2015 HKT
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
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (13020) seconds.
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
recommended polling time:      ( 217) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   001   001   051    Pre-fail  Always   FAILING_NOW 42565
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   089   089   025    Pre-fail  Always       -       3457
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3777
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       17328
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       605
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1276
 13 Read_Soft_Error_Rate    0x003a   100   100   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0022   098   098   000    Old_age   Always       -       58216710
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       310
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       54001
194 Temperature_Celsius     0x0002   053   043   000    Old_age   Always       -       47 (Min/Max 12/57)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   097   097   000    Old_age   Always       -       499
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       23
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       17275
241 Total_LBAs_Written      0x0032   093   090   000    Old_age   Always       -       10586225
242 Total_LBAs_Read         0x0032   091   088   000    Old_age   Always       -       13124224
254 Free_Fall_Sensor        0x0032   252   252   000    Old_age   Always       -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -
# 2  Short offline       Completed without error       00%         0         -
# 3  Short offline       Completed without error       00%         0         -


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
I think I am gonna buy a hdd some days later, hgst, perhaps :sad:

---

### Post by tgalati4 on 2015-05-20
Well, you got 17K hours on the disk drive.  499 sectors are pending, which means they are difficult to read and may be reallocated.  You have no free-fall marks, so it hasn't been dropped.  The Program_Fail_Count total is really high (58216710).  I don't know what this number means.  Perhaps it is a disk controller problem.  Could be a loose cable.  It's worth checking.  

At least you got a warning.  Many drives fail without a SMART warning (perhaps 1/3 of failures are not captured by the SMART system).  Back up your data as soon as you can.

---

### Post by efflandt on 2015-05-20
You never know how long a hard drive is going to last. Long ago I had 1 fail (constantly increasing bad sectors) within a month of purchase. But I have a PC in my basement that has been running an old SuSE 8.2 version 24/7 since 2003 including a 5 year stretch without rebooting from July 2006 to July 2011 (when power failed for 14 hrs). One of its 3 drives was a warranty replacement drive long ago that has lasted indefinitely. The Linux partition at the far end of the 1 TB drive on my current desktop began failing after 3 years as I filled it up when I got into Linux Steam. So I took that opportunity to shrink Win7 to make more room for Linux before cloning that to a new drive, reinstalling Ubuntu, and copying my /home over from the failing drive. Only a few Linux game files were corrupted which Steam was able to replace.

A drive caddy that handles laptop or desktop drives connected with eSATA or USB can be handy for that. The caddy also comes in handy if you need to virus/malware scan a Windows drive from another computer, which I needed to do with my laptop drive after ending up on a bogus site when attempting to get Google Chrome and ending up with some Binkiland browser with adware/malware. I boot Ubuntu on that from mSATA SSD card.

---

