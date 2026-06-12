---
title: "Ubuntu 14.04 very slow on Dell Inspiron n4030"
date: 2015-03-29
forum: Hardware
---

### Post by chhitizsubedi on 2015-03-29
Hello,
For the past few months my Ubuntu 14.04 has been running very slow. The startup has been slower than before. The browsers- Chrome, Chromium, Firefox and Opera are all slow, and hang while using. In the past few days the whole system seems to be running very slow and its getting frustrating.
My system specs are:
Memory: 1.8GB
Processor: Intel Core i3 CPU M 370 @ 2.40Ghz x 4
Graphics: Intel Ironlake Mobile x86/MMX/SSE2
Disk: 312.9 GB
I did a clean install of Ubuntu 14.04.
Any help will be appreciated.

---

### Post by v3.xx on 2015-03-31
How much memory are you using?
```
free -m
```
You can also look at Processes in the System Monitor for memory usage.

---

### Post by weatherman2 on 2015-03-31
Check the hard drive health.  Install GSmartControl, then look for any S.M.A.R.T. Attributes highlighted in pink.  Any sectors with a RAW value > 0 probably indicate problems.  You can also run S.M.A.R.T. tests with GSmartControl.  A failing hard drive can slow a system way down.  Obviously, make sure you everything is backed up that you care about, anyway.

---

### Post by gordintoronto on 2015-04-01
Are you monitoring the system temperature?  If it gets hot, it could throttle back.

---

### Post by chhitizsubedi on 2015-04-02
The free memory is 
> 
chhitiz@MY-PC:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1880       1702        178        180         83        857
-/+ buffers/cache:        760       1119
Swap:         1909          0       1909


Yes my system does get hot while I am using it. So I use a external fan and it seems to cool it down.

---

### Post by v3.xx on 2015-04-02
Your memory and swap look good at the moment.  You have 1119M of free ram.  But ..

I'm still not convince that swap isn't kicking in.  So I suggest for the moment you turn swap off and see if that makes any difference.
```
sudo swapoff -a
```
If you wish to turn it on
```
sudo swapon -a
man swapon
```
Gordintoronto has a good point.  My wife's computer will do this (and other things) if I don't keep it dusted out and it starts running hot.  Can you monitor your temps?

And as mention by weatherman2, if you can run the 'smart' test on your hdd.

---

### Post by Vladlenin5000 on 2015-04-02
... And really check your HDD. A 320GB can be 10 years old or worse...

---

### Post by chhitizsubedi on 2015-04-03
I did turn the swap off. I am waiting to see if this solves the problem. GSmartControl didnt show any errors. The output file is:
> 
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD3200BEVT-75ZCT2
Serial Number:    WD-WX11EA0T4517
LU WWN Device Id: 5 0014ee 2054182b9
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Fri Apr  3 18:15:08 2015 NPT
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
data collection: 		( 9960) seconds.
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
recommended polling time: 	 ( 118) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       17
  3 Spin_Up_Time            0x0027   186   185   021    Pre-fail  Always       -       1683
  4 Start_Stop_Count        0x0032   094   094   000    Old_age   Always       -       6317
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9115
 10 Spin_Retry_Count        0x0032   100   099   000    Old_age   Always       -       1
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5661
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       419
193 Load_Cycle_Count        0x0032   185   185   000    Old_age   Always       -       47420
194 Temperature_Celsius     0x0022   095   085   000    Old_age   Always       -       52
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   088   088   000    Old_age   Always       -       8834
241 Total_LBAs_Written      0x0032   001   001   000    Old_age   Always       -       217401656596395
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       26542626078


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      9115         -
# 2  Short offline       Completed without error       00%      8955         -
# 3  Short offline       Completed without error       00%      8955         -
# 4  Short offline       Completed without error       00%      4762         -
# 5  Short offline       Completed without error       00%         0         -


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

