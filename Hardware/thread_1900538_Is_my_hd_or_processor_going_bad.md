---
title: "Is my hd or processor going bad?"
date: 2011-12-26
forum: Hardware
---

### Post by ubume2 on 2011-12-26
I have a 4 yr old Dell 500 series Desktop with 80 gig HD, 1gig RAM, 3ghz processor. an Intel 810 video card.

I have Ubuntu 10.04, 11.10, Xubuntu 11.10, and Win XP installed, and have been using Linux successfully for some years.

Lately, I have had problems with all the Linux distros.  Typical symptoms: running an app and unable to close it.  Buttons won't respond. It takes a hard reboot to get back into my Desktops. (when it happens I get the same symptoms on 10.04,11.10), and Xubuntu. A couple of times the systems start to work again.

I can run Puppy Live CD or Ubuntu live CD with no problem.  I can also run Win XP without any symptoms.

I am thinking processor or HD going bad, but wouldn't I have the same problem with Live CD's and XP?

Help would be appreciated. Thanks.

---

### Post by lindsay7 on 2011-12-26
Seems to me that if you can run the live os's and windows the cpu is ok, Run the Disk Utility found under the systems/administration menu and note the maker of your hard drive, check there website for hard drive trouble shooting applications or tests. Most hard drive mfgs have a way to check if your drive is going bad. It could also be new kernel updates that may have something that your computer does not like, You might try going back to an older kernel and see if those work better for you.

---

### Post by sgtGarcia on 2011-12-26
Install:
```
sudo apt-get install smartmontools
```

Start smartctl in terminal:
```
sudo smartctl -a /dev/sda
``` can be sda or sdb ( whatever You have in system )

Then You will see bunch of text of which most important is table which will look something like that:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   070   070   025    Pre-fail  Always       -       9185
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       143
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2467
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       152
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   057   000    Old_age   Always       -       35 (Lifetime Min/Max 18/43)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       159

SMART Error Log Version: 1
No Errors Logged

