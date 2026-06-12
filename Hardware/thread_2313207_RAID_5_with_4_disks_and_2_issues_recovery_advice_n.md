---
title: "RAID 5 with 4 disks and 2 issues recovery advice needed"
date: 2016-02-10
forum: Hardware
---

### Post by redirect on 2016-02-10
Hi All,

First let me say that I know I made an error in not adding further redundancy to my setup, its an incredibly valuable lesson learned.

I am running a Raid 5 system with 4 drives and encountered 2 issues.  

After a power outage my array failed to start up in degraded mode.  The error I got was:

```
Error starting RAID array: Command-line `mdadm --assemble  --scan --uuid "16f9df9a:c90b8161:ca66c3a1:f2e4c2cd"' exited with non-zero exit status 2:  (udisks-error-quark, 0)
```

I found that /dev/sdc fails self-test so I think this is the faulty drive but this doesn't explain why the array didn't start up in degraded mode.  After some researching I tried to assemble the array to see if I get any errors.  This is what I got:

> sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted

My intention was to recreate the array /dev/md0/ with this command to fix the "no superblock" issue:

[COLOR=#000000][FONT=verdana]mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 missing /dev/sdc1 /dev/sdd1 /dev/sde1

[/FONT][/COLOR]Next I was going to replace /dev/sdc1 and add it to the array.  

At this point I am unsure how I can proceed without losing my data and given it contains all my childrens pictures of them growing up, I would be devastated to lose them.  I am looking for some advice.  If someone could please provide some guidance I would greatly appreciate it.  

Cheers

---

### Post by rubylaser on 2016-02-16
Did you already run the --create --assume-clean command (--create should be the absolute last thing you try).  If, not, please don't do that yet.  Your previous attempt at --assemble did not use the partitions /dev/sde**1**, but instead used the device.

It would be nice to see the metadata for the disks.
```

mdadm -E /dev/sd[bcde]1

```

and the smart data for sdc
```

smartctl -a /dev/sdc

```

You could try the assemble again with the proper disk partitions.
```

sudo -i
mdadm --stop /dev/md0
mdadm --assemble /dev/sd[bcde]1

```

If that fails, try it without /dev/sdc1
```

mdadm --assemble /dev/sd[bde]1

```

If this doesn't work, try it with the --force option.
```

mdadm --assemble --force /dev/sd[bde]1

```
 
Let us know how that goes.

---

### Post by redirect on 2016-02-16
rubylaser,

Thank you so much for your attention to this.  I have not proceeded with any commands aside from what I indicate in my first post.  I am currently at work but when I get home tonight I will try your suggestions.  

Do you think that the "no superblock" issue was due to not specifying the partition? 
Why do you think the Array did not start up in degraded mode?  I was thinking it should have considering I had 3 of 4 drives in working condition.

Thank you again for your time and I will report back with the results of your suggestion.

Cheers,

Dave

---

### Post by redirect on 2016-02-16
Hey rubylaser,

Below is the output of the first two commands.  Stepping away to feed the rugrats and will attempt the reassemble after that.

Dave

Disk metadata:

```
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 16f9df9a:c90b8161:ca66c3a1:f2e4c2cd
  Creation Time : Sun Aug  1 22:09:22 2010
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0


    Update Time : Sun Sep 27 03:23:58 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5f7331c - correct
         Events : 2437


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1


   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       49        3      active sync   /dev/sdd1

``````
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 16f9df9a:c90b8161:ca66c3a1:f2e4c2cd
  Creation Time : Sun Aug  1 22:09:22 2010
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0


    Update Time : Sat Dec 19 03:17:01 2015
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 664bae5 - correct
         Events : 4348


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1


   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       49        3      active sync   /dev/sdd1

```
```
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 16f9df9a:c90b8161:ca66c3a1:f2e4c2cd
  Creation Time : Sun Aug  1 22:09:22 2010
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0


    Update Time : Sat Dec 19 12:18:58 2015
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 66528e1 - correct
         Events : 4359


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1


   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed

```
```
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 16f9df9a:c90b8161:ca66c3a1:f2e4c2cd
  Creation Time : Sun Aug  1 22:09:22 2010
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0


    Update Time : Sat Dec 19 12:18:58 2015
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 665290f - correct
         Events : 4359


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     1       8       65        1      active sync   /dev/sde1


   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed

