---
title: "Harddisk not working"
date: 2015-03-09
forum: Hardware
---

### Post by Freestyle Skater on 2015-03-09
I have a server running ubuntu server 14.04. It has an internal drive and then 7 (6 + spare) other harddrives in an external RAID eSata enclosure. I'm using mdadm to run RAID10. The server experienced power failure after the UPS died, but the RAID enclosure was on a separate UPS and did not go out. When I turned back on the server, one of the drives would not load. /dev/sdd was there, but there was no /dev/sdd1. I synced the spare so my RAID is fine, but I'd like to understand what happened a bit better.

Here's fdisk -l. The partition table appears fine.

```
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d7254

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953525167   976761560   fd  Linux raid autodetect

```

smartctl -a shows that it's working fine.

mdadm -E /dev/sdd
```
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   1953523120 sectors at         2048 (type fd)
```

I'm just out of ideas for what to check for why it's not loading /dev/sdd1, and I'd like to understand this a bit better in case it happens again. Thanks.

---

### Post by tgalati4 on 2015-03-09
Post the SMART parameters.  Were there any errors captured near the bottom?

Then check the server logs, although chances are with a sudden power loss, nothing will get captured.

You were lucky to have 2 UPS's--one which saved your data! (Was that by design or did you run out of outlets?)  But you have also demonstrated that power loss can mess up your system.  I would use one UPS with a more rigorous test and battery maintenance program.  How long did your first UPS stay up before it lost power?  Was the battery so bad that it couldn't even perform the switchover?

My first inclination as to why it is not loading /dev/ssd1 is that the striping got messed up on the drive because the power failure occured during a write operation.  It must have been a serious enough failure (and most power outages are) that the striping got hopelessly messed up.

I don't know of any tool that could have repaired this RAID10 in-place.

RAID10 can handle a lot of failure scenarios.  Except the one you experienced.

---

### Post by Freestyle Skater on 2015-03-09
Thanks tgalati4 for your help. The smart output you requested is below. The UPS design was something that someone else had setup, and I had just, stupidly, not tested them. My best guess for what happened is that we just had a power flicker since we experience intermittent brownouts here and the server was off when I came in on Monday, plus the UPS it was connected to shows the battery needs replaced. The syslogs are all fine, right up until they stop logging hourly chron jobs.

If it's just the power loss that messed it up, I'll keep it as a hot spare after zeroing it out and then be more vigilant about maintaining my UPSs.

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-46-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD10EFRX-68PJCN0
Serial Number:    WD-WCC4J4512247
LU WWN Device Id: 5 0014ee 2b4e679af
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Mar  9 13:08:57 2015 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (13920) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 158) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   137   136   021    Pre-fail  Always       -       4150
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       14
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1265
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       13
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       159
194 Temperature_Celsius     0x0022   122   113   000    Old_age   Always       -       21
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

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

---

### Post by Freestyle Skater on 2015-03-09
I just wanted to say thanks again. I went ahead and installed apcupsd, and I now have my server set to monitor the UPS and shut down gracefully if anything like this happens again. I'm feeling much better about my server after the headache this morning.

---

