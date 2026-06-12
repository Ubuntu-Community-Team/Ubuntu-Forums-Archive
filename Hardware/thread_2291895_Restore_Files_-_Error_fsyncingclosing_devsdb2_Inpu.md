---
title: "Restore Files - Error fsyncing/closing /dev/sdb2: Input/output error"
date: 2015-08-23
forum: Hardware
---

### Post by metinkale38 on 2015-08-23
Hey,

i have a problem:
I have a HDD with 3 Partitions (Win10-Sys,Win10,Files, NTFS). It isn't working anymore. 
When i try to boot, i sometimes see Windows Boot Screen folowed by a Bluescreen, sometimes it can't even recognize it as a bootable disk.

I started Ubuntu from USB, GParted shows "Error fsyncing/closing /dev/sdb1: Input/output error" (for sdb1,sdb2,sdb3) while scanning, if i select the Disk, it shows correct size (~500gigs) and as unallocated (no partitions).

Most probably the disk has physical defects, but i want to recover some files from it (only the last partition), any ideas on how to do it? I cant mount it, i cant dd to a file, it gives:
```
dd: error reading &#8216;/dev/sdb3&#8217;: Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000401509 s, 0.0 kB/s
```

---

### Post by weatherman2 on 2015-08-23
Check the drive's S.M.A.R.T. health first to figure out what you are dealing with.

You can install GSmartControl from a live Ubuntu USB session (from Ubuntu Software Center), but first you may have to enable the "universe" repository.  (Also, you need to be on the internet to download/install it).  Check the S.M.A.R.T. Attributes and see what kind of issues (e.g. Pending Sectors > 0) you have. Attributes highlighted in red are the worst ones.

It may not be easy to get your files from a failing hard disk.  You can try something like ddrescue (package is called "gddrescue") in the worst case.

---

### Post by metinkale38 on 2015-08-23
I didnt understand much but here my output:
Reallocated Sector count,Reallocated Event count, Current  Pending sector count are marked red, probably they are important...
I also did a Short-Self Test - Results below

```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue EIDE
Device Model:     WDC WD5000AAKB-00H8A0
Serial Number:    WD-WCASY3303600
LU WWN Device Id: 5 0014ee 2ad04e9a0
Firmware Version: 05.04E05
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
Local Time is:    Sun Aug 23 20:53:25 2015 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)    Offline data collection activity
                    was aborted by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (11160) seconds.
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
recommended polling time:      ( 131) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   178   154   021    Pre-fail  Always       -       4100
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5541
  5 Reallocated_Sector_Ct   0x0033   186   186   140    Pre-fail  Always       -       110
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       7193
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5477
192 Power-Off_Retract_Count 0x0032   198   198   000    Old_age   Always       -       1542
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5541
194 Temperature_Celsius     0x0022   113   088   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       32
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      7193         1191057
# 2  Short offline       Completed without error       00%      6951         -
# 3  Short offline       Completed without error       00%      2271         -

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

### Post by weatherman2 on 2015-08-23
OK, that's definitely a failing hard drive.  110 sectors had already failed and were replaced ("reallocated") by the drive's firmware, but 6 more sectors are "pending" (cannot be read).  And the short test failed at 90% - probably when trying to read one of the 6 pending sectors.

I'd probably try ddrescue (gddrescue) at this point to try to save whatever can be read from that failed partition. 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As noted there,  there is an older program called "dd_rescue" (to be really confusing!).  Sounds like the gddrescue version is newer/better.

But you will need some other device - another hard drive - at least as large as the original partition to save off a copy with gddrescue.

Other programs like testdisk that may be able to fix partition tables and recover files may fail due to hardware issues, and the more abuse you do to a failing hard drive, the worse it could get.  A program like gddrescue will at least save a pass of what's readable right now so you have the best copy possible, in case the drive gets even worse and stops responding completely.  Maybe you could use testdisk afterward on whatever image you were able to create with gddrescue.

---

### Post by metinkale38 on 2015-08-23
ok thank you, i now already have another hdd with Ubuntu on it... 

the problem now is: the HDD is not shown, only in rare cases after a reboot (could not get it to show again after my last post)... so i cant even ddrescue, any ideas on that?

---

### Post by weatherman2 on 2015-08-23
Hate to say it but it might be too late.

Some people will advise you to try the "freezer trick" (put your hard drive in a ziplock bag then put it in the freezer) - colder hard drives may work more reliably than hot ones - but I have never had any luck with that myself.

---

### Post by metinkale38 on 2015-08-24
i dont know how/why, but it is recognized somehow again, and i was even able to mount it ro. 

Now copying it all, even without ddrescue, to another HDD :D



Thank you guys for your help ):P


Edit: finished copying, after unmounting the drive dissapeared suddenly :)

---

