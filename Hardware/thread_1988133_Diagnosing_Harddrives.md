---
title: "Diagnosing Harddrives"
date: 2012-05-26
forum: Hardware
---

### Post by bonfire89 on 2012-05-26
I had been having issues with my home server shutting down on its own. And just now I was sitting next to the server when it went "click click click" and then just shut down.

Obviously there is a hard drive which is dying, the problem is that there are 10 of them in the machine.

I now plan to attach each one individually to another computer which is easier for me to sit at by a SATA-USB connector and run some diagnostics, but, which diagnostic do I run? Or is the fact that it took down machine indicate that it was the OS drive?


Thanks!


Edit: I just found this [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) but, I'm off for a few hours.

---

### Post by ahallubuntu on 2012-05-27
Not quite obvious that it is one of your hard drive.  Actually, it sounds more like your power supply.  A bad hard drive often won't cause your computer just to shut down, but a failing power supply could easily cause the drives to "click" because they don't have enough power to spin up.

---

### Post by bonfire89 on 2012-05-27
hmm, by shutdown I meant in terms of software. At the time I think I made the mistake by diagnosing it immediately. I was working at the computer, heard the clicks and the screen just went blank but the power was still on. Without giving it time I just shut it down by the hard switch on the psu. I probably should have waited to see what would happen, but, too late for that now.

if it helps I could find out the wattage of the PSU but it would require some disassembly. But, the PSU has been powering the same drives for over a year now no problem and the only thing fancy on this system is the number of WD green drives I have, the cpu is an old P4, 1.25GB of ram...

I also suppose you are suggesting that not all the drives were spinning a few moments prior to the clicks?

---

### Post by ahallubuntu on 2012-05-27
It's really not that complicated:  test each component systematically.  Test each hard drive.  Test the power supply or try a different one.

Test each drive's S.M.A.R.T status with SmartMonTools:

sudo smartctl -a /dev/sda

(repeat for each drive)

Or click on each drive in GSmartControl (graphic interface to same thing as above).  Any drive attributes highlighted in red?  Pending sector errors and read errors are the ones you should care most about but look at anything highlighted in red.

Every bad power supply I've ever replaced worked great until it didn't.  The fact that your power supply worked great for the last year is irrelevant if it has now failed.  Yes, I have seen some power supplies fail "gradually" - that is, they still provide some power but no longer enough.  I corrupted a hard drive that way once.   Lesson learned: don't use cheap power supplies.

There are ways to test power supplies, but sometimes you just have to swap in a good one and see if there is any different.  If the problem goes away with another power supply, then you have your solution.

---

### Post by bonfire89 on 2012-05-28
I ran the test on the OS drive this evening, and, I got a read failure. The test was conducted by attaching the drive to another machine of mine via a USB->SATA connector. It seems like this might be the problem.

Tomorrow I will run the test again.

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD15EARS-00Z5B1
Serial Number:    --------------
LU WWN Device Id: 5 0014ee 0ac9410ed
Firmware Version: 80.00A80
User Capacity:    1,500,301,910,016 bytes [1.50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon May 28 01:01:50 2012 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 118)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(33000) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3031)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       19
  3 Spin_Up_Time            0x0027   198   180   021    Pre-fail  Always       -       5083
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       112
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   073   073   000    Old_age   Always       -       20067
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       100
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       76
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1335797
194 Temperature_Celsius     0x0022   115   113   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always       -       1464
198 Offline_Uncorrectable   0x0030   195   194   000    Old_age   Offline      -       1448
199 UDMA_CRC_Error_Count    0x0032   200   183   000    Old_age   Always       -       20
200 Multi_Zone_Error_Rate   0x0008   200   169   000    Old_age   Offline      -       1

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       60%     20067         1441348840
# 2  Short offline       Completed without error       00%     20064         -

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

### Post by ahallubuntu on 2012-05-28
Oh, yes - you have over 1400 pending sector errors.  That drive is probably junk.

---

