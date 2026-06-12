---
title: "Corsair Neutron XT SSD: &quot;Disk is likely to fail soon&quot;"
date: 2016-02-28
forum: Hardware
---

### Post by Mr Fredrick on 2016-02-28
Hi All,

About 6 months ago I purchased a 408GB Corsair Neutron XT SSD. A few days ago I attempted to save some work using Netbeans to disk but when I checked the work the next morning I found that it has not been saved. When I checked the drive using the Disks utility it showed the following message: "Disk likely to fail soon". After much hair pulling I later I notice that GParted reports that one of my partitions sda5 "lvm2 pv" is completely full at 446.85GB. This struck me as unusual since my previous non SSD 300GB drive never managed to even get half full after years of use. I'm hoping that the full partition accounts for the error message and that if I can reduce the data in the partition then that will hopefully solve the problem.

However I have attempted to run fstrim or blkdiscard on the partition multiple times but nothing works. I get:

blkdiscard: /dev/sda5: BLKDISCARD ioctl failed: Input/output error

so some such.

I'm running Ubuntu 15.10

Any advice welcome, thanks in advance.

Mr Fred.

---

### Post by weatherman2 on 2016-02-28
A full partition won't cause a "Disk likely to fail soon" message.  That sounds like a S.M.A.R.T. message.  It sounds like your SSD is failing.  You could check the S.M.A.R.T. Attributes - I like GSmartControl, but I would do all of this from a live USB boot of Ubuntu and stop using this SSD immediately for anything until you have copied any remaining data you do not have backed up elsewhere.    You can install GSmartControl in a live USB (or live DVD or whatever) session of Ubuntu by first enabling the "universe" repository in Ubuntu Software Center, then installing it.  I would assume the SSD is about to fail and you will soon be unable to get any data off of it again.

SSDs can certainly fail too.  Backups are important for all types of devices.

---

### Post by Mr Fredrick on 2016-02-28
Thanks for the reply.

I'm now running from a bootable USB on which I installed the package you suggested and below are the results, doesn't look good:

```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     Corsair Neutron XT SSD
Serial Number:    145181920001025900A0
Firmware Version: SAFC01.1
User Capacity:    480,103,981,056 bytes [480 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Feb 28 23:55:11 2016 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
No failed Attributes found.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   30) seconds.
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
recommended polling time: 	 (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0013   100   100   050    Pre-fail  Always       -       1
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       2686
 12 Power_Cycle_Count       0x0012   100   100   000    Old_age   Always       -       644
162 Unknown_Attribute       0x0003   099   099   000    Pre-fail  Always       -       4294969139
170 Unknown_Attribute       0x0002   100   100   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       196625
174 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       138
181 Program_Fail_Cnt_Total  0x0012   100   100   000    Old_age   Always       -       1
187 Reported_Uncorrect      0x0012   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0012   100   100   000    Old_age   Always       -       138
194 Temperature_Celsius     0x0023   070   070   030    Pre-fail  Always       -       30 (Min/Max 29/30)
196 Reallocated_Event_Count 0x0002   100   100   010    Old_age   Always       -       1
218 Unknown_Attribute       0x000b   100   100   050    Pre-fail  Always       -       0
231 Temperature_Celsius     0x0013   100   100   000    Pre-fail  Always       -       100
241 Total_LBAs_Written      0x0012   100   100   000    Old_age   Always       -       801
242 Total_LBAs_Read         0x0012   100   100   000    Old_age   Always       -       717

Read SMART Log Directory failed: scsi error aborted command

Read SMART Error Log failed: scsi error aborted command

Read SMART Self-test Log failed: scsi error aborted command

Read SMART Selective Self-test Log failed: scsi error aborted command
```

I've only had this drive a few months, so I very disappointed. I would be good to know if others have had problems with this SSD.

---

### Post by weatherman2 on 2016-02-28
I don't know what some of those unkonwn attributes mean - Corsair must have some vendor-specific use for them.  I'm not sure what #162 is.  #173 is "wear-leveling" but that one might be normal.

Still, the messages:

```

SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.

```

look dire.  As I said above - backup what you can then RMA under warranty.

All devices can fail.  Corsair isn't exactly known as the most reliable name in SSDs - (those are probably Intel, Crucial, and Samsung).  You can dig up reviews of that model and see how often people experience failures like yours.

---

