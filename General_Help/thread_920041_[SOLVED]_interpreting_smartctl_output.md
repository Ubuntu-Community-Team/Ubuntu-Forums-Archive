---
title: "[SOLVED] interpreting smartctl output"
date: 2008-09-14
forum: General Help
---

### Post by hwttdz on 2008-09-14
How does one interpret smartctl output.  I assume the raw value is the value of my hardware, so what's the first value.  The threshold is where one needs to start worrying?  Does this look like my drive is in danger of imminent failure?  What's the "TA_increase_count"?  Thanks a bunch.  

```
user 21:31:02 @ phoenix ~ >> sudo smartctl --all -d sat /dev/sda -F samsung2
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD501LJ
Serial Number:    S0MUJ13P318613
Firmware Version: CR100-10
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Sun Sep 14 21:31:21 2008 EDT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection: 		 (8814) seconds.
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
recommended polling time: 	 ( 150) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   015    Pre-fail  Always       -       4992
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       612
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3181
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       487
187 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   072   063   000    Old_age   Always       -       28
194 Temperature_Celsius     0x0022   154   127   000    Old_age   Always       -       28
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       41774053
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   253   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0032   100   100   000    Old_age   Always       -       1

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3181         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
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

### Post by cariboo on 2008-09-14
> TA_increase_count"

Most of the output is vendor specific have a look at:

```
man smartctl
```

There is information in there specific to Samsung drives.

Jim

---

### Post by hwttdz on 2008-09-15
Yeah, the only information in there specific to samsung drives that I saw was where it told you you can specify -F samsung or samsung2.  I would have said it was a more recent even though the firmware doesn't end in 23, but if I do samsung I get the same output.  I believe I am running the command correctly and that it is producing the correct output.  I just don't know what the output means, and I think the man page assumes perhaps a more intelligent consumer?

---

### Post by hwttdz on 2008-09-15
Does anyone else have advice?

---

### Post by caljohnsmith on 2008-09-15
> **hwttdz said:**
> 
```

Device Model:     SAMSUNG HD501LJ
Serial Number:    S0MUJ13P318613
Firmware Version: CR100-10
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Sun Sep 14 21:31:21 2008 EDT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
[COLOR="Red"]SMART overall-health self-assessment test result: PASSED[/COLOR]


```
The main thing is what is highlighted above: your HDD's overall health is "PASSED", which is good. :) The "TA increase count" might mean "Torque Amplification Count" I think, but you can get more details about most of those SMART parameters in the [Wikipedia article on SMART HDD technology]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology"). Or if you find any other good resources in your search, let me know, as that could be useful. :)

---

### Post by hwttdz on 2008-09-15
Most of what I was curious about was in the man page, and it's my fault for not reading it more carefully.  In summary:

RAW_VALUE: this is the only thing with real or physical meaning, generally these are the counts or the measurements

VALUE, WORST and THRESH are all reported in the same arbitrary units, which normalize the raw value to 0-255, where bigger is better.  VALUE is the current value, WORST is the worst that has been recorded while the disk is functioning, and THRESH is the floor that you want to stay above.

Or at least that's what the man page says, it appears that this is one of those things that no one follows conventions on, and it appears my drive is normalizing some things to 100, such as raw read error rate (which has a raw value of 0, perfect, and therefore should transform to 255).  So, in conclusion I'm not freaking out terribly much about this drive dying tomorrow.

---

### Post by firekage on 2012-09-09
Sorry for refreshing but i have one question. I performed scan with smartctl in terminal, i waited for 54 minutes and...the question is - where i should look to for a output of this test? If i use gsmartcontrol than i see output in gui mode, but where i should look for it when i use terminal command? Where it is stored for viewing? I don't see it in /var/log

---

### Post by wildmanne39 on 2012-09-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