```
Smart data:

```
smartctl -a /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA)
Device Model:     WDC WD5000AAKS-00V1A0
Serial Number:    WD-WCAWF1359253
LU WWN Device Id: 5 0014ee 1ad0542ec
Firmware Version: 05.01D05
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Tue Feb 16 17:42:45 2016 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		( 8160) seconds.
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
recommended polling time: 	 (  97) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       84
  3 Spin_Up_Time            0x0027   137   135   021    Pre-fail  Always       -       4133
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       124
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   048   048   000    Old_age   Always       -       38098
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       114
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       93
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   095   082   000    Old_age   Always       -       48
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   001   001   000    Old_age   Always       -       42600
198 Offline_Uncorrectable   0x0030   188   188   000    Old_age   Offline      -       1023
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   195   195   000    Old_age   Offline      -       1027


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     37589         546448952
# 2  Extended offline    Completed: read failure       90%     37046         546448952
# 3  Short offline       Completed: read failure       90%     37006         546448952


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay
```.

---

### Post by redirect on 2016-02-16
Ok I tried to assemble and here is what I got in return:

```
root@Ubuntu-Server:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Ubuntu-Server:~# mdadm --assemble /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble --force /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.

```

Should I be using this instead?

```
mdadm **/dev/md0** --assemble /dev/sd[bcde]1
```

---

### Post by rubylaser on 2016-02-17
> **redirect said:**
> Ok I tried to assemble and here is what I got in return:

```
root@Ubuntu-Server:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Ubuntu-Server:~# mdadm --assemble /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.
root@Ubuntu-Server:~# mdadm --assemble --force /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.

