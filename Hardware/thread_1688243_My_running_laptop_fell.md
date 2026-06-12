---
title: "My running laptop fell"
date: 2011-02-15
forum: Hardware
---

### Post by ltoso on 2011-02-15
Hi,
my running laptop felled from my hand and when i lifted it was still up but with a frozen screen not responding to keyboard or mouse, i took out the battery put it back in and it was running fine again and ofcourse it is on ubuntu

i want to know, is there a utility that i can run to check if my hard disk is functioning fine or not

i have been using my laptop after the fall for approx 6-8 hours but didn't saw any error

please recommend i am worried

---

### Post by HankB on 2011-02-15
> **ltoso said:**
> 
i want to know, is there a utility that i can run to check if my hard disk is functioning fine or not

i have been using my laptop after the fall for approx 6-8 hours but didn't saw any error

Yes. ou can examine the SMART information in the hard drive. Install smartmontools through Applications => Ubuntu Software Center or in a terminal window:

```
sudo apt-get install smartmontools
```

And then check drive health with the command:

```
sudo smartctl -a /dev/sda
```

In particular, I monitor reallocated sector count. A few reallocated sectors are not cause for excessive concern, but if that number grows over time, better find a replacement drive! There are some other statistics that may look alarmingly large but don't seem to indicate a problem. Here is the output from the drive on my laptop (with reallocated sector count highlighted):
```
hbarta@cypress:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000BEVT-22ZAT0
Serial Number:    (removed)
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Feb 15 07:37:26 2011 CST
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
data collection: 		 (12780) seconds.
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
recommended polling time: 	 ( 149) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0027   185   182   021    Pre-fail  Always       -       1725
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4167
**[COLOR="Red"]  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0[/COLOR]**
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       14178
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       181
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       37
193 Load_Cycle_Count        0x0032   194   194   000    Old_age   Always       -       19447
194 Temperature_Celsius     0x0022   108   099   000    Old_age   Always       -       39
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

hbarta@cypress:~$ 

```

The SMART information may also list errors that the drive has encountered during previous operation.

Good luck!

-hank

---

### Post by ltoso on 2011-02-15
Thanx Hank for fast reply,
Is there some graphical disk checking tool in ubuntu

Please recommend

---

### Post by rg4w on 2011-02-15
> **ltoso said:**
> Thanx Hank for fast reply,
Is there some graphical disk checking tool in ubuntu

Please recommend
I've been able to find disk errors easily using the Disk Utility that comes with Ubuntu - see System->Administration.

---

### Post by HankB on 2011-02-15
> **ltoso said:**
> 
Is there some graphical disk checking tool in ubuntu

If you go to Ubuntu Software Center and type smartmontools in the search box, the second selection listed is a graphical front end to the smartmontools command line utility.

As rg4w mentioned, System => Administration => Disk Utility also shows SMART drive information. (That's something I didn't know about and now I understand why smartmontools are not installed by default.)

---

### Post by ltoso on 2011-02-15
Hi,
disk utility is definately better tool than smartmontools, is the disk utility independent of the graphical front end of smartmontool, as i installed the both cli and smartmontools gui, but the application launcher for smartmontools wasn't available in any of the menus,


thanx for the info rg4w

---

### Post by HankB on 2011-02-15
Glad to see you got the information you need. The GUI for smartmontools should be found in Applications => System Tools => GSmartControl

BTW, "better" is a value judgment and may depend on needs. I like the CLI version of smartmontools because I can script it to scan drives periodically, select the results that interest me and email a summary to me. It's nice to have choices to meet different preferences.

---

### Post by ltoso on 2011-02-15
> 
BTW, "better" is a value judgment and may depend on needs. I like the  CLI version of smartmontools because I can script it to scan drives  periodically, select the results that interest me and email a summary to  me. It's nice to have choices to meet different preferences. 	


you are right if you want to monitor multiple systems hard disk using CLI, then something like smartmontools-cli is invaluable

> Applications => System Tools => GSmartControl

no link is appearing in my Applications => System Tools as GSmartControl

do you think it can get to some other folder.

Thanx for prompt replies

---

### Post by HankB on 2011-02-15
> **ltoso said:**
> 
no link is appearing in my Applications => System Tools as GSmartControl

do you think it can get to some other folder.
I'm never quite sure why some GUI commands do not get added to the main menu. When that happens, I usually find the command in the list of package files:```
hbarta@cypress:~$ dpkg -L gsmartcontrol|grep bin
/usr/bin
/usr/bin/gsmartcontrol
/usr/bin/gsmartcontrol-root
hbarta@cypress:~$
``` Then I run the command from a terminal. In this case, neither command works the same as the one in the menu so I inspected the menu properties and found the actual command that gets run is:
```
su-to-root -X -c gsmartcontrol
```

Sorry I cannot provide a better answer and I'm only too happy to be able to help. I know how disappointing it can be to post a question that goes unanswered.

BTW, is your drive OK?

---

### Post by fjgaude on 2011-02-15
> **ltoso said:**
> you are right if you want to monitor multiple systems hard disk using CLI, then something like smartmontools-cli is invaluable

no link is appearing in my Applications => System Tools as GSmartControl

do you think it can get to some other folder.

Thanx for prompt replies

Simply install it from the Ubuntu Software Center after doing a search for it.

---