### Post by v3.xx on 2015-04-03
```
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family: Western Digital Scorpio Blue Serial ATA
Device Model: WDC WD3200BEVT-75ZCT2
Serial Number: WD-WX11EA0T4517
LU WWN Device Id: 5 0014ee 2054182b9
Firmware Version: 11.01A11
User Capacity: 320,072,933,376 bytes [320 GB]
Sector Size: 512 bytes logical/physical
Rotation Rate: 5400 rpm
Device is: In smartctl database [for details use: -P show]
ATA Version is: ATA8-ACS (minor revision not indicated)
SATA Version is: SATA 2.5, 3.0 Gb/s
Local Time is: Fri Apr 3 18:15:08 2015 NPT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status: (0x00) Offline data collection activity
was never started.
Auto Offline Data Collection: Disabled.
Self-test execution status: ( 0) The previous self-test routine completed
without error or no self-test has ever
been run.
Total time to complete Offline
data collection: ( 9960) seconds.
Offline data collection
capabilities: (0x7b) SMART execute Offline immediate.
Auto Offline data collection on/off support.
Suspend Offline collection upon new
command.
Offline surface scan supported.
Self-test supported.
Conveyance Self-test supported.
Selective Self-test supported.
SMART capabilities: (0x0003) Saves SMART data before entering
power-saving mode.
Supports SMART auto save timer.
Error logging capability: (0x01) Error logging supported.
General Purpose Logging supported.
Short self-test routine
recommended polling time: ( 2) minutes.
Extended self-test routine
recommended polling time: ( 118) minutes.
Conveyance self-test routine
recommended polling time: ( 5) minutes.
SCT capabilities: (0x303f) SCT Status supported.
SCT Error Recovery Control supported.
SCT Feature Control supported.
SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x002f 200 200 051 Pre-fail Always - 17
3 Spin_Up_Time 0x0027 186 185 021 Pre-fail Always - 1683
4 Start_Stop_Count 0x0032 094 094 000 Old_age Always - 6317
5 Reallocated_Sector_Ct 0x0033 200 200 140 Pre-fail Always - 0
7 Seek_Error_Rate 0x002e 100 253 000 Old_age Always - 0
9 Power_On_Hours 0x0032 088 088 000 Old_age Always - 9115
10 Spin_Retry_Count 0x0032 100 099 000 Old_age Always - 1
11 Calibration_Retry_Count 0x0032 100 100 000 Old_age Always - 0
12 Power_Cycle_Count 0x0032 095 095 000 Old_age Always - 5661
192 Power-Off_Retract_Count 0x0032 200 200 000 Old_age Always - 419
193 Load_Cycle_Count 0x0032 185 185 000 Old_age Always - 47420
194 Temperature_Celsius 0x0022 095 085 000 Old_age Always - 52
196 Reallocated_Event_Count 0x0032 200 200 000 Old_age Always - 0
197 Current_Pending_Sector 0x0032 200 200 000 Old_age Always - 0
198 Offline_Uncorrectable 0x0030 100 253 000 Old_age Offline - 0
199 UDMA_CRC_Error_Count 0x0032 200 200 000 Old_age Always - 0
200 Multi_Zone_Error_Rate 0x0008 100 253 000 Old_age Offline - 0
240 Head_Flying_Hours 0x0032 088 088 000 Old_age Always - 8834
241 Total_LBAs_Written 0x0032 001 001 000 Old_age Always - 217401656596395
242 Total_LBAs_Read 0x0032 200 200 000 Old_age Always - 26542626078


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Short offline Completed without error 00% 9115 -
# 2 Short offline Completed without error 00% 8955 -
# 3 Short offline Completed without error 00% 8955 -
# 4 Short offline Completed without error 00% 4762 -
# 5 Short offline Completed without error 00% 0 -


SMART Selective self-test log data structure revision number 1
SPAN MIN_LBA MAX_LBA CURRENT_TEST_STATUS
1 0 0 Not_testing
2 0 0 Not_testing
3 0 0 Not_testing
4 0 0 Not_testing
5 0 0 Not_testing
Selective self-test flags (0x0):
After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```
> I did turn the swap off. I am waiting to see if this solves the problem.
If this solves the problem you need to turn swap on and adjust swappiness to 10.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by chhitizsubedi on 2015-04-04
My swapiness is already 10.

---

