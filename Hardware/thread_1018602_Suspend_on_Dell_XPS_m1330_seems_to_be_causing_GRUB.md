---
title: "Suspend on Dell XPS m1330 seems to be causing GRUB problems"
date: 2008-12-22
forum: Hardware
---

### Post by potiphera on 2008-12-22
Hi, I have a Dell XPS m1330 laptop running Hardy, and lately using suspend has been causing problems: when I try to resume from suspend, GRUB will either give me the prompt that says "minimal bash-like editing is supported" or show [Error 18]("http://wiki.linuxquestions.org/wiki/GRUB#Error_18").  Then after I reboot a couple of times, it starts up fine.  What should I do to fix this?

---

### Post by caljohnsmith on 2008-12-22
Are you trying to resume from a suspend or hibernation? If it is hibernation, then this thread might help you:

[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Let me know if that helps at all.

---

### Post by potiphera on 2008-12-22
Thanks for the response! The problem occurs when I resume after putting it in the low-power suspend mode, but it may happen with hibernate as well.  (I'm not sure because I don't usually use hibernate, and the problem isn't always reproducible.)

However, this laptop has an Intel processor, so I'm not sure if that thread describes my problem.

---

### Post by sdennie on 2008-12-22
Grub shouldn't come into play when using suspend.  Are you positive you are using suspend and not hibernate?

---

### Post by potiphera on 2008-12-22
That makes sense.  It's my mom's computer and this is the problem as she described it to me, so I'll have to check with her :).  I haven't managed to reproduce the error myself.

The other possibility that occurs to me is that sometimes I get some random errors as it's going into suspend, so maybe occasionally it fails and shuts down instead?  Suspend is rather temperamental in general on this computer -- I find that sometimes it just hangs on a blinking cursor after exiting Gnome.

---

### Post by potiphera on 2008-12-22
I talked to her about it, and she doesn't usually check what happens after she clicks on "suspend," but it looks like the blinking-cursor hang happens quite often.  So I think I'm going to try some of the fixes in [http://ubuntuforums.org/showthread.php?t=807593](http://ubuntuforums.org/showthread.php?t=807593).

---

### Post by potiphera on 2008-12-23
By the way, getting suspend to work properly wouldn't be as much of a priority if I could just get Gnome to start up faster when turning the computer on from being shut off.  Ubuntu seems to take a pretty normal amount of time starting, but then after the login screen, it takes about 80 seconds for the GUI to load fully.  Is this normal for laptops?

---

### Post by potiphera on 2009-01-04
(bump)

I've gotten a chance to look at this computer again, and suspend isn't the problem (and the thread title is thus inaccurate) -- rather, it occurs when I turn the computer on, usually after it's been off a while.  If suspend causes it, it's because suspend fails and the battery dies (so the thread title is inaccurate).

When I turn the computer on, I've observed any of several behaviors:

a) GRUB error saying "minimal BASH-like editing is supported," and often Error 18.
b) Just now, I got {DRDY err} errors like the ones described [here]("http://ubuntuforums.org/showthread.php?t=937872").
c) The last time there was a scheduled fsck, there were some faulty inodes, which I repaired, but that didn't seem to affect this issue.

This wouldn't be as pressing an issue if suspend worked properly, which it often doesn't.

Also, I reprofiled the bootup a while back by following [this guide]("http://ubuntuforums.org/showthread.php?t=254263").  Could that have screwed something up?

---

### Post by caljohnsmith on 2009-01-04
Considering the inconsistent behavior that computer has, and also considering that fsck found faulty inodes when most likely it shouldn't have if your system was running OK, I'm inclined to think that you could have a hardware problem at this point. I would run the "memtest86+" option from the Grub menu to see if it finds anything wrong with your computer's memory, but the main thing I would check would be the health of your HDD. You can run a "SMART" test on the HDD from Ubuntu to check its integrity by doing the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so we can see the results.

---

### Post by potiphera on 2009-01-05
Thanks! I had installed smartmontools a while back to see if I should apply the head-parking fix -- unfortunately, I never figured out whether I should or not because some of the SMART values seemed to be totally off.  The sda_health_before_test.txt says it's going to fail within 24 hours, but I think it also told me that several months ago.  The value for Head_Flying_Hours is 43851616095157, which can't be right, because that would be 5 billion years.

I ran sudo smartctl -t long /dev/sda and it tells me that it will take 111 minutes, but then sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status" gives me

```
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
```

...so is the self-test not working, or what?

---

### Post by potiphera on 2009-01-05
Also, the content of sda_health_before_test.txt is:> smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST9200420ASG
Serial Number:    5SH09LF4
Firmware Version: 3.ADD
User Capacity:    200,049,647,616 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan  5 00:00:17 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
Offline data collection
capabilities: 			 (0x53) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
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
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   098   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1294
  5 Reallocated_Sector_Ct   0x0033   001   001   036    Pre-fail  Always   FAILING_NOW 42622
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       12928394660
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2990
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1317
187 Unknown_Attribute       0x0032   079   079   000    Old_age   Always       -       21
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   062   045   045    Old_age   Always   In_the_past 723714086
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       917
193 Load_Cycle_Count        0x0022   021   021   000    Old_age   Always       -       158099
194 Temperature_Celsius     0x001a   038   055   000    Old_age   Always       -       38 (Lifetime Min/Max 0/16)
195 Hardware_ECC_Recovered  0x0012   061   047   000    Old_age   Always       -       84493910
197 Current_Pending_Sector  0x0010   099   098   000    Old_age   Offline      -       30
198 Offline_Uncorrectable   0x003e   099   098   000    Old_age   Always       -       30
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 43851616095157
241 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 1665522197
242 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 513194
254 Unknown_Attribute       0x0000   001   001   000    Old_age   Offline      -       1

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

