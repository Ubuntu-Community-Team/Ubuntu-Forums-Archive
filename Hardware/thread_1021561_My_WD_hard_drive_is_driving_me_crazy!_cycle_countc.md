---
title: "My WD hard drive is driving me crazy! cycle count/clicking noise/laptop mode related?"
date: 2008-12-25
forum: Hardware
---

### Post by Axx83 on 2008-12-25
I've bought a new western digital scorpio hard drive "WD1600BEVS" for my thinkpad X60s laptop.

With intrepid fresh installed when I unplug the cable and run on battery _the hard drive starts making a loud noise_, it starts spinning very noisy and sometimes it clicks. On AC it is perfectly silent.

I have laptop mode turned off both on ac and on battery, cat /proc/sys/vm/laptop_mode always gives me 0

I have set sudo hdparm -B 255 /dev/sda OR sudo hdparm -B 254 /dev/sda but the noise when I unplug is there no matter what, with this hdparm setting or without.

I have turned off gnome power manager in gconf-settings, no difference.

The noise is similar to when I'm transferring a lot of files, but actually I'm doing nothing at all.

Please help me...

---

### Post by Axx83 on 2008-12-27
Guys please, let me know if someone has the same problem, I firmly believe it's not something broken in the hard disk cause when it's on AC is dead silent.

---

### Post by Bucky Ball on 2008-12-27
Okay, this is a common problem with power management on battery power and should be fixed asap. Until then, try to *avoid running on battery power* as you may *cause serious damage* to your drive. Try this:

[http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html](http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html)

and ...

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

Do a search for 'load cycle count ubuntu hardy' and you will find plenty, but I suggest running the fix in the first link asap if you intend running on battery.

---

### Post by Axx83 on 2008-12-27
Thanks for the reply, I'll see if something changes with the laptop mode deamon because with the hdparm fix the problem is still there

---

### Post by Axx83 on 2008-12-27
Is it possible that the hdparm fix or tuning laptop-mode don't resolve the issue at all ?

The noise is still there and cycle counts grows 1 or 2 units every minute when I run on battery, on AC it's totally different.
On battery, with laptop mode tuned as the website says, probably in an hour it will give 60 or 80 more cycles...

the result of smartctl:
```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1600BEVT-00ZCT0
Serial Number:    WD-WXC508L31813
Firmware Version: 11.01A11
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Dec 27 23:40:42 2008 CET
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
data collection: 		 (5400) seconds.
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
recommended polling time: 	 (  66) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   157   157   021    Pre-fail  Always       -       1116
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       53
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       40
 10 Spin_Retry_Count        0x0033   100   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       34
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1984
194 Temperature_Celsius     0x0022   107   096   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged
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

thanks for the patience

---

### Post by Bucky Ball on 2008-12-27
Post the results of this:

```
date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
```You have installed the smart tools but have you done the actual fix from further down this page:

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

which starts with:

> 3. IF YOU ARE AFFECTED THEN FOLLOW DIRECTIONS HERE TO USE MY FIX - PLEASE READ FULLY AND CAREFULLY AS INCORRECT IMPLEMENTATION WILL NOT PROTECT YOU You need to adjust things to get it right for your circumstances.

---

