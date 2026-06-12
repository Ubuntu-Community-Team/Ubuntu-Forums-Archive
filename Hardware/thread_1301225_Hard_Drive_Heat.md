---
title: "Hard Drive Heat"
date: 2009-10-25
forum: Hardware
---

### Post by Mosabama on 2009-10-25
I am posting this again because I had enough of this problem hoping some one will help me this time (after 1 year of looking for a silution)

MY HARD DISK HEATS!!! I have to use a cooler under the laptop ALWAYS so that the harddisk temp to stay below 50 C!

I didnt have such a problem with windows 2 years ago.

I had this problem with another DELL laptop a year ago ...exact same thing.

ps. the load cycle count doesn't increase (if it increases it will every couple of hours) (maybe thats the problem)

the following is the result of the "sudo smartctl --all /dev/sda " command:

```

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1600BEVT-60ZCT0
Serial Number:    WD-WXC408517483
Firmware Version: 11.01A11
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Oct 26 04:13:53 2009 GST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x02)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (5160) seconds.
Offline data collection
capabilities: 			 (0x51) SMART execute Offline immediate.
					No Auto Offline data collection support.
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
recommended polling time: 	 (  64) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0027   159   157   021    Pre-fail  Always       -       1008
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2710
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       3697
 10 Spin_Retry_Count        0x0033   100   096   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1653
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       12885098500
190 Airflow_Temperature_Cel 0x0022   055   039   040    Old_age   Always   In_the_past 45
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       354
193 Load_Cycle_Count        0x0032   173   173   000    Old_age   Always       -       81242
194 Temperature_Celsius     0x0022   098   082   000    Old_age   Always       -       45
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 4
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

Error 4 occurred at disk power-on lifetime: 2424 hours (101 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 a8 48 f9 14 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 67 4b 51 06 08      00:43:50.935  READ FPDMA QUEUED
  61 28 58 df fe 14 10 08      00:43:50.935  WRITE FPDMA QUEUED
  61 80 50 57 fe 14 10 08      00:43:50.935  WRITE FPDMA QUEUED
  61 00 48 57 fa 14 10 08      00:43:50.935  WRITE FPDMA QUEUED
  61 00 40 57 f6 14 10 08      00:43:50.935  WRITE FPDMA QUEUED

Error 3 occurred at disk power-on lifetime: 2423 hours (100 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 00 86 d7 14 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 e8 48 8f 12 2a 0a 08      00:23:38.843  WRITE FPDMA QUEUED
  61 58 80 37 0f 2a 0a 08      00:23:38.843  WRITE FPDMA QUEUED
  61 28 40 0f d5 14 10 08      00:23:38.841  WRITE FPDMA QUEUED
  61 58 38 b7 d3 14 10 08      00:23:38.840  WRITE FPDMA QUEUED
  61 f8 30 bf d2 14 10 08      00:23:38.839  WRITE FPDMA QUEUED

Error 2 occurred at disk power-on lifetime: 2355 hours (98 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 01 86 0b bd 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 78 7f 0b bd 09 08      01:17:01.546  WRITE FPDMA QUEUED
  61 08 70 57 0b bd 09 08      01:17:01.546  WRITE FPDMA QUEUED
  61 10 68 3f 0b bd 09 08      01:17:01.546  WRITE FPDMA QUEUED
  61 08 60 2f 0b bd 09 08      01:17:01.546  WRITE FPDMA QUEUED
  61 08 58 27 0b bd 09 08      01:17:01.545  WRITE FPDMA QUEUED

Error 1 occurred at disk power-on lifetime: 2355 hours (98 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 00 df 8d 0d 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 10 df 8d 0d 10 08      01:16:05.528  WRITE FPDMA QUEUED
  61 20 08 0f e1 c1 09 08      01:16:05.528  WRITE FPDMA QUEUED
  61 e0 00 c7 d0 c1 09 08      01:16:05.527  WRITE FPDMA QUEUED
  61 08 00 af 8a bd 09 08      01:16:00.543  WRITE FPDMA QUEUED
  61 08 00 a7 da e5 08 08      01:16:00.543  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%      3683         -
# 2  Short offline       Completed without error       00%      2515         -
# 3  Short offline       Completed without error       00%      2447         -

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


 Hope some one can end this.

---

### Post by admelfo on 2009-10-25
I'm running Hardy LTS on an old Compaq Armada M300 laptop, and it gets warm, too. At first I worried about it, b/c the machine is old, and I maxed out the RAM and swapped out the old HD with a 60G -- was worried that the hardware just wasn't up to it, or my fans weren't running right (tried adding sensors, but the chip in this puppy doesn't support them). But, in looking around, it seems that laptop HD temps of up to C 70 are pretty -- so I stopped worying about it.

If you've never cleaned it, try that -- maybe you have a bunch of dust build up. Some machines seem to run hotter than others. I know it's confusing -- b/c back when this laptop was new, and running Windows, I never noticed the heat. ~shrugs~

---

### Post by admelfo on 2009-10-25
Here's one of many forum discussions on [this topic]("http://ubuntuforums.org/showthread.php?t=1129135&highlight=%27acceptable+hd+temp+laptops%27"), if you haven't seen it. Good luck. I'd be interested to hear if you come up with a solution.

---

### Post by Mosabama on 2009-10-25
same thing in single mode 

I restarted 2 times ... and the load cycle count increased 10 .. if this can help!

---

### Post by Mosabama on 2010-03-12
I cleaned it from dust ... no process consumes the CPU.

Simply th HDD doesnt heat with windows ! and I am still dreaming of putting the laptop on my lap ... it would reach 60 C if I do that.

is it possible that no one suffered from this problem !!! same thing happened to me with 2 laptops and 3 HDDs ... its really wierd that there is no solution for this !!

---

### Post by Mosabama on 2010-03-28
ok ... this may help:

when I use a command like hdparm -y (or -Y) to manually put the HDD in a standby or sleep mode .. it won't .
Actually it does but in less than a second it will go active again ... I am sure of that because when I make the command I could hear the hard disk spin down and in less than a second I could hear it spinup again.

Nothing is accessing the HDD repeatidly .. I checked with iotop -o

---

### Post by Mosabama on 2010-03-28
by the way .. the load count cycle today is 83400 !!! please look at the date of to day and compare this value with my first post in 2008 .. !!!!

it increased only 2000 somthing in during the 2 years ... !!!!! its clearly not spinning down.

---

### Post by Mosabama on 2010-03-29
when I run linux from USB (live) and try the command "hdparm -y /dev/sda" it actually stops spinning .. but not whan I am running ubuntu from the sda drive ... its wont spindown.
I am adding these comments hoping some one will find me a solution .. cause I have been suffering from this problem for about 2 years now .. 2 laptops and 3 harddisks.

---

### Post by abdusamed on 2010-06-19
this bug can actually destroy hd

---

