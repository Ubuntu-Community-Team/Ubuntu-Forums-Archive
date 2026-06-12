---
title: "rsync to USB-connected drive &quot;hangs&quot;"
date: 2016-03-05
forum: Hardware
---

### Post by kazz2 on 2016-03-05
I've recently built an Ubuntu Server 14.04.4 LTS server on an MSI H67MA-E35 motherboard. This was after aborting my first build on other hardware in order to avoid the hassle of 3rd-party drivers and parts. The MSI motherboard was the foundation for a Windows Home Server that's been running for years, backing up to a Seagate, USB3 5TB hard drive. Before I abandoned the other Ubuntu Server build I purchased a second 5TB drive just like the first and a 3rd-party USB adapter for backups. It was able to rsync what I needed to it (3.2TB) in that build just fine. And the crontab backup job seemed to be working fine.

On this new build, I didn't need the 3rd party USB adapter since the motherboard had one built in. I had created a RAIDZ on the original build and when moving it to the new build forgot to import at and created it - dumb me. But I had the backup. So I started a restore (rsync). That "hung" at one point - I'd left it to restore overnight. I tried to do a sudo shutdown -P now but it hung midway through the shutdown process. I had to resort to the power button.

I did some poking through dmesg and syslog and noticed ACPI errors, did some research, tried to change settings in the BIOS to minimize them. I also moved the external backup to the second USB3 port in an effort to eliminate that as a possibility as well. I then resumed the restore via rsync. That completed, having moved much more data than the previous failed restore. I basically finished shares, permissions, etc. and setup the sudo crontab -e rsync job, logging with tree, to occur daily at 2:30am.

Checking this morning I saw the log didn't finish. I noticed the external drive's light was flashing. And trying a shutdown resulted in another hang. I shut the system down with the power button, moved the external drive to a USB2 port, and restarted the system.

At this point, I'd like to try to discover whether there is some conflict occurring or if the problem resides outside the server (USB cable or external drive). Below are starting points. I'd greatly appreciate any assistance in narrowing this down!

