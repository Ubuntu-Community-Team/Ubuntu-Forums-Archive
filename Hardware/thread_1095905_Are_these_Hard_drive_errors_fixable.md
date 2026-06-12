---
title: "Are these Hard drive errors fixable?"
date: 2009-03-14
forum: Hardware
---

### Post by Bruce M. on 2009-03-14
Hi Folks,

**This is [[SOLVED]]("http://ubuntuforums.org/showthread.php?t=1044714")**

OK, I think I have a problem, and need to know if these are fixable or am I loosing the drive?

If fixable could you point me in the right direction to read up on how please.

BTW: It's a Maxtor DiamondMax - ATA/133

```
bruloo@bruloo:~$ sudo smartctl -P show /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Drive found in smartmontools Database.  Drive identity strings:
MODEL:              Maxtor 6L200P0
FIRMWARE:           BAJ41G20
match smartmontools Drive Database entry:
MODEL REGEXP:       ^Maxtor 6(B(30|25|20|16|12|08)0[MPRS]|L(080[MLP]|(100|120)[MP]|160[MP]|200[MPRS]|250[RS]|300[RS]))0$
FIRMWARE REGEXP:    .*
MODEL FAMILY:       Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
ATTRIBUTE OPTIONS:  009 Power_On_Minutes
bruloo@bruloo:~$
```

```
bruloo@bruloo:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
Device Model:     Maxtor 6L200P0
Serial Number:    L41RBVQH
Firmware Version: BAJ41G20
User Capacity:    203,928,109,056 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sat Mar 14 10:59:08 2009 ARST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (1622) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  82) minutes.
SCT capabilities: 	       (0x0021)	SCT Status supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   211   206   063    Pre-fail  Always       -       17207
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       899
  5 Reallocated_Sector_Ct   0x0033   251   251   063    Pre-fail  Always       -       23
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   251   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   248   238   187    Pre-fail  Always       -       52455
  9 Power_On_Minutes        0x0032   237   237   000    Old_age   Always       -       141h+49m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   251   251   000    Old_age   Always       -       1092
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   036   253   000    Old_age   Always       -       40
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       13536
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   252   252   000    Old_age   Offline      -       11
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   001   001   000    Old_age   Offline      -       7244
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   239   239   000    Old_age   Offline      -       175
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   251   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1007 (device log contains only the most recent five errors)
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

Error 1007 occurred at disk power-on lifetime: 4757 hours (198 days + 5 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:00:31.212  IDENTIFY DEVICE
  c8 00 78 ba 33 58 e3 00      00:00:29.752  READ DMA
  27 00 00 00 00 00 e0 00      00:00:29.744  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:00:29.736  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:29.730  SET FEATURES [Set transfer mode]

Error 1006 occurred at disk power-on lifetime: 4757 hours (198 days + 5 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:00:29.654  IDENTIFY DEVICE
  c8 00 78 ba 33 58 e3 00      00:00:28.203  READ DMA
  27 00 00 00 00 00 e0 00      00:00:28.195  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:00:28.187  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:28.181  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

bruloo@bruloo:~$
```

I have a WD 80GB ATA-133 and two WD 40GB ATA-100's that I can use.

Thanks in advance.
Bruce

---

### Post by tgalati4 on 2009-03-16
Try cleaning the interior of the machine and reseating the ribbon cables and power cables.  Could be a controller problem.  Do you have hddtemp installed?  Are the drives getting hot?

---

### Post by Bruce M. on 2009-03-17
> **tgalati4 said:**
> Try cleaning the interior of the machine and reseating the ribbon cables and power cables.  Could be a controller problem.  Do you have hddtemp installed?  Are the drives getting hot?

The sides of the machine have been off for most of the summer (southern hemisphere), the box is clean, and hddtemp in conky put the temps routinely between 41 and 46°C. The cables are fine the other two drives have NO errors and no problems.

---

### Post by tgalati4 on 2009-03-17
The fact that you have ~7200 connection errors (UDMA_CRC_Error_Count) would indicate a cable/power/controller issue.  The logged errors indicate that the drive was in an unknown state--this also points to a cable/power/controller issue.

I assume you have the machine on an UPS.  I also assume that the power supply is OK and not causing hiccups.

You can run some long-term tests:

>sudo smartctl -t long /dev/sda

Wait for the tests to complete then run:

>sudo smartctl -l selftest /dev/sda

to view the results.

I would switch/change cables and make sure the drives are tight.  Vibrations can cause strange errors.

Also check

>dmesg | tail -100

for drive access errors.

Since none of your other SMART parameters have dipped below the threshold values, you should be OK.

Remember that SMART only captures ~56% (not 2/3 as some believe) of drive failures.  The rest just happen.

Google employees did a research paper on disk drives (I believe 80 GB models) a few years ago.  The results are interesting.  Since Google eats disk drives like coal in a power plant, they found that age was the #1 factor for drive failure.  Drives are generally good for the first 3 years.  Failures start to climb in year 4 and 5.

The paper is called "Failure Trends in a Large Disk Population"

