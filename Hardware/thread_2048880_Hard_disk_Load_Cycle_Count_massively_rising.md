---
title: "Hard disk Load_Cycle_Count massively rising"
date: 2012-08-27
forum: Hardware
---

### Post by ashzoomerintrack on 2012-08-27
Hello everyone,
My laptop is plagued by the massively increasing Load_Cyle_Count. The hard disk is WD one. Here is complete smartctl log:
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD5000BEVT-22A0RT0
Serial Number:    WD-WX71A6093228
LU WWN Device Id: 5 0014ee 655a830fb
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Aug 27 21:16:07 2012 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(13200) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 154) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7037)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   187   151   021    Pre-fail  Always       -       1633
  4 Start_Stop_Count        0x0032   085   085   000    Old_age   Always       -       15757
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3460
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2700
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       439
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       326
193 Load_Cycle_Count        0x0032   061   061   000    Old_age   Always       -       419806
194 Temperature_Celsius     0x0022   109   097   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3456         -

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

I have disabled the dreaded intellipark like feature by using idle3 tools from sourceforge. Also I have set hdparm -B to 200 in hdparm-functions . Yet the load_cycle_count is rising fast. 

One noticeble thing is that hdparm -S gives :
 -S: bad/missing standby-interval value (0..255)
even when I have set value in hdparm.conf as 120. Please help me.

P.S.: As i write this post the Load_cycle_count has risen by 2!!!

---

### Post by ashzoomerintrack on 2012-09-03
bump

---

### Post by ahallubuntu on 2012-09-03
Yikes!  I have almost this exact same hard drive (WD 500GB, same firmware, sub-model number is a little newer than yours).  Mine has had most of its life in Ubuntu laptops and netbooks.  It's now in use as an portable backup drive in an enclosure.

My drive has been on longer than yours (5577) but the load cycle count is lower (56759).

Curious, I plugged it into my Dell laptop (Ubuntu 10.04 LTS).  Just like you saw, the load cycle count increased pretty quickly, like once every 15 or 20 seconds!

Then I plugged it into my Acer netbook (Ubuntu 11.04).  The load cycle count didn't increase at all.

One difference I noticed:  Power management was set to "Spin down hard disks when possible" on the laptop and UNchecked on the netbook.  I tried UNchecking it on the laptop (10.04) but that made no difference - it still increased.

Did you try the fix given here, follow the instructions exactly?

[http://ubuntuforums.org/showthread.php?t=1956333](http://ubuntuforums.org/showthread.php?t=1956333)

I have not tried it.  One note: the poster noticed something similar to what I noticed: his Acer netbook didn't exhibit the problem but his Dell and Toshiba laptops did.

---