```

Post that table here. We will look what's wrong.

---

### Post by saneearth on 2011-12-26
You might also go to the dell support site and download a diagnostic .iso and burn a disc. You can test all the hardware this way and it typically eliminates possibilities and narrows it down to a specific issue. I would run the full diagnostic. It takes a long time, but is worth it if you want to identify the specific issue. It could even be a memory issue or video.

---

### Post by khelben1979 on 2011-12-26
I think so.

Make backups and replace the hard disc.

---

### Post by MoreOrLess on 2011-12-26
> **khelben1979 said:**
> Make backups and replace the hard disc.

Slow down. You're jumping the gun, there.

There's an easy way to rule out issues with the hard disk - use a Live CD/USB (and make sure it's not using any swap on the hard disk). If you have easy access to it, just unplug the disk and use a live distro until it shows issues or you're satisfied that it's okay.

Running at least one full pass of memtest is also highly recommended.

---

### Post by ubume2 on 2011-12-26
This is the readout using smartmontools

{QUOTE]
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K80 series
Device Model:     HDS728080PLA380
Serial Number:    PFDBU0SYTVENKX
Firmware Version: PF2OA63A
User Capacity:    80,000,000,000 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Mon Dec 26 16:33:29 2011 CST
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
data collection: 		 (1828) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       1
  2 Throughput_Performance  0x0004   158   158   050    Old_age   Offline      -       213
  3 Spin_Up_Time            0x0007   119   119   024    Pre-fail  Always       -       168 (Average 167)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1002
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   142   142   020    Old_age   Offline      -       28
  9 Power_On_Hours          0x0012   094   094   000    Old_age   Always       -       44921
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       843
192 Power-Off_Retract_Count 0x0032   099   099   050    Old_age   Always       -       1743
193 Load_Cycle_Count        0x0012   099   099   050    Old_age   Always       -       1743
194 Temperature_Celsius     0x0002   152   152   000    Old_age   Always       -       36 (Lifetime Min/Max 12/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 20 (device log contains only the most recent five errors)
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

Error 20 occurred at disk power-on lifetime: 13074 hours (544 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1d 25 64 e0  Error: UNC 8 sectors at LBA = 0x0064251d = 6563101

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 d8 08 1d 25 64 e0 00      00:18:08.200  READ DMA
  c8 d8 01 00 00 00 e0 00      00:18:08.200  READ DMA
  c8 d8 08 1d 25 64 e0 00      00:18:04.100  READ DMA
  c8 d8 08 8d e8 62 e0 00      00:18:04.100  READ DMA
  c8 d8 08 85 e8 62 e0 00      00:18:04.100  READ DMA

Error 19 occurred at disk power-on lifetime: 13074 hours (544 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1d 25 64 e0  Error: UNC 8 sectors at LBA = 0x0064251d = 6563101

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 d8 08 1d 25 64 e0 00      00:18:04.100  READ DMA
  c8 d8 08 8d e8 62 e0 00      00:18:04.100  READ DMA
  c8 d8 08 85 e8 62 e0 00      00:18:04.100  READ DMA
  c8 d8 08 2d 93 c6 e2 00      00:18:04.100  READ DMA
  c8 d8 08 7d e8 62 e0 00      00:18:04.100  READ DMA

Error 18 occurred at disk power-on lifetime: 13074 hours (544 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1d 25 64 e0  Error: UNC 8 sectors at LBA = 0x0064251d = 6563101

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 d8 08 1d 25 64 e0 00      00:17:59.600  READ DMA
  c8 d8 01 00 00 00 e0 00      00:17:59.600  READ DMA
  c8 d8 08 1d 25 64 e0 00      00:17:55.500  READ DMA
  c8 d8 08 8d e8 62 e0 00      00:17:55.500  READ DMA
  c8 d8 08 85 e8 62 e0 00      00:17:55.500  READ DMA

Error 17 occurred at disk power-on lifetime: 13074 hours (544 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1d 25 64 e0  Error: UNC 8 sectors at LBA = 0x0064251d = 6563101

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 d8 08 1d 25 64 e0 00      00:17:55.500  READ DMA
  c8 d8 08 8d e8 62 e0 00      00:17:55.500  READ DMA
  c8 d8 08 85 e8 62 e0 00      00:17:55.500  READ DMA
  c8 d8 08 2d 93 c6 e2 00      00:17:55.500  READ DMA
  c8 d8 08 7d e8 62 e0 00      00:17:55.500  READ DMA

Error 16 occurred at disk power-on lifetime: 13074 hours (544 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1d 25 64 e0  Error: UNC 8 sectors at LBA = 0x0064251d = 6563101

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 d8 08 1d 25 64 e0 00      00:17:03.900  READ DMA
  c8 d8 01 00 00 00 e0 00      00:17:03.900  READ DMA
  c8 d8 08 1d 25 64 e0 00      00:16:59.800  READ DMA
  c8 d8 08 8d e8 62 e0 00      00:16:59.800  READ DMA
  c8 d8 08 85 e8 62 e0 00      00:16:59.800  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short captive       Completed without error       00%     13074         -
# 2  Short offline       Completed without error       00%         0         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
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

### Post by sgtGarcia on 2011-12-26
Apart from age of Your disk ( 44921hours=~5years ) & some READ DMA ERRORS ( last one, was on 13074 hours so it was long time ago ) this disk is ok.
I think Your problem lies elsewhere.

---------EDIT-------------

I was WRONG!!!!!

This:
```
Error: UNC 8 sectors at LBA = 0x0064251d = 6563101
```are probably sectors pending for reallocation.
So this can be signs of degrading of disk.

But let's wait for someone with more knowledge.

---

### Post by MoreOrLess on 2011-12-27
8 sectors over 5 years with none failing recently is nothing to panic about. Memtest is still highly recommended...

---

### Post by ryanspano7 on 2011-12-27
Thanks for the posting.[metaburn]("http://metaburnproduct.weebly.com")

---

### Post by ubume2 on 2011-12-27
I did 3 passes of memtest86+ v4 with no errors.

When on 11.10, I was running Audacity, editing an mp3 file. I got a popup stating running out of memory and to try emptying trash. I have over 6 gig of space left.

I am currently on 10.04.  I can't close apps with the close,minimize,maximize buttons.  The menu system is unresponsive if I have an app up. I can minimize using Ctrl+Alt+D and then close from the panel.  The mouse is generally unusable. Can't edit, highlight text or move to a different line.

I am expecting the same response when I boot back into 11.10.

Edit: I am now getting the same responses as I did when running 10.04.
Edit2: Then completely normal on both for a while.

---

### Post by MoreOrLess on 2011-12-27
Then it does sound like a bad CPU and/or memory controller.

---

### Post by ubume2 on 2011-12-28
I ran Ubuntu 10.04 Live CD for about 6 hours yesterday with no problems. I didn't run any heavy apps though.

Today, 10.04 was hardly functional. After going into 11.10, and rebooting to 10.04 things were normal (for now)
Right now I am on 11.10, and things seem to be running normally. I downloaded cpuburn and from terminal did burnP5 for about a minute while downloading an flv file and using audacity to edit and save an mp3 file. Still no problems.

I noticed the fan started to run and did so for about two minutes before it stopped.  The fan has seemed to run very rarely in the past.

Edit: I am using burnP6. no problems apparent after 10 minutes of burning. cpu usage less on 10.04 compared to 11.10.

Edit: 1/6/12 no problem after 6 days. I'd like to believe that the computer healed itself.  But likely will see problems shortly.

---