Error 22 occurred at disk power-on lifetime: 2976 hours (124 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 60 00 58 e0  Error: UNC at LBA = 0x00580060 = 5767264

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 ff 3f 55 00 58 e0 00      00:00:06.939  READ DMA EXT
  25 ff 06 4f 00 58 e0 00      00:00:06.938  READ DMA EXT
  c8 ff 3f 7e 00 00 e0 00      00:00:06.938  READ DMA
  c8 ff 3f 5c 28 00 e0 00      00:00:06.938  READ DMA
  c8 ff 05 57 28 00 e0 00      00:00:06.938  READ DMA

Error 21 occurred at disk power-on lifetime: 2976 hours (124 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 6e 00 58 e0  Error: UNC at LBA = 0x0058006e = 5767278

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 ff 3f 55 00 58 e0 00      00:00:06.955  READ DMA EXT
  25 ff 06 4f 00 58 e0 00      00:00:06.955  READ DMA EXT
  c8 ff 3f 7e 00 00 e0 00      00:00:06.955  READ DMA
  c8 ff 3f 5c 28 00 e0 00      00:00:06.955  READ DMA
  c8 ff 05 57 28 00 e0 00      00:00:07.010  READ DMA

Error 20 occurred at disk power-on lifetime: 2935 hours (122 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5f 00 58 e0  Error: UNC at LBA = 0x0058005f = 5767263

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 ff 3f 55 00 58 e0 00      00:00:06.515  READ DMA EXT
  25 ff 06 4f 00 58 e0 00      00:00:06.515  READ DMA EXT
  c8 ff 3f 7e 00 00 e0 00      00:00:06.515  READ DMA
  c8 ff 3f 5c 28 00 e0 00      00:00:06.515  READ DMA
  c8 ff 05 57 28 00 e0 00      00:00:06.571  READ DMA

Error 19 occurred at disk power-on lifetime: 2935 hours (122 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5f 00 58 e0  Error: UNC at LBA = 0x0058005f = 5767263

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 ff 3f 55 00 58 e0 00      00:00:06.516  READ DMA EXT
  25 ff 06 4f 00 58 e0 00      00:00:06.516  READ DMA EXT
  c8 ff 3f 7e 00 00 e0 00      00:00:06.516  READ DMA
  c8 ff 3f 5c 28 00 e0 00      00:00:06.516  READ DMA
  c8 ff 05 57 28 00 e0 00      00:00:06.571  READ DMA

Error 18 occurred at disk power-on lifetime: 2935 hours (122 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b9 0c 5c e0  Error: UNC at LBA = 0x005c0cb9 = 6032569

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 ff 3f a2 0c 5c e0 00      00:00:12.934  READ DMA EXT
  25 ff 3f 63 0c 5c e0 00      00:00:12.934  READ DMA EXT
  25 ff 3f 24 0c 5c e0 00      00:00:12.933  READ DMA EXT
  25 ff 3f e5 0b 5c e0 00      00:00:12.932  READ DMA EXT
  25 ff 3f a6 0b 5c e0 00      00:00:12.932  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         3         -
# 2  Short offline       Completed without error       00%         0         -

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

### Post by caljohnsmith on 2009-01-05
As I suspected, it unfortunately looks like your HDD is on its last legs. If I were in your shoes, I would immediately try to backup any important data that you have on the drive if you have not done so all ready, and then scrap the HDD for recycling. The test returned multiple errors, and the overall health assessment is "FAILED", so I think that about says it all. It's up to you what you want to do, but if I were in your situation, I would invest in a new HDD. Good luck and let me know how it goes. :)

---

### Post by potiphera on 2009-01-05
Thanks! There are only a few personal files to back up, but I'd also like to back up the system files so I don't have to re-tweak everything... Google tells me Remastersys may be what I need for the job?

Also, did Ubuntu kill the drive (due to the load cycle issue)?  I've only had Ubuntu on that computer for maybe 8 months or less (it's running Hardy).  Then again, I seem to remember that there were some repeating file-corruption issues when it was running Vista, and the computer has had some [other hardware issues]("http://ubuntuforums.org/showthread.php?t=822815") as well.

---

### Post by caljohnsmith on 2009-01-05
> **potiphera said:**
> Thanks! There are only a few personal files to back up, but I'd also like to back up the system files so I don't have to re-tweak everything... Google tells me Remastersys may be what I need for the job?

Also, did Ubuntu kill the drive (due to the load cycle issue)?  I've only had Ubuntu on that computer for maybe 8 months or less (it's running Hardy).  Then again, I seem to remember that there were some repeating file-corruption issues when it was running Vista, and the computer has had some [other hardware issues]("http://ubuntuforums.org/showthread.php?t=822815") as well.
I've never used Remastersys, but it looks like it will do a full system backup, which considering the state of your HDD, that may not help you if it backs up corrupted system files. If you know which system files you tweaked in the past, like /etc/X11/xorg.conf for example, I think I would save those manually if I were you. I really don't think that Ubuntu in itself would be at fault of damaging the HDD, but it could be that you installed software that possibly misused the HDD (although I doubt it); if Vista had the same problem, then that would indicate it's highly unlikely it is Vista's or Ubuntu's fault. Anyway, good luck and hope you can get a new HDD soon so you at least won't have a bad HDD to deal with. :)

---