((I've tried three times to post this thread. I believe the logs I included were too long so I've pastebin'd and linked))

dmesg: [http://paste.ubuntu.com/15295203/](http://paste.ubuntu.com/15295203/)

syslog.1 (2:30am backup appears here): [http://paste.ubuntu.com/15295272/](http://paste.ubuntu.com/15295272/)

syslog: [http://paste.ubuntu.com/15295250/](http://paste.ubuntu.com/15295250/)

Thanks!

---

### Post by weatherman2 on 2016-03-05
First of all, check your hard drive health of each hard drive involved (the original and the backup drive) using GSmartControl, if you haven't already.  Just make sure there aren't any S.M.A.R.T. issues.  Rule that out.  The key thing is to look at the Attributes of each drive and also make sure each drive passes the "short" S.M.A.R.T. test.

Beyond that - it sounds like you were able to restore via USB2 right?  If so, see if you can do a reliable nightly backup with USB2 for a night or two.  If that turns out to be reliable, then it's likely an issue with the USB3 driver on the built-in port.  In that case, you can poke around and figure out the issue specifically related to that.   Or it might be easier (if annoying) to plug your old USB3 adapter (PCI-E?) if that worked before.

Lately, I've been using eSata for connecting my internal drives externally using a USB dock I have that also has an eSata port.  I got an adapter to connect eSata to one of my motherboard's SATA connectors and add an eSata connector on the back.  My MSI motherboard supports hot swapping of eSATA drives and that has been working very reliably for me.  I have had a few random issues with USB3 myself but don't rely on a USB3 drive for nightly backup.  I'm also only using Ubuntu 14.04.1 on this particular server.

---

### Post by kazz2 on 2016-03-05
Thanks for the reply. I do have it now plugged into a USB2 port and will see how it runs overnight tonight. I was able to back up to it with the previous hardware thought a 3rd party USB port.

Thanks for your suggestion, however, I'm on server not workstation and don't have any gui installed nor am I looking to do so. smartmontools is recommended for checking SMART issues. But when I run sudo smartctl -i /dev/sdf I receive the following:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


/dev/sdf: Unknown USB bridge [0x0bc2:0x3322 (0x100)]
Please specify device type with the -d option.


Use smartctl -h to get a usage summary

```

and the -d parameter is documented in help as:

```

 -d TYPE, --device=TYPE
         Specify device type to one of: ata, scsi, sat[,auto][,N][+TYPE], usbcypress[,X], usbjmicron[,p][,x][,N], usbsunplus, marvell, areca,N/E, 3ware,N, hpt,L /M/N, megaraid,N, cciss,N, auto, test

```

I'm afraid I don't know which type to specify. An lsusb simply states:

```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bc2:3322 Seagate RSS LLC
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Can someone help me complete the appropriate smartctl command?

Thank you!

---

### Post by kazz2 on 2016-03-05
Found some answers. Passed a short test, started a long test. Won't know the results before tomorrow morning, apparently. Imagine that'll screw up the backup cron. LOL Oh well.

I found this link for determining smartctl type (-t) parameters: [https://www.smartmontools.org/wiki/Supported_USB-Devices](https://www.smartmontools.org/wiki/Supported_USB-Devices)

I made an educated guess and used -d sat and that worked.

---

### Post by weatherman2 on 2016-03-05
Right, -d sat is what I was going to recommend.  I've been using that forever on older versions of SmartMonTools but had hoped the newer versions would be smart enough (so to speak) - guess not!

What about the S.M.A.R.T. Attributes?  Could be you won't be able to retrieve that data now that you are running the long test, but those are as important if not more important than the long test in my opinion.  (Make sure RAW value of Pending Sector Count is 0; others may depend on type of drive, Read error rate can be important but on some drives it is meaningless.)  Good to run the long test anyway, though.

Running the long test should not interfere with the backup - may slow it down a little at worst.

I suspect if you passed the short test that the drive is probably OK.

Assuming the drive is OK, as I said, my next step would probably be using the USB2 port for a few days, then plugging in your PCI-E USB 3 card if you still have it and try that for a few days...and if that works, then dig into which USB3 chipset you have on the motherboard and what the potential issues are for it, if you want to use the motherboard's built in USB3 port.

---

### Post by kazz2 on 2016-03-05
Thanks. Since the add-in USB3 adapter doesn't require it's own driver, I'm willing to use it if necessary, short or long term.

Interesting results so far, however.

This was just a couple of minutes after I started it:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Self-test routine in progress 90%       292         -
# 2  Short offline       Completed without error       00%       292         -

```

This I just ran, somewhere around an hour later:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       80%       294         2066680224
# 2  Short offline       Completed without error       00%       292         -

```

I would say the drive's toasty. I'll contact the mfr.

---

### Post by weatherman2 on 2016-03-05
Again - S.M.A.R.T. Attributes?

```

sudo smartctl -A /dev/sdf
sudo smartctl -A /dev/sdf | grep -i sector

```

---

### Post by kazz2 on 2016-03-05
Ooops, sorry. Cooking dinner for five here. LOL

sudo smartctl -A /dev/sdf -d sat

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       9923912
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       21
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       15725010
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       294
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       21
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   061   045    Old_age   Always       -       30 (Min/Max 30/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       90
194 Temperature_Celsius     0x0022   030   040   000    Old_age   Always       -       30 (0 18 0 0 0)
195 Hardware_ECC_Recovered  0x001a   119   100   000    Old_age   Always       -       9923912
197 Current_Pending_Sector  0x0012   098   098   000    Old_age   Always       -       944
198 Offline_Uncorrectable   0x0010   098   098   000    Old_age   Offline      -       944
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       177953379975327
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       10045947563
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       7023540663

```

sudo smartctl -A /dev/sdf -d sat | grep -i sector

```

   5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   098   098   000    Old_age   Always       -       944

```

---

### Post by weatherman2 on 2016-03-05
Oh, that drive has 944 bad sectors.  Toast.  You're lucky if you can get it replaced under warranty.  I hope you don't need anything off of that drive - good thing it's just a backup?  I'd expect a lot of corrupted files.  

I now monitor S.M.A.R.T. nightly on the important hard drives  my servers and email me whenever there is a change in one of those attributes.  Obviously your backup drive isn't very useful if you can't recover from it.

Good luck!

---

### Post by kazz2 on 2016-03-05
I have everything on one other format. I'm curious why you think I'd be fortunate to have the mfr replace it. I purchased it in February.

I do need to look into monitoring. This whole move to Ubuntu Server's been fraught with no fun. But I'll get it there.

I really do appreciate your help!

---

### Post by weatherman2 on 2016-03-05
I didn't really look at the age - now I see it has only 294 hours on it.  New drives can fail, but I guess I just assumed the drive was older than that from the other things you were talking about!  Of course, if the drive is under warranty (1-3 years or whatever it is), you should have no issue getting it replaced.  I would personally wipe it first (zero it out with dd, maybe) before sending it back, if you care about the data that's on there at all.

FYI, whenever I get a new drive, I always run an extended S.M.A.R.T. test on it before I use it for anything important.

Seagate drives sure are getting a bad reputation lately!  But drives from all manufacturers certainly fail, too!

---

### Post by kazz2 on 2016-03-06
Purchased through Amazon. Amazon's sending me a new one. I have to return the old one w/in 30 days. Amazon pays for shipping.

Lotsa work, frustration, and time, but there's a shining moment of good!

Currently using a Windows file synching program I've used for years to check all files on the Ubuntu Server for accuracy. Then I'll double-check the older 5TB drive and, if good, wipe it, connect it to the Ubuntu Server, and run backup. I sill have the old servers hard drives as my ultimate backup. I think I'm making progress! LOL

---

### Post by weatherman2 on 2016-03-06
Great deal with Amazon.  With NewEgg, you have to send your old drive back first then wait for a new one.  Kind of leaves you without a drive you might be relying on...

I have gone through similar things to this several times over the years.  I have always learned from each experience, at least!  I still have episodes like this, but I don't seem to lose data anymore, which is the most important thing.

---

### Post by kazz2 on 2016-03-06
So far, the important files are fine on the server's RAID. Taking forever to get through the movie files for plex, though. 2.2TB via USB2. Ugh.

Thanks again for all your help!

---

### Post by kazz2 on 2016-03-06
S.M.A.R.T attributes of older Seagate 5TB hard drive that's been backing up the older servers:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   142   142   021    Pre-fail  Always       -       3858
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       98
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1592
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       93
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       45
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       52
194 Temperature_Celsius     0x0022   114   108   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```

Running a long test now...

---

### Post by weatherman2 on 2016-03-06
All of those attributes look OK.  No pending sectors, no reallocated sectors, read error rate is 0.  Many old drives experience some failed sectors over time, but these should not be catastrophic; modern drives have some spare sectors to replace the failed sectors.  These are "reallocated" - so the bad sectors are marked "do not use" by the drive firmware and spares are reallocated to replace them.  If you have a few reallocated sectors on an older drive that's probably OK if the number doesn't go up quickly.  A "pending" sector is one that can't be read at all and thus replaced.

---

### Post by kazz2 on 2016-03-09
It took a couple of days to get all of the data to the replacement drive as it's first official backup. And afterwards I thought I'd run the long version of the SMART test:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST5000DM000-1FK178
Serial Number:    W4J14N33
LU WWN Device Id: 5 000c50 08fd74f81
Firmware Version: CC49
User Capacity:    5,000,981,078,016 bytes [5.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5980 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Mar  9 08:12:38 2016 CST
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
data collection: 		(   96) seconds.
Offline data collection
capabilities: 			 (0x73) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
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
recommended polling time: 	 ( 615) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   100   006    Pre-fail  Always       -       153790848
  3 Spin_Up_Time            0x0003   093   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       7
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   069   060   030    Pre-fail  Always       -       10030970
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       41
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       7
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   054   045    Old_age   Always       -       30 (Min/Max 30/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       15
194 Temperature_Celsius     0x0022   030   046   000    Old_age   Always       -       30 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   117   100   000    Old_age   Always       -       153790848
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       248858995064868
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       6977149179
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2578935

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        35         -
# 2  Short offline       Completed without error       00%         5         -

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