[http://research.google.com/archive/disk_failures.pdf](http://research.google.com/archive/disk_failures.pdf)

The long test scans the entire disk surface.  According to the Google research, after one error of this scan test, the failure rate for that particular drive increases 39 times.  

Some drives perform a short test automatically every so often.  Normally you have to manually run the long test.

You can also run badblocks. 

>sudo apt-get install badblocks

>sudo badblocks /dev/sda

If you do detect some bad blocks then you can work around them with:

>sudo fsck -cc /dev/sda

Good luck.

---

### Post by Bruce M. on 2009-03-17
> **tgalati4 said:**
> The fact that you have ~7200 connection errors (UDMA_CRC_Error_Count) would indicate a cable/power/controller issue.  The logged errors indicate that the drive was in an unknown state--this also points to a cable/power/controller issue.

I assume you have the machine on an UPS.  I also assume that the power supply is OK and not causing hiccups.

Got all the rest savd and will print later. Obviously I took the drive out, I was reinstalling way to many times to be comfortable keeping it in. I do have a place to put it, on my secondary cable as slave to my CD. I'll test it there. This drive came to me second hand, so it's quite possible that it's like me; getting old and showing it in the bones. :)

Now, as to your thoughts posted above regarding: points to a cable/power/controller issue.

The cables are new. They are firmly in place, my drives are always put in "good and snug" so I'm looking at power and controller, and that's on the MB, something I'd prefer not to think about. ($$$) :)

Power is a different issue. - this bldg, to put it nicely, sucks!! And the power issue is a biggie. As for a UPS, I've never owned one, it's a home computer used for email, online banking and entertainment - nothing else - There is nothing "life threatening" or so personal that I'd be in a state of shock/panic if it goes down.

I'll mark this solved, and link to it. When I get the time, I'll let you know the results.

Thank you very much for your time and reply.

Have a nice day.
Bruce

---

### Post by tgalati4 on 2009-03-20
Even home computers can benefit from an UPS.  I buy them used and replace the batteries.

The hard disk controller may be suffering from heat stroke.  They are known to  run hot, and lead-free solder is less tolerant to heat warpage.

---

### Post by Bruce M. on 2009-03-20
> **tgalati4 said:**
> Even home computers can benefit from an UPS.  I buy them used and replace the batteries.

The hard disk controller may be suffering from heat stroke.  They are known to  run hot, and lead-free solder is less tolerant to heat warpage.

I'll look around for a cheap one, but where I am I doubt that's going to happen.

---

### Post by Downtown on 2009-05-10
I figured I'd just add on to this thread instead of starting my own. I just installed Ubuntu 9.04 and now one of my hard drives is getting a SMART error when I boot up. I ran smartctl for a log but I don't understand it. Can anybody make sense of this for me? Thanks in advance.

```
junior@junior-linux:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAKS-55YGA0
Serial Number:    WD-WCAS88415385
Firmware Version: 12.01C02
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat May  9 21:47:38 2009 MST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (13200) seconds.
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
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       321
  3 Spin_Up_Time            0x0003   172   171   021    Pre-fail  Always       -       6400
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       192
  5 Reallocated_Sector_Ct   0x0033   138   138   140    Pre-fail  Always   FAILING_NOW 492
  7 Seek_Error_Rate         0x000e   196   186   051    Old_age   Always       -       49
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1869
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       191
192 Power-Off_Retract_Count 0x0032   190   190   000    Old_age   Always       -       7550
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       7645
194 Temperature_Celsius     0x0022   101   090   000    Old_age   Always       -       49
196 Reallocated_Event_Count 0x0032   148   148   000    Old_age   Always       -       52
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       3
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       2

SMART Error Log Version: 1
ATA Error Count: 78 (device log contains only the most recent five errors)
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

Error 78 occurred at disk power-on lifetime: 897 hours (37 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 60 f7 b8 40  Error: UNC at LBA = 0x00b8f760 = 12121952

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 04 60 f7 b8 2d 08      02:18:23.158  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:19.916  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:16.690  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:13.747  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:10.787  READ VERIFY SECTOR(S) EXT

Error 77 occurred at disk power-on lifetime: 897 hours (37 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 60 f7 b8 40  Error: UNC at LBA = 0x00b8f760 = 12121952

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 04 60 f7 b8 2d 08      02:18:19.916  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:16.690  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:13.747  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:10.787  READ VERIFY SECTOR(S) EXT
  42 00 08 70 f7 b8 2d 08      02:18:10.777  READ VERIFY SECTOR(S) EXT

Error 76 occurred at disk power-on lifetime: 897 hours (37 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 60 f7 b8 40  Error: UNC at LBA = 0x00b8f760 = 12121952

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 04 60 f7 b8 2d 08      02:18:16.690  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:13.747  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:10.787  READ VERIFY SECTOR(S) EXT
  42 00 08 70 f7 b8 2d 08      02:18:10.777  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:18:06.939  READ VERIFY SECTOR(S) EXT

Error 75 occurred at disk power-on lifetime: 897 hours (37 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 60 f7 b8 40  Error: UNC at LBA = 0x00b8f760 = 12121952

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 04 60 f7 b8 2d 08      02:18:13.747  READ VERIFY SECTOR(S) EXT
  42 00 04 60 f7 b8 2d 08      02:18:10.787  READ VERIFY SECTOR(S) EXT
  42 00 08 70 f7 b8 2d 08      02:18:10.777  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:18:06.939  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:18:03.133  READ VERIFY SECTOR(S) EXT

Error 74 occurred at disk power-on lifetime: 897 hours (37 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 60 f7 b8 40  Error: UNC at LBA = 0x00b8f760 = 12121952

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 04 60 f7 b8 2d 08      02:18:10.787  READ VERIFY SECTOR(S) EXT
  42 00 08 70 f7 b8 2d 08      02:18:10.777  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:18:06.939  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:18:03.133  READ VERIFY SECTOR(S) EXT
  42 00 08 68 f7 b8 2d 08      02:17:59.328  READ VERIFY SECTOR(S) EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

I had to RMA another drive that was identical to this one last month after some SMART errors. It never failed, but I didn't want to risk it. It was a hassle though so I'm trying to avoid it this time. I thought it was mounted in my case wrong because it was making a lot of vibrating noise so I took it out and reinstalled it. The vibrating stopped but the error is still there.

---