```

Should I be using this instead?

```
mdadm **/dev/md0** --assemble /dev/sd[bcde]1
```

Yes, you should add /dev/md0, sorry, I typed that on my phone yesterday :)  Also, /dev/sdc has errors, but they appear to be the result of UDMA errors which is normally the result of a bad SATA cable, or connection.  I'd turn off your machine, and swap the cable on that drive with a new one.  I'd be surprised if that disk isn't salvageable. Also, your event counter for /dev/sdb1 is half of what the other disks are.  That's what looks like actually caused the issue.  You appear to have been running degraded for a very long time.  I would try to fix the SATA cable on the current /dev/sdc, and then try to assemble the array with the current /dev/sd[cde]1.  You will want to write down the serial number of each disk to ensure that after a reboot, you are trying to assemble with the correct disks. Let me know how the assemble goes (you will probably need to use the --force flag to assemble. If this works, you will end up with a degraded array, but you should be able to read your data (back it up first before doing anything else).

---

### Post by redirect on 2016-02-17
Hey rubylaser,

So things aren't going as well as I had hoped.  First let me say that I changed the cable out and the drive letters changed as I recorded each drives serial # and put them back (not in the same order).  I noticed the drive letter change before I forced an assemble so I took that into account and the array came up in degraded mode but many of the files were not accessible.  Then system froze so I waited 45min(ish)rebooted and the array is not coming back up now.

Here is some output:



```
[FONT=courier new]
[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm --examine /dev/sdb1[/FONT]
[FONT=courier new]/dev/sdb1:[/FONT]
[FONT=courier new]          Magic : a92b4efc[/FONT]
[FONT=courier new]        Version : 0.90.00[/FONT]
[FONT=courier new]           UUID : 16f9df9a:c90b8161:ca66c3a1:f2e4c2cd[/FONT]
[FONT=courier new]  Creation Time : Sun Aug  1 22:09:22 2010[/FONT]
[FONT=courier new]     Raid Level : raid5[/FONT]
[FONT=courier new]  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)[/FONT]
[FONT=courier new]     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)[/FONT]
[FONT=courier new]   Raid Devices : 4[/FONT]
[FONT=courier new]  Total Devices : 3[/FONT]
[FONT=courier new]Preferred Minor : 0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    Update Time : Sat Dec 19 12:18:58 2015[/FONT]
[FONT=courier new]          State : clean[/FONT]
[FONT=courier new] Active Devices : 2[/FONT]
[FONT=courier new]Working Devices : 2[/FONT]
[FONT=courier new] Failed Devices : 1[/FONT]
[FONT=courier new]  Spare Devices : 0[/FONT]
[FONT=courier new]       Checksum : 66529c0 - correct[/FONT]
[FONT=courier new]         Events : 4581[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]         Layout : left-symmetric[/FONT]
[FONT=courier new]     Chunk Size : 64K[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]      Number   Major   Minor   RaidDevice State[/FONT]
[FONT=courier new]this     2       8       17        2      active sync   /dev/sdb1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]   0     0       0        0        0      removed[/FONT]
[FONT=courier new]   1     1       8       65        1      active sync   /dev/sde1[/FONT]
[FONT=courier new]   2     2       8       17        2      active sync   /dev/sdb1[/FONT]
[FONT=courier new]   3     3       0        0        3      faulty removed[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# smartctl -a /dev/sdb1[/FONT]
[FONT=courier new]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)[/FONT]
[FONT=courier new]Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF INFORMATION SECTION ===[/FONT]
[FONT=courier new]Model Family:     Western Digital Caviar Blue (SATA)[/FONT]
[FONT=courier new]Device Model:     WDC WD5000AAKS-00V1A0[/FONT]
[FONT=courier new]Serial Number:    WD-WCAWF1352313[/FONT]
[FONT=courier new]LU WWN Device Id: 5 0014ee 157b6379c[/FONT]
[FONT=courier new]Firmware Version: 05.01D05[/FONT]
[FONT=courier new]User Capacity:    500,107,862,016 bytes [500 GB][/FONT]
[FONT=courier new]Sector Size:      512 bytes logical/physical[/FONT]
[FONT=courier new]Device is:        In smartctl database [for details use: -P show][/FONT]
[FONT=courier new]ATA Version is:   ATA8-ACS (minor revision not indicated)[/FONT]
[FONT=courier new]SATA Version is:  SATA 2.6, 3.0 Gb/s[/FONT]
[FONT=courier new]Local Time is:    Wed Feb 17 11:54:14 2016 EST[/FONT]
[FONT=courier new]SMART support is: Available - device has SMART capability.[/FONT]
[FONT=courier new]SMART support is: Enabled[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF READ SMART DATA SECTION ===[/FONT]
[FONT=courier new]SMART overall-health self-assessment test result: PASSED[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]General SMART Values:[/FONT]
[FONT=courier new]Offline data collection status:  (0x82)    Offline data collection activity[/FONT]
[FONT=courier new]                    was completed without error.[/FONT]
[FONT=courier new]                    Auto Offline Data Collection: Enabled.[/FONT]
[FONT=courier new]Self-test execution status:      (   0)    The previous self-test routine completed[/FONT]
[FONT=courier new]                    without error or no self-test has ever [/FONT]
[FONT=courier new]                    been run.[/FONT]
[FONT=courier new]Total time to complete Offline [/FONT]
[FONT=courier new]data collection:         ( 7800) seconds.[/FONT]
[FONT=courier new]Offline data collection[/FONT]
[FONT=courier new]capabilities:              (0x7b) SMART execute Offline immediate.[/FONT]
[FONT=courier new]                    Auto Offline data collection on/off support.[/FONT]
[FONT=courier new]                    Suspend Offline collection upon new[/FONT]
[FONT=courier new]                    command.[/FONT]
[FONT=courier new]                    Offline surface scan supported.[/FONT]
[FONT=courier new]                    Self-test supported.[/FONT]
[FONT=courier new]                    Conveyance Self-test supported.[/FONT]
[FONT=courier new]                    Selective Self-test supported.[/FONT]
[FONT=courier new]SMART capabilities:            (0x0003)    Saves SMART data before entering[/FONT]
[FONT=courier new]                    power-saving mode.[/FONT]
[FONT=courier new]                    Supports SMART auto save timer.[/FONT]
[FONT=courier new]Error logging capability:        (0x01)    Error logging supported.[/FONT]
[FONT=courier new]                    General Purpose Logging supported.[/FONT]
[FONT=courier new]Short self-test routine [/FONT]
[FONT=courier new]recommended polling time:      (   2) minutes.[/FONT]
[FONT=courier new]Extended self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (  93) minutes.[/FONT]
[FONT=courier new]Conveyance self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (   5) minutes.[/FONT]
[FONT=courier new]SCT capabilities:            (0x303f)    SCT Status supported.[/FONT]
[FONT=courier new]                    SCT Error Recovery Control supported.[/FONT]
[FONT=courier new]                    SCT Feature Control supported.[/FONT]
[FONT=courier new]                    SCT Data Table supported.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Attributes Data Structure revision number: 16[/FONT]
[FONT=courier new]Vendor Specific SMART Attributes with Thresholds:[/FONT]
[FONT=courier new]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE[/FONT]
[FONT=courier new]  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  3 Spin_Up_Time            0x0027   141   140   021    Pre-fail  Always       -       3908[/FONT]
[FONT=courier new]  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       122[/FONT]
[FONT=courier new]  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]  9 Power_On_Hours          0x0032   050   050   000    Old_age   Always       -       37058[/FONT]
[FONT=courier new] 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       120[/FONT]
[FONT=courier new]192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       89[/FONT]
[FONT=courier new]193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       32[/FONT]
[FONT=courier new]194 Temperature_Celsius     0x0022   092   075   000    Old_age   Always       -       51[/FONT]
[FONT=courier new]196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Error Log Version: 1[/FONT]
[FONT=courier new]No Errors Logged[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Self-test log structure revision number 1[/FONT]
[FONT=courier new]Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error[/FONT]
[FONT=courier new]# 1  Short offline       Completed without error       00%     35951         -[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Selective self-test log data structure revision number 1[/FONT]
[FONT=courier new] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT]
[FONT=courier new]    1        0        0  Not_testing[/FONT]
[FONT=courier new]    2        0        0  Not_testing[/FONT]
[FONT=courier new]    3        0        0  Not_testing[/FONT]
[FONT=courier new]    4        0        0  Not_testing[/FONT]
[FONT=courier new]    5        0        0  Not_testing[/FONT]
[FONT=courier new]Selective self-test flags (0x0):[/FONT]
[FONT=courier new]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT]
[FONT=courier new]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# smartctl -a /dev/sdc1[/FONT]
[FONT=courier new]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)[/FONT]
[FONT=courier new]Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF INFORMATION SECTION ===[/FONT]
[FONT=courier new]Model Family:     Western Digital Caviar Blue (SATA)[/FONT]
[FONT=courier new]Device Model:     WDC WD5000AAKS-00V1A0[/FONT]
[FONT=courier new]Serial Number:    WD-WCAWF1359253[/FONT]
[FONT=courier new]LU WWN Device Id: 5 0014ee 1ad0542ec[/FONT]
[FONT=courier new]Firmware Version: 05.01D05[/FONT]
[FONT=courier new]User Capacity:    500,107,862,016 bytes [500 GB][/FONT]
[FONT=courier new]Sector Size:      512 bytes logical/physical[/FONT]
[FONT=courier new]Device is:        In smartctl database [for details use: -P show][/FONT]
[FONT=courier new]ATA Version is:   ATA8-ACS (minor revision not indicated)[/FONT]
[FONT=courier new]SATA Version is:  SATA 2.6, 3.0 Gb/s[/FONT]
[FONT=courier new]Local Time is:    Wed Feb 17 11:54:21 2016 EST[/FONT]
[FONT=courier new]SMART support is: Available - device has SMART capability.[/FONT]
[FONT=courier new]SMART support is: Enabled[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF READ SMART DATA SECTION ===[/FONT]
[FONT=courier new]SMART overall-health self-assessment test result: PASSED[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]General SMART Values:[/FONT]
[FONT=courier new]Offline data collection status:  (0x84)    Offline data collection activity[/FONT]
[FONT=courier new]                    was suspended by an interrupting command from host.[/FONT]
[FONT=courier new]                    Auto Offline Data Collection: Enabled.[/FONT]
[FONT=courier new]Self-test execution status:      (   0)    The previous self-test routine completed[/FONT]
[FONT=courier new]                    without error or no self-test has ever [/FONT]
[FONT=courier new]                    been run.[/FONT]
[FONT=courier new]Total time to complete Offline [/FONT]
[FONT=courier new]data collection:         ( 8160) seconds.[/FONT]
[FONT=courier new]Offline data collection[/FONT]
[FONT=courier new]capabilities:              (0x7b) SMART execute Offline immediate.[/FONT]
[FONT=courier new]                    Auto Offline data collection on/off support.[/FONT]
[FONT=courier new]                    Suspend Offline collection upon new[/FONT]
[FONT=courier new]                    command.[/FONT]
[FONT=courier new]                    Offline surface scan supported.[/FONT]
[FONT=courier new]                    Self-test supported.[/FONT]
[FONT=courier new]                    Conveyance Self-test supported.[/FONT]
[FONT=courier new]                    Selective Self-test supported.[/FONT]
[FONT=courier new]SMART capabilities:            (0x0003)    Saves SMART data before entering[/FONT]
[FONT=courier new]                    power-saving mode.[/FONT]
[FONT=courier new]                    Supports SMART auto save timer.[/FONT]
[FONT=courier new]Error logging capability:        (0x01)    Error logging supported.[/FONT]
[FONT=courier new]                    General Purpose Logging supported.[/FONT]
[FONT=courier new]Short self-test routine [/FONT]
[FONT=courier new]recommended polling time:      (   2) minutes.[/FONT]
[FONT=courier new]Extended self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (  97) minutes.[/FONT]
[FONT=courier new]Conveyance self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (   5) minutes.[/FONT]
[FONT=courier new]SCT capabilities:            (0x303f)    SCT Status supported.[/FONT]
[FONT=courier new]                    SCT Error Recovery Control supported.[/FONT]
[FONT=courier new]                    SCT Feature Control supported.[/FONT]
[FONT=courier new]                    SCT Data Table supported.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Attributes Data Structure revision number: 16[/FONT]
[FONT=courier new]Vendor Specific SMART Attributes with Thresholds:[/FONT]
[FONT=courier new]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE[/FONT]
[FONT=courier new]  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       86[/FONT]
[FONT=courier new]  3 Spin_Up_Time            0x0027   138   135   021    Pre-fail  Always       -       4091[/FONT]
[FONT=courier new]  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       126[/FONT]
[FONT=courier new]  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]  9 Power_On_Hours          0x0032   048   048   000    Old_age   Always       -       38115[/FONT]
[FONT=courier new] 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       116[/FONT]
[FONT=courier new]192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       93[/FONT]
[FONT=courier new]193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       32[/FONT]
[FONT=courier new]194 Temperature_Celsius     0x0022   091   082   000    Old_age   Always       -       52[/FONT]
[FONT=courier new]196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]197 Current_Pending_Sector  0x0032   001   001   000    Old_age   Always       -       44627[/FONT]
[FONT=courier new]198 Offline_Uncorrectable   0x0030   188   188   000    Old_age   Offline      -       1022[/FONT]
[FONT=courier new]199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1[/FONT]
[FONT=courier new]200 Multi_Zone_Error_Rate   0x0008   195   195   000    Old_age   Offline      -       1025[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Error Log Version: 1[/FONT]
[FONT=courier new]No Errors Logged[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Self-test log structure revision number 1[/FONT]
[FONT=courier new]Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error[/FONT]
[FONT=courier new]# 1  Short offline       Completed: read failure       90%     37589         546448952[/FONT]
[FONT=courier new]# 2  Extended offline    Completed: read failure       90%     37046         546448952[/FONT]
[FONT=courier new]# 3  Short offline       Completed: read failure       90%     37006         546448952[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Selective self-test log data structure revision number 1[/FONT]
[FONT=courier new] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT]
[FONT=courier new]    1        0        0  Not_testing[/FONT]
[FONT=courier new]    2        0        0  Not_testing[/FONT]
[FONT=courier new]    3        0        0  Not_testing[/FONT]
[FONT=courier new]    4        0        0  Not_testing[/FONT]
[FONT=courier new]    5        0        0  Not_testing[/FONT]
[FONT=courier new]Selective self-test flags (0x0):[/FONT]
[FONT=courier new]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT]
[FONT=courier new]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# smartctl -a /dev/sdd1[/FONT]
[FONT=courier new]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)[/FONT]
[FONT=courier new]Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF INFORMATION SECTION ===[/FONT]
[FONT=courier new]Model Family:     Western Digital Caviar Blue (SATA)[/FONT]
[FONT=courier new]Device Model:     WDC WD5000AAKS-00V1A0[/FONT]
[FONT=courier new]Serial Number:    WD-WCAWF1418840[/FONT]
[FONT=courier new]LU WWN Device Id: 5 0014ee 1ad054089[/FONT]
[FONT=courier new]Firmware Version: 05.01D05[/FONT]
[FONT=courier new]User Capacity:    500,107,862,016 bytes [500 GB][/FONT]
[FONT=courier new]Sector Size:      512 bytes logical/physical[/FONT]
[FONT=courier new]Device is:        In smartctl database [for details use: -P show][/FONT]
[FONT=courier new]ATA Version is:   ATA8-ACS (minor revision not indicated)[/FONT]
[FONT=courier new]SATA Version is:  SATA 2.6, 3.0 Gb/s[/FONT]
[FONT=courier new]Local Time is:    Wed Feb 17 11:54:25 2016 EST[/FONT]
[FONT=courier new]SMART support is: Available - device has SMART capability.[/FONT]
[FONT=courier new]SMART support is: Enabled[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF READ SMART DATA SECTION ===[/FONT]
[FONT=courier new]SMART overall-health self-assessment test result: PASSED[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]General SMART Values:[/FONT]
[FONT=courier new]Offline data collection status:  (0x82)    Offline data collection activity[/FONT]
[FONT=courier new]                    was completed without error.[/FONT]
[FONT=courier new]                    Auto Offline Data Collection: Enabled.[/FONT]
[FONT=courier new]Self-test execution status:      (   0)    The previous self-test routine completed[/FONT]
[FONT=courier new]                    without error or no self-test has ever [/FONT]
[FONT=courier new]                    been run.[/FONT]
[FONT=courier new]Total time to complete Offline [/FONT]
[FONT=courier new]data collection:         ( 8160) seconds.[/FONT]
[FONT=courier new]Offline data collection[/FONT]
[FONT=courier new]capabilities:              (0x7b) SMART execute Offline immediate.[/FONT]
[FONT=courier new]                    Auto Offline data collection on/off support.[/FONT]
[FONT=courier new]                    Suspend Offline collection upon new[/FONT]
[FONT=courier new]                    command.[/FONT]
[FONT=courier new]                    Offline surface scan supported.[/FONT]
[FONT=courier new]                    Self-test supported.[/FONT]
[FONT=courier new]                    Conveyance Self-test supported.[/FONT]
[FONT=courier new]                    Selective Self-test supported.[/FONT]
[FONT=courier new]SMART capabilities:            (0x0003)    Saves SMART data before entering[/FONT]
[FONT=courier new]                    power-saving mode.[/FONT]
[FONT=courier new]                    Supports SMART auto save timer.[/FONT]
[FONT=courier new]Error logging capability:        (0x01)    Error logging supported.[/FONT]
[FONT=courier new]                    General Purpose Logging supported.[/FONT]
[FONT=courier new]Short self-test routine [/FONT]
[FONT=courier new]recommended polling time:      (   2) minutes.[/FONT]
[FONT=courier new]Extended self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (  97) minutes.[/FONT]
[FONT=courier new]Conveyance self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (   5) minutes.[/FONT]
[FONT=courier new]SCT capabilities:            (0x303f)    SCT Status supported.[/FONT]
[FONT=courier new]                    SCT Error Recovery Control supported.[/FONT]
[FONT=courier new]                    SCT Feature Control supported.[/FONT]
[FONT=courier new]                    SCT Data Table supported.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Attributes Data Structure revision number: 16[/FONT]
[FONT=courier new]Vendor Specific SMART Attributes with Thresholds:[/FONT]
[FONT=courier new]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE[/FONT]
[FONT=courier new]  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  3 Spin_Up_Time            0x0027   141   140   021    Pre-fail  Always       -       3941[/FONT]
[FONT=courier new]  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       125[/FONT]
[FONT=courier new]  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]  9 Power_On_Hours          0x0032   049   049   000    Old_age   Always       -       37270[/FONT]
[FONT=courier new] 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       122[/FONT]
[FONT=courier new]192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       88[/FONT]
[FONT=courier new]193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       36[/FONT]
[FONT=courier new]194 Temperature_Celsius     0x0022   098   082   000    Old_age   Always       -       45[/FONT]
[FONT=courier new]196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Error Log Version: 1[/FONT]
[FONT=courier new]No Errors Logged[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Self-test log structure revision number 1[/FONT]
[FONT=courier new]Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error[/FONT]
[FONT=courier new]# 1  Short offline       Completed without error       00%     36161         -[/FONT]
[FONT=courier new]# 2  Short offline       Completed without error       00%     15467         -[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Selective self-test log data structure revision number 1[/FONT]
[FONT=courier new] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT]
[FONT=courier new]    1        0        0  Not_testing[/FONT]
[FONT=courier new]    2        0        0  Not_testing[/FONT]
[FONT=courier new]    3        0        0  Not_testing[/FONT]
[FONT=courier new]    4        0        0  Not_testing[/FONT]
[FONT=courier new]    5        0        0  Not_testing[/FONT]
[FONT=courier new]Selective self-test flags (0x0):[/FONT]
[FONT=courier new]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT]
[FONT=courier new]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# smartctl -a /dev/sde1[/FONT]
[FONT=courier new]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)[/FONT]
[FONT=courier new]Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF INFORMATION SECTION ===[/FONT]
[FONT=courier new]Model Family:     Western Digital Caviar Blue (SATA)[/FONT]
[FONT=courier new]Device Model:     WDC WD5000AAKS-00V1A0[/FONT]
[FONT=courier new]Serial Number:    WD-WCAWF1325665[/FONT]
[FONT=courier new]LU WWN Device Id: 5 0014ee 10261475a[/FONT]
[FONT=courier new]Firmware Version: 05.01D05[/FONT]
[FONT=courier new]User Capacity:    500,107,862,016 bytes [500 GB][/FONT]
[FONT=courier new]Sector Size:      512 bytes logical/physical[/FONT]
[FONT=courier new]Device is:        In smartctl database [for details use: -P show][/FONT]
[FONT=courier new]ATA Version is:   ATA8-ACS (minor revision not indicated)[/FONT]
[FONT=courier new]SATA Version is:  SATA 2.6, 3.0 Gb/s[/FONT]
[FONT=courier new]Local Time is:    Wed Feb 17 11:54:28 2016 EST[/FONT]
[FONT=courier new]SMART support is: Available - device has SMART capability.[/FONT]
[FONT=courier new]SMART support is: Enabled[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]=== START OF READ SMART DATA SECTION ===[/FONT]
[FONT=courier new]SMART overall-health self-assessment test result: PASSED[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]General SMART Values:[/FONT]
[FONT=courier new]Offline data collection status:  (0x82)    Offline data collection activity[/FONT]
[FONT=courier new]                    was completed without error.[/FONT]
[FONT=courier new]                    Auto Offline Data Collection: Enabled.[/FONT]
[FONT=courier new]Self-test execution status:      (   0)    The previous self-test routine completed[/FONT]
[FONT=courier new]                    without error or no self-test has ever [/FONT]
[FONT=courier new]                    been run.[/FONT]
[FONT=courier new]Total time to complete Offline [/FONT]
[FONT=courier new]data collection:         ( 7980) seconds.[/FONT]
[FONT=courier new]Offline data collection[/FONT]
[FONT=courier new]capabilities:              (0x7b) SMART execute Offline immediate.[/FONT]
[FONT=courier new]                    Auto Offline data collection on/off support.[/FONT]
[FONT=courier new]                    Suspend Offline collection upon new[/FONT]
[FONT=courier new]                    command.[/FONT]
[FONT=courier new]                    Offline surface scan supported.[/FONT]
[FONT=courier new]                    Self-test supported.[/FONT]
[FONT=courier new]                    Conveyance Self-test supported.[/FONT]
[FONT=courier new]                    Selective Self-test supported.[/FONT]
[FONT=courier new]SMART capabilities:            (0x0003)    Saves SMART data before entering[/FONT]
[FONT=courier new]                    power-saving mode.[/FONT]
[FONT=courier new]                    Supports SMART auto save timer.[/FONT]
[FONT=courier new]Error logging capability:        (0x01)    Error logging supported.[/FONT]
[FONT=courier new]                    General Purpose Logging supported.[/FONT]
[FONT=courier new]Short self-test routine [/FONT]
[FONT=courier new]recommended polling time:      (   2) minutes.[/FONT]
[FONT=courier new]Extended self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (  95) minutes.[/FONT]
[FONT=courier new]Conveyance self-test routine[/FONT]
[FONT=courier new]recommended polling time:      (   5) minutes.[/FONT]
[FONT=courier new]SCT capabilities:            (0x303f)    SCT Status supported.[/FONT]
[FONT=courier new]                    SCT Error Recovery Control supported.[/FONT]
[FONT=courier new]                    SCT Feature Control supported.[/FONT]
[FONT=courier new]                    SCT Data Table supported.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Attributes Data Structure revision number: 16[/FONT]
[FONT=courier new]Vendor Specific SMART Attributes with Thresholds:[/FONT]
[FONT=courier new]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE[/FONT]
[FONT=courier new]  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  3 Spin_Up_Time            0x0027   141   140   021    Pre-fail  Always       -       3916[/FONT]
[FONT=courier new]  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       123[/FONT]
[FONT=courier new]  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0[/FONT]
[FONT=courier new]  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]  9 Power_On_Hours          0x0032   050   050   000    Old_age   Always       -       37069[/FONT]
[FONT=courier new] 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0[/FONT]
[FONT=courier new] 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       121[/FONT]
[FONT=courier new]192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       89[/FONT]
[FONT=courier new]193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       33[/FONT]
[FONT=courier new]194 Temperature_Celsius     0x0022   097   075   000    Old_age   Always       -       46[/FONT]
[FONT=courier new]196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0[/FONT]
[FONT=courier new]198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       18[/FONT]
[FONT=courier new]200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Error Log Version: 1[/FONT]
[FONT=courier new]No Errors Logged[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Self-test log structure revision number 1[/FONT]
[FONT=courier new]Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error[/FONT]
[FONT=courier new]# 1  Short offline       Completed without error       00%     35959         -[/FONT]
[FONT=courier new]# 2  Short offline       Completed without error       00%     15468         -[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]SMART Selective self-test log data structure revision number 1[/FONT]
[FONT=courier new] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT]
[FONT=courier new]    1        0        0  Not_testing[/FONT]
[FONT=courier new]    2        0        0  Not_testing[/FONT]
[FONT=courier new]    3        0        0  Not_testing[/FONT]
[FONT=courier new]    4        0        0  Not_testing[/FONT]
[FONT=courier new]    5        0        0  Not_testing[/FONT]
[FONT=courier new]Selective self-test flags (0x0):[/FONT]
[FONT=courier new]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT]
[FONT=courier new]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT]



