---
title: "Hard Drive has 10 bad sectors, could it just be a bug?"
date: 2010-05-06
forum: Hardware
---

### Post by TheNerdAL on 2010-05-06
Well my hard drive has 10 bad sectors. 

I posted this forum: [http://ubuntuforums.org/showthread.php?t=1475083](http://ubuntuforums.org/showthread.php?t=1475083)

I had troubles with Ubuntu booting up and stuff so Wee_Guy thought it would be bad sectors on the hard drive and he might be correct, but I also heard that Ubuntu Disk Utility has some bugs still, I don't know though. 

I attached a screen shot of Ubuntu Disk Utility. 

I am running on a Live CD right now. 

Thanks.

---

### Post by andrewc6l on 2010-05-06
Seeing a few bad sectors isn't a big deal. With most modern hard drives, bad sectors are mapped out by the hard drive silently and you never need to worry. There are a number of "unallocated" sectors that get mapped to the bad sectors.

However, if you see that number increasing, then eventually you really will have bad sectors - at that point, the hard drive is pretty far gone (in other words, close to death).

You might want to try running fsck on your hard drive from when booting from the Live CD just to see if the file system is corrupt. If it is, fsck can usually fix it. If it's not, I'd bet it's more likely to be a driver issue / incompatibility (especially if it started happening after an update).

---

### Post by TheNerdAL on 2010-05-06
> **andrewc6l said:**
> Seeing a few bad sectors isn't a big deal. With most modern hard drives, bad sectors are mapped out by the hard drive silently and you never need to worry. There are a number of "unallocated" sectors that get mapped to the bad sectors.

However, if you see that number increasing, then eventually you really will have bad sectors - at that point, the hard drive is pretty far gone (in other words, close to death).

You might want to try running fsck on your hard drive from when booting from the Live CD just to see if the file system is corrupt. If it is, fsck can usually fix it. If it's not, I'd bet it's more likely to be a driver issue / incompatibility (especially if it started happening after an update).

Does Linux automatically Mark the bad sectors?

---

### Post by andrewc6l on 2010-05-06
It's actually done in the hardware (below the OS layer - in the drive's firmware). S.M.A.R.T. drives then report the number of sectors they've remapped.

---

### Post by TheNerdAL on 2010-05-06
So it does it automatically?

---

### Post by andrewc6l on 2010-05-07
Yes. Here's a little more info:

[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

---

### Post by TheNerdAL on 2010-05-09
That's weird, now it has 8 bad sectors.

---

### Post by urbanus on 2010-05-09
I have had Linux report bad sectors and faulty hard drive when it really wasn't (still using it/them). I read that many people have experienced this. There was talk about the "disk tool" (not sure which) is giving false positives (says there faults when there isn't).

So, probably, don't worry....but always backup important stuff ;-)

---

### Post by dpiwowarski on 2010-05-10
@TheNerdAL: show us output of
```
smartctl -a /dev/sda
```

---

### Post by TheNerdAL on 2010-05-10
> **dpiwowarski said:**
> @TheNerdAL: show us output of
```
smartctl -a /dev/sda
```

The program 'smartctl' is currently not installed.  You can install it by typing:
sudo apt-get install smartmontools

---

### Post by dpiwowarski on 2010-05-11
Ok, so first
```
sudo apt-get install smartmontools
```
and then
```
smartctl -a /dev/sda
```

---

### Post by BlacqWolf on 2010-05-11
i doubt its a bug.....

lets just face it. ubuntu only does to your hd what your bios/hd firmware tells it to do, instead of overriding it like os x/windows. this causes your hard disk to normally have a VERY short life. for example.... my friend was using another distro of ubuntu linux. his hd life: 100 days.

i got that taken care of with my pc, but now will someone help me with my net download resetting problem?

i cant even download a 24mb file without it getting errors

---

