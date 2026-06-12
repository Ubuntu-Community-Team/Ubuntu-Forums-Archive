---
title: "trouble getting smart status for external hdd"
date: 2022-07-09
forum: Hardware
---

### Post by coley9225 on 2022-07-09
Hello again everyone,
I recently noticed a problem during reboot/shutdown. It seems to take an abnormally long time to shutdown(or shutdown half of reboot). Start up is as fast as ever. I don't use quiet-splash, so I can see what it is doing. It appears to be having trouble unmounting  partitions on my external drive. I decided to check the smart status of the drive, but I'm unable to do so.
I ran the following commands I found doing a search for the proccess.
```
charles:$ !136sudo smartctl -i /dev/sdb
[sudo] password for charles: 
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


Read Device Identity failed: scsi error unsupported field in scsi command


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
charles:$ !139
sudo smartctl -d sat --all /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


Read Device Identity failed: scsi error unsupported field in scsi command


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
charles:$ !140
sudo smartctl -d sat,12 --all /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


Read Device Identity failed: scsi error unsupported field in scsi command


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
charles:$ 



```

I also ran lsusb to see the actual info on the drive, if that will help.
```
harles:$ lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0821 Realtek Semiconductor Corp. Bluetooth Radio 
Bus 001 Device 005: ID 5986:1127 Acer, Inc EasyCamera
Bus 001 Device 008: ID 25a7:fa67 GenesysLogic USB2.0 Hub
Bus 001 Device 009: ID 04a9:18a2 Canon, Inc. USB2.0 HUB
[COLOR=#ff0000]*Bus 001 Device 006: ID 0bc2:ab24 Seagate RSS LLC Backup Plus Portable Drive*[/COLOR]
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 004: ID 214b:7250 GenesysLogic USB2.0 Hub
Bus 001 Device 002: ID 214b:7250  USB2.0 HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
charles:$ 



```

The troubled drive is the Seagate.

My concern is that drive is beginning to die, which would be catastrophic, as that holds all my backups. Any idea how I can get the smart output, or anything you can think of to check why the difficulty unmounting the partitions?

If I need to buy a new backup drive, I would prefer to do so prior to a total failure of this one. Any help is greatly appreciated.

Currently using lubuntu 20.04 with all updates.

---

### Post by #&amp;thj^% on 2022-07-09
Did you ever try with:
```
sudo smartctl -T permissive /dev/sdb
```
That would at least show "ATA device successfully opened"

---

### Post by coley9225 on 2022-07-09
Thanks 1fallen.
I ran the suggested command.
```
charles:$ sudo smartctl -T permissive /dev/sdbsmartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


ATA device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information
```

So I tried this command.
```
sudo smartctl -aT permissive /dev/sdbsmartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


Read Device Identity failed: scsi error unsupported field in scsi command


=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
Local Time is:    Sat Jul  9 13:58:07 2022 EDT
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
charles:$ 



```

I do remember reading that it may be an issue with the sata to usb controller inside the drive, but never saw anything to suggest a fix or work around.

---

### Post by #&amp;thj^% on 2022-07-09
That sucks, some seagates just don't come with decent control board.
I was lucky with mine:
```
smartctl -d sat --all /dev/sda
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.18.9-zen1-1-zen] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Pro Compute
Device Model:     ST1000LM049-2GH172
Serial Number:    WN9221M7
LU WWN Device Id: 5 000c50 0cfb7bdab
Firmware Version: LXM4
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      2.5 inches
TRIM Command:     Available
Device is:        In smartctl database 7.3/5319
ATA Version is:   ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Jul  9 11:41:06 2022 MDT
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
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x71) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 124) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   079   064   034    Pre-fail  Always       -       71637471
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       802
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   067   060   045    Pre-fail  Always       -       4635177
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2944 (244 183 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       512
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       2
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   052   040    Old_age   Always       -       37 (Min/Max 34/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       50
193 Load_Cycle_Count        0x0032   093   093   000    Old_age   Always       -       14262
194 Temperature_Celsius     0x0022   037   048   000    Old_age   Always       -       37 (0 17 0 0 0)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x000f   099   099   030    Pre-fail  Always       -       1386 (122 232 0)
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Vendor (0x50)       Completed without error       00%      2812         -
# 2  Short offline       Completed without error       00%      2812         -

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
But if it's directly connected inside your machine with a Powered sata to usb controller it should work.
is your sata to usb controller powered or just USB connected?

---

### Post by coley9225 on 2022-07-09
The drive is an external 2T, connected to a usb(non-powered) hub. I have an enclosure, and just ran tests on on 2 different drives. The results are similar to yours. Maybe, to err on the side of caution, I'l use ddrescue and clone the 2 most important partitions(timeshift partition and back in time partition), and order a new drive for my backups. At that point I can clone this drive to the new, or just start with new backups. Of course, I could get really nuts and break open the hard drives case and move it to my enclosure and try that(after cloning of coarse).
If you can think of anything else I can try, just let me know,

---

### Post by #&amp;thj^% on 2022-07-09
> **coley9225 said:**
> The drive is an external 2T, connected to a usb(non-powered) hub. 

That's the deal breaker>>non-powered.
> **coley9225 said:**
>  Maybe, to err on the side of caution, I'l use ddrescue and clone the 2 most important partitions(timeshift partition and back in time partition), 
That's always a wise choice.
> **coley9225 said:**
> 
If you can think of anything else I can try, just let me know,
None I can think of, without it being powered. BUT: I would not open the enclosure just to check...I know your just throwing that out there. ;)
maybe after the successful back-ups, you then could go crazy with it. :D

---

### Post by coley9225 on 2022-07-09
Thanks for the assist. I'll get this thing cloned soon and order a new back up drive, maybe I'll splurge for a ssd this time.

[IMG]https://ubuntuforums.org/images/icons/icon11.png[/IMG] Of coarse no breaking into the case before properly cloned, or new back up drive in place.

---