```

This is my second attempt after the reboot to assemble the array

```
[FONT=courier new]root@Ubuntu-Server:~# mdadm --stop /dev/md0[/FONT]
[FONT=courier new]mdadm: stopped /dev/md0[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm /dev/md0 --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1[/FONT]
[FONT=courier new]mdadm: forcing event count in /dev/sdc1(3) from 4533 upto 4581[/FONT]
[FONT=courier new]mdadm: forcing event count in /dev/sdb1(2) from 4359 upto 4581[/FONT]
[FONT=courier new]mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdb1[/FONT]
[FONT=courier new]mdadm: clearing FAULTY flag for device 1 in /dev/md0 for /dev/sdc1[/FONT]
[FONT=courier new]mdadm: Marking array /dev/md0 as 'clean'[/FONT]
[FONT=courier new]mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm /dev/md0 --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1[/FONT]
[FONT=courier new]mdadm: /dev/sdb1 is busy - skipping[/FONT]
[FONT=courier new]mdadm: /dev/sdc1 is busy - skipping[/FONT]
[FONT=courier new]mdadm: /dev/sdd1 is busy - skipping[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm --stop /dev/md0[/FONT]
[FONT=courier new]mdadm: stopped /dev/md0[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm /dev/md0 --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1[/FONT]
[FONT=courier new]mdadm: ignoring /dev/sdd1 as it reports /dev/sdb1 as failed[/FONT]
[FONT=courier new]mdadm: ignoring /dev/sdc1 as it reports /dev/sdb1 as failed[/FONT]
[FONT=courier new]mdadm: Marking array /dev/md0 as 'clean'[/FONT]
[FONT=courier new]mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm --stop /dev/md0[/FONT]
[FONT=courier new]mdadm: stopped /dev/md0[/FONT]
[FONT=courier new]root@Ubuntu-Server:~# mdadm /dev/md0 --assemble --force /dev/sdc1 /dev/sdd1 /dev/sde1[/FONT]
[FONT=courier new]mdadm: ignoring /dev/sdd1 as it reports /dev/sdc1 as failed[/FONT]
[FONT=courier new]mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.[/FONT]

```

---

### Post by rubylaser on 2016-02-17
This is tough.  Right now, you have one disk that is so out of date because it's been removed in the past that you can't really use it for reassembly and one that is not working well (read errors).  At this point, you are looking at needing to use something like gddrescue to clone your disk that's having trouble with reads to a new disk and then trying to assemble from there, or trying to go with a recovery company.  mdadm --create --assume-clean isn't going to help because you have two bad disks in a RAID5.

---

### Post by redirect on 2016-02-17
Ok.  I have a spare disk that I just bought to replace the disk that failed so I can probably clone...installing gddrescue.  Any specific instructions I need to know?

D

---

### Post by rubylaser on 2016-02-17
The main advice is to make sure you are first working on the correct disks, so you don't overwrite the wrong one. Here are some good directions (you can skip the Knoppix part and really the smart portion other than to verify you have the correct disks via serial number).

[http://www.kossboss.com/linux---how-to-clone-a-disk-with-ddrescue---dnu-ddrescue-also-known-as-gddrescue---the-better-ddrescue-tool](http://www.kossboss.com/linux---how-to-clone-a-disk-with-ddrescue---dnu-ddrescue-also-known-as-gddrescue---the-better-ddrescue-tool)[B][FONT=courier new]
[/FONT][/B]

---