### Post by TheNerdAL on 2010-05-11
> **dpiwowarski said:**
> Ok, so first
```
sudo apt-get install smartmontools
```
and then
```
smartctl -a /dev/sda
```

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 9 family
Device Model:     Maxtor 6Y160P0
Serial Number:    Y47E2PQE
Firmware Version: YAR41BW0
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue May 11 15:11:33 2010 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 302) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  69) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   221   206   063    Pre-fail  Always       -       12760
  4 Start_Stop_Count        0x0032   251   251   000    Old_age   Always       -       4996
  5 Reallocated_Sector_Ct   0x0033   253   252   063    Pre-fail  Always       -       8
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   251   241   187    Pre-fail  Always       -       37481
  9 Power_On_Minutes        0x0032   219   219   000    Old_age   Always       -       45h+46m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   241   241   000    Old_age   Always       -       4740
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       28
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       1059
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       1
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   195   195   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 2039 inconsistent with error log pointer 5

ATA Error Count: 2039 (device log contains only the most recent five errors)
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

Error 2039 occurred at disk power-on lifetime: 11267 hours (469 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c7 d2 10 e1  Error: UNC 1 sectors at LBA = 0x0110d2c7 = 17879751

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 d2 10 e1 08      02:37:44.992  READ DMA
  ec 00 00 00 00 00 a0 0a      02:37:44.976  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 0a      02:37:44.976  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 0a      02:37:44.960  IDENTIFY DEVICE
  c8 00 08 c7 d2 10 e1 08      02:37:43.952  READ DMA

Error 2038 occurred at disk power-on lifetime: 11267 hours (469 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c7 d2 10 e1  Error: UNC 1 sectors at LBA = 0x0110d2c7 = 17879751

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 d2 10 e1 08      02:37:43.952  READ DMA
  ec 00 00 00 00 00 a0 0a      02:37:43.936  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 0a      02:37:43.936  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 0a      02:37:43.920  IDENTIFY DEVICE
  c8 00 08 c7 d2 10 e1 08      02:37:42.912  READ DMA

Error 2037 occurred at disk power-on lifetime: 11267 hours (469 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c7 d2 10 e1  Error: UNC 1 sectors at LBA = 0x0110d2c7 = 17879751

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 d2 10 e1 08      02:37:42.912  READ DMA
  ec 00 00 00 00 00 a0 0a      02:37:42.896  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 0a      02:37:42.896  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 0a      02:37:42.896  IDENTIFY DEVICE
  c8 00 08 c7 d2 10 e1 08      02:37:41.888  READ DMA

Error 2036 occurred at disk power-on lifetime: 11267 hours (469 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c7 d2 10 e1  Error: UNC 1 sectors at LBA = 0x0110d2c7 = 17879751

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 d2 10 e1 08      02:37:41.888  READ DMA
  ec 00 00 00 00 00 a0 0a      02:37:41.856  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 0a      02:37:41.856  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 0a      02:37:41.856  IDENTIFY DEVICE
  c8 00 08 c7 d2 10 e1 08      02:37:40.832  READ DMA

Error 2035 occurred at disk power-on lifetime: 11267 hours (469 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c7 d2 10 e1  Error: UNC 1 sectors at LBA = 0x0110d2c7 = 17879751

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 d2 10 e1 08      02:37:40.832  READ DMA
  ec 00 00 00 00 00 a0 0a      02:37:40.816  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 0a      02:37:40.816  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 0a      02:37:40.816  IDENTIFY DEVICE
  c8 00 08 c7 d2 10 e1 08      02:37:39.792  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     11306         -
# 2  Short offline       Completed without error       00%     11292         -
# 3  Short offline       Completed: read failure       60%     11271         17879758
# 4  Short offline       Completed: read failure       60%     11268         17879758
# 5  Short offline       Completed: read failure       60%     11267         17879758
# 6  Short offline       Completed: read failure       60%     11267         17879758
# 7  Short offline       Completed without error       00%      3462         -

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

### Post by dpiwowarski on 2010-05-12
8 bad sectors. Backup your data and buy new disk. I would do this.

---

