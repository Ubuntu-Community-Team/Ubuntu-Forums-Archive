---
title: "hdd bad sector"
date: 2009-02-07
forum: Hardware
---

### Post by miazma on 2009-02-07
Hello,

do I need a new hdd, because it seems smart has found one bad sector (and badblocks found 3 blocks one at a time)...

```
johannes@luna:~$ sudo smartctl -a /dev/sda1
[sudo] password for johannes: 
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK8034GSX
Serial Number:    Z6I6T15IT
Firmware Version: AH301E
User Capacity:    80.026.361.856 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb  8 05:49:59 2009 CET
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
data collection: 		 ( 120) seconds.
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
recommended polling time: 	 (  61) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1727
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       781
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       10108
 10 Spin_Retry_Count        0x0033   115   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       704
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       234
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       282
193 Load_Cycle_Count        0x0032   038   038   000    Old_age   Always       -       629249
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       40 (Lifetime Min/Max 1/59)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       4233
222 Loaded_Hours            0x0032   082   082   000    Old_age   Always       -       7509
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       398
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 22 (device log contains only the most recent five errors)
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

Error 22 occurred at disk power-on lifetime: 8308 hours (346 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6e e5 5e 40  Error: UNC 1 sectors at LBA = 0x005ee56e = 6219118

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 67 e5 5e 40 00      00:01:34.152  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:26.465  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:18.762  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:11.043  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:03.344  READ DMA

Error 21 occurred at disk power-on lifetime: 8308 hours (346 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6e e5 5e 40  Error: UNC 1 sectors at LBA = 0x005ee56e = 6219118

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 67 e5 5e 40 00      00:01:26.465  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:18.762  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:11.043  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:03.344  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:56.621  READ DMA

Error 20 occurred at disk power-on lifetime: 8308 hours (346 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6e e5 5e 40  Error: UNC 1 sectors at LBA = 0x005ee56e = 6219118

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 67 e5 5e 40 00      00:01:18.762  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:11.043  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:03.344  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:56.621  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:48.902  READ DMA

Error 19 occurred at disk power-on lifetime: 8308 hours (346 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6e e5 5e 40  Error: UNC 1 sectors at LBA = 0x005ee56e = 6219118

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 67 e5 5e 40 00      00:01:11.043  READ DMA
  c8 00 08 67 e5 5e 40 00      00:01:03.344  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:56.621  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:48.902  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:41.230  READ DMA

Error 18 occurred at disk power-on lifetime: 8308 hours (346 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6e e5 5e 40  Error: UNC 1 sectors at LBA = 0x005ee56e = 6219118

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 67 e5 5e 40 00      00:01:03.344  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:56.621  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:48.902  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:41.230  READ DMA
  c8 00 08 67 e5 5e 40 00      00:00:33.496  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     10102         -
# 2  Extended offline    Aborted by host               90%     10102         -
# 3  Extended offline    Completed without error       00%     10099         -
# 4  Extended offline    Aborted by host               10%     10098         -
# 5  Extended offline    Interrupted (host reset)      10%      9490         -

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

I've also run 2 selftests:

# 1  Short offline       Completed without error       00%     10102         -
# 2  Extended offline    Aborted by host               90%     10102         -
# 3  Extended offline    Completed without error       00%     10099         -

and e2fsck -cc -v -f -k /dev/sda1 without any bad blocks found so I'm really not sure. But my Ubuntu is really unstable... and as said badblocks found 3 bad blocks (well, I think all 3 blocks in one sector) before I checked with e2fsck, hm 

greetings,
Johannes

---

### Post by 00b00nt00 on 2009-02-08
Johannes, I think it's time to start backing up your data and investing in a new hard disk. These errors sound terminal, and they're bound to get worse.

Sorry to be the bearer of bad news.

---

### Post by miazma on 2009-02-08
Jep but I'm not sure how to backup my data and all the packages I've installed so far... mh and I haven't got the time right now, because I'm writing my bachelor thesis (which is backed up per svn at the university) :(

---

### Post by caljohnsmith on 2009-02-08
From everything I've read, it is natural over the course of time for a HDD to develop a few bad sectors, and of course the key word here is "few" (which is your case). That's why HDDs come with SMART technology, so if they find one or two bad sectors, they can simply mark them as unusable. In fact, if I remember correctly from my previous research on the subject, modern HDDs typically have bad sectors even when they are shipped, because with today's standards of data density, it is essentially impossible for HDD manufacturer's to make a perfect HDD where all the sectors are usable and still be cost effective. Of course those bad sectors are marked as unusable before the HDD is shipped so you don't have to worry about it, but they still exist. The main thing is your HDD passed the SMART test:
[QUOTE=miazma]```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: [COLOR="green"]PASSED[/COLOR]
```[/QUOTE]
So one or two bad sectors out of 156,301,488 total sectors (the size of your HDD) is not bad at all I think. I would just make sure to run the SMART test at least every few weeks to see if a trend is developing with bad sectors, or if you are just experiencing the bad sectors that come up due to normal aging. Good luck and keep us posted. :)

---

### Post by miazma on 2009-02-08
Hm, are these 3 bad blocks marked now, so that they aren't used anymore, after e2fsck -cc -v -f -k /dev/sda1 and the same for sda2?

The main thing is, that my Ubuntu is really unstable and everytime when Ubuntu (almost) is frozen my hdd LED is blinking like hell. I've also checked my RAM with memtest86+ a month ago (and haven't had bad blocks) because it's so unstable since 4 or 5 months now.

greetings,
Johannes

---

### Post by 00b00nt00 on 2009-02-12
Johannes, memtest will only find errors relating to RAM, not your hard disk (which is the source of the problem).

As you are busy at the moment - save all your important data to a USB flash drive and then boot Ubuntu from a live CD. That way, the computer need not access the hard disk. when you have time, replace the HD and reinstall Ubuntu.

---

