---
title: "RAID5 Array Errors Re-Assembling"
date: 2013-05-08
forum: Hardware
---

### Post by lynwode on 2013-05-08
Folks,
I have a server fail and had to rebuild and thus recreate my RAID array. 

Initially when the array was recreated all was fine and dandy, however upon reboot I was dropped into a busybox shell as the array was in degraded state. This was two days ago

I have been trying all sorts of variants of mdadm and have finally got (what appears on the surface) my array back.

The following created the array and then watching mdstat showed the array was being recovered - cue celebratory beer.....
```

mdadm --create /dev/md0 -v -l 5 -n 4 /dev/sda /dev/sdc /dev/sdd /dev/sdb

```

However this only took 30 mins to complete and not the full 160 that mdstat was reporting - obviously I was too quick in cracking a beer.

```

mdadm -D /dev/md0

```

gives:

```

/dev/md0:
        Version : 1.2
  Creation Time : Wed May  8 21:05:39 2013
     Raid Level : raid5
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 976631296 (931.39 GiB 1000.07 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Wed May  8 21:54:06 2013
          State : clean, FAILED 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : homer:0  (local to host homer)
           UUID : 079732e7:b48de26b:86f320ad:26079d41
         Events : 13

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       0        0        3      removed

       0       8        0        -      faulty spare   /dev/sda
       4       8       16        -      spare   /dev/sdb

```

So my reading is that there is 
1.  a foobarred disk - /dev/sda
2. a spare disk -/dev/sdb


Question:
what are my options to recvover this array?  And before you ask the last backup was a month ago - yes I know......

Any assistance would be greatly appreciated.
Cheers,
Tim.

---

### Post by SaturnusDJ on 2013-05-08
Why did you do a (re)create? That's a kind of last resort, when metadata/superblock information is corrupted or lost.

The basic command to work with in situations like that is:
```
mdadm --assemble /dev/md0 /dev/sd[a-d]
```

You can add some flags if the above doesn't work:
```
mdadm --assemble --force --run /dev/md0 /dev/sd[a-d]
```

Before trying those, the array must be stopped because quite often in situations like this, it's partially assembled.
```
mdadm --stop /dev/md0
```


[SIZE=1]Additional info; read here why you should use partitions instead of whole disks as raid members: [http://ubuntuforums.org/showpost.php?p=12484473&postcount=8](http://ubuntuforums.org/showpost.php?p=12484473&postcount=8) [/SIZE]

---

### Post by lynwode on 2013-05-09
Hi,
I did a re-create as that was pretty much the only option that seemed to be available having read numerous forums. 

My earlier steps did include the commands above. I have just ran them again and the array is now re-building without a faulty disk !

```


   Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       16        3      spare rebuilding   /dev/sdb
root@homer:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda[0] sdb[4] sdd[2] sdc[1]
      2929893888 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.1% (1490944/976631296) finish=174.4min speed=93184K/sec

```

I'm now completely confused !

Well lets see what happens in the next 3 hours.....

---

### Post by lynwode on 2013-05-09
Well that failed as well.

Looks like /dev/sda has errors.

Now I may be wrong but I thought the whole point of having a spare was so that it could be added in to recover the array - I can't seem to get the spare /dev/sdb added back into the array.
Any pointers?

---

### Post by SaturnusDJ on 2013-05-09
You have a 4 disk raid array, and there are 4 disks total. You can't have a spare unless the array was degraded, and the failed disk removed already.

The question is what's wrong, so we'll check SMART data.
```
smartctl -a /dev/sd..
```
That command for every disk.

At the same time let's have a look at the raid member state reported by each disk
```
mdadm --examine /dev/sd*
```

---

### Post by lynwode on 2013-05-09
```

mdadm --examine /dev/sd*

/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 71368172:11f26d46:cf44f2bc:f1d74db8
           Name : homer:0  (local to host homer)
  Creation Time : Thu May  9 21:16:12 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953262592 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bba5b11c:c85e7991:f245f91c:3b8b730d

    Update Time : Thu May  9 21:46:12 2013
       Checksum : a14403e4 - correct
         Events : 9

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 71368172:11f26d46:cf44f2bc:f1d74db8
           Name : homer:0  (local to host homer)
  Creation Time : Thu May  9 21:16:12 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953262592 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e6cde972:33a7818e:301139a2:4b69668b

    Update Time : Thu May  9 21:50:46 2013
       Checksum : f7b91edd - correct
         Events : 13

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 71368172:11f26d46:cf44f2bc:f1d74db8
           Name : homer:0  (local to host homer)
  Creation Time : Thu May  9 21:16:12 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953262592 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ebe3015c:4f01476f:c1616c56:4067eb7a

    Update Time : Thu May  9 21:50:46 2013
       Checksum : 654edd81 - correct
         Events : 13

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 71368172:11f26d46:cf44f2bc:f1d74db8
           Name : homer:0  (local to host homer)
  Creation Time : Thu May  9 21:16:12 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953262592 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c99294f1:83831a1f:820f7bb3:1869bee2

    Update Time : Thu May  9 21:50:46 2013
       Checksum : 6f96be2e - correct
         Events : 13

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AA. ('A' == active, '.' == missing)


```

Smartctl:

/dev/sda

```

smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-003BB1
Serial Number:    WD-WCAV5M579165
LU WWN Device Id: 5 0014ee 20564fd69
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu May  9 22:02:09 2013 EST
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
data collection: 		(23280) seconds.
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
recommended polling time: 	 ( 227) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       7
  3 Spin_Up_Time            0x0027   135   126   021    Pre-fail  Always       -       6233
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       280
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18559
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       171
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       110
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       881913
194 Temperature_Celsius     0x0022   105   091   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     18558         392477408
# 2  Short offline       Completed: read failure       90%     18556         392477408
# 3  Short offline       Completed: read failure       90%     18556         392477408

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

And /dev/sdb

```
smartctl -a /dev/sdb
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-003BB1
Serial Number:    WD-WCAV5J935800
LU WWN Device Id: 5 0014ee 25a860108
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu May  9 22:04:03 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(21060) seconds.
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
recommended polling time: 	 ( 206) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       2
  3 Spin_Up_Time            0x0027   134   124   021    Pre-fail  Always       -       6283
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       418
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18589
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       305
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       236
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       880095
194 Temperature_Celsius     0x0022   103   090   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     18586         -

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
```

And /dev/sdc
```
smartctl -a /dev/sdc
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-003BB1
Serial Number:    WD-WCAV5M594046
LU WWN Device Id: 5 0014ee 20564fd0d
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu May  9 22:04:48 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(21900) seconds.
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
recommended polling time: 	 ( 213) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   132   125   021    Pre-fail  Always       -       6358
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       280
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18586
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       167
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       97
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       879661
194 Temperature_Celsius     0x0022   104   089   000    Old_age   Always       -       43
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     18583         -

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

And finally /dev/sdd

```
smartctl -a /dev/sdd
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-003BB1
Serial Number:    WD-WCAV5M598693
LU WWN Device Id: 5 0014ee 2b00fdaf6
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu May  9 22:05:30 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(21300) seconds.
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
recommended polling time: 	 ( 208) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   135   129   021    Pre-fail  Always       -       6208
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       292
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18587
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       178
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       109
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       887077
194 Temperature_Celsius     0x0022   106   094   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     18584         -

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


Appreciate your help on this :)

---

### Post by lynwode on 2013-05-09
I have also had a look at your link and not quite sure how this fits in with my scenario - I don't (believe) that I used LVM.

---

### Post by SaturnusDJ on 2013-05-09
Something is up with /dev/sda.
Can you start the array without it?
```
mdadm --assemble /dev/md0 /dev/sd[b-d] --no-degraded
```
What does it say?

Alternative:
```
mdadm --assemble /dev/md0 /dev/sd[b-d] --run && mdadm --readonly /dev/md0
```

The idea here is to look what is possible without /dev/sda. If data is intact, you could make a backup or something, and then we'll use badblocks to fill /dev/sda a few times and look again at SMART.

---

### Post by lynwode on 2013-05-09
Ok ran the commands and ...

```
mdadm --assemble /dev/md0 /dev/sd[b-d] --no-degraded
```

```
mdadm: /dev/md0 assembled from 2 drives (out of 4), but not started.
```

```
mdadm --assemble /dev/md0 /dev/sd[b-d] --run && mdadm --readonly /dev/md0
```

```
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.
```

Do I have any hope or am I looking stuffed?

---

### Post by lynwode on 2013-05-09
From /var/log/syslog:

```

May  9 22:45:48 homer kernel: [ 6334.929723] md/raid:md0: device sdd operational as raid disk 2
May  9 22:45:48 homer kernel: [ 6334.929728] md/raid:md0: device sdc operational as raid disk 1
May  9 22:45:48 homer kernel: [ 6334.929732] md/raid:md0: device sda operational as raid disk 0
May  9 22:45:48 homer kernel: [ 6334.930665] md/raid:md0: allocated 4338kB
May  9 22:45:48 homer kernel: [ 6334.930734] md/raid:md0: raid level 5 active with 3 out of 4 devices, algorithm 2
May  9 22:45:48 homer kernel: [ 6334.930738] RAID conf printout:
May  9 22:45:48 homer kernel: [ 6334.930741]  --- level:5 rd:4 wd:3
May  9 22:45:48 homer kernel: [ 6334.930744]  disk 0, o:1, dev:sda
May  9 22:45:48 homer kernel: [ 6334.930747]  disk 1, o:1, dev:sdc
May  9 22:45:48 homer kernel: [ 6334.930750]  disk 2, o:1, dev:sdd
May  9 22:45:48 homer kernel: [ 6334.930797] md0: detected capacity change from 0 to 3000211341312
May  9 22:45:48 homer kernel: [ 6334.930864] RAID conf printout:
May  9 22:45:48 homer kernel: [ 6334.930872]  --- level:5 rd:4 wd:3
May  9 22:45:48 homer kernel: [ 6334.930878]  disk 0, o:1, dev:sda
May  9 22:45:48 homer kernel: [ 6334.930882]  disk 1, o:1, dev:sdc
May  9 22:45:48 homer kernel: [ 6334.930885]  disk 2, o:1, dev:sdd
May  9 22:45:48 homer kernel: [ 6334.930888]  disk 3, o:1, dev:sdb
May  9 22:45:48 homer kernel: [ 6334.931093] md: recovery of RAID array md0
May  9 22:45:48 homer kernel: [ 6334.931099] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
May  9 22:45:48 homer kernel: [ 6334.931104] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
May  9 22:45:48 homer kernel: [ 6334.931114] md: using 128k window, over a total of 976631296k.
May  9 23:20:13 homer kernel: [ 8399.818398] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
May  9 23:20:13 homer kernel: [ 8399.818402] ata1.00: irq_stat 0x40000001
May  9 23:20:13 homer kernel: [ 8399.818405] ata1.00: failed command: READ FPDMA QUEUED
May  9 23:20:13 homer kernel: [ 8399.818410] ata1.00: cmd 60/00:00:e8:b6:64/04:00:17:00:00/40 tag 0 ncq 524288 in
May  9 23:20:13 homer kernel: [ 8399.818410]          res 41/40:00:e0:ba:64/00:00:17:00:00/40 Emask 0x409 (media error) <F>
May  9 23:20:13 homer kernel: [ 8399.818412] ata1.00: status: { DRDY ERR }
May  9 23:20:13 homer kernel: [ 8399.818414] ata1.00: error: { UNC }
May  9 23:20:13 homer kernel: [ 8399.818416] ata1.00: failed command: READ FPDMA QUEUED
May  9 23:20:13 homer kernel: [ 8399.818420] ata1.00: cmd 60/00:08:e8:ba:64/04:00:17:00:00/40 tag 1 ncq 524288 in
May  9 23:20:13 homer kernel: [ 8399.818420]          res 41/40:00:00:00:00/00:00:00:00:00/00 Emask 0x9 (media error)
May  9 23:20:13 homer kernel: [ 8399.818422] ata1.00: status: { DRDY ERR }
May  9 23:20:13 homer kernel: [ 8399.818423] ata1.00: error: { UNC }
May  9 23:20:13 homer kernel: [ 8399.831719] ata1.00: configured for UDMA/133
May  9 23:20:13 homer kernel: [ 8399.831920] sd 0:0:0:0: [sda] Unhandled sense code
May  9 23:20:13 homer kernel: [ 8399.831922] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.831925] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  9 23:20:13 homer kernel: [ 8399.831928] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.831930] Sense Key : Medium Error [current] [descriptor]
May  9 23:20:13 homer kernel: [ 8399.831935] Descriptor sense data with sense descriptors (in hex):
May  9 23:20:13 homer kernel: [ 8399.831937]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
May  9 23:20:13 homer kernel: [ 8399.831952]         17 64 ba e0
]May  9 23:20:13 homer kernel: [ 8399.831958] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.831961] Add. Sense: Unrecovered read error - auto reallocate failed
May  9 23:20:13 homer kernel: [ 8399.831965] sd 0:0:0:0: [sda] CDB:
May  9 23:20:13 homer kernel: [ 8399.831968] Read(10): 28 00 17 64 b6 e8 00 04 00 00
May  9 23:20:13 homer kernel: [ 8399.831981] end_request: I/O error, dev sda, sector 392477408
May  9 23:20:13 homer kernel: [ 8399.831984] raid5_end_read_request: 24 callbacks suppressed
May  9 23:20:13 homer kernel: [ 8399.831987] md/raid:md0: read error not correctable (sector 392477408 on sda).
May  9 23:20:13 homer kernel: [ 8399.831991] md/raid:md0: Disk failure on sda, disabling device.
May  9 23:20:13 homer kernel: [ 8399.831991] md/raid:md0: Operation continuing on 2 devices.
May  9 23:20:13 homer kernel: [ 8399.832046] sd 0:0:0:0: [sda] Unhandled sense code
May  9 23:20:13 homer kernel: [ 8399.832048] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.832049] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  9 23:20:13 homer kernel: [ 8399.832051] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.832052] Sense Key : Medium Error [current] [descriptor]
May  9 23:20:13 homer kernel: [ 8399.832054] Descriptor sense data with sense descriptors (in hex):
May  9 23:20:13 homer kernel: [ 8399.832055]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
May  9 23:20:13 homer kernel: [ 8399.832062]         00 00 00 00
May  9 23:20:13 homer kernel: [ 8399.832066] sd 0:0:0:0: [sda]
May  9 23:20:13 homer kernel: [ 8399.832068] Add. Sense: Unrecovered read error - auto reallocate failed
May  9 23:20:13 homer kernel: [ 8399.832070] sd 0:0:0:0: [sda] CDB:
May  9 23:20:13 homer kernel: [ 8399.832071] Read(10): 28 00 17 64 ba e8 00 04 00 00
May  9 23:20:13 homer kernel: [ 8399.832079] end_request: I/O error, dev sda, sector 392477416
May  9 23:20:13 homer kernel: [ 8399.832082] md/raid:md0: read error not correctable (sector 392477416 on sda).
May  9 23:20:13 homer kernel: [ 8399.832084] md/raid:md0: read error not correctable (sector 392477424 on sda).
May  9 23:20:13 homer kernel: [ 8399.832086] md/raid:md0: read error not correctable (sector 392477432 on sda).
May  9 23:20:13 homer kernel: [ 8399.832088] md/raid:md0: read error not correctable (sector 392477440 on sda).
May  9 23:20:13 homer kernel: [ 8399.832089] md/raid:md0: read error not correctable (sector 392477448 on sda).
May  9 23:20:13 homer kernel: [ 8399.832091] md/raid:md0: read error not correctable (sector 392477456 on sda).
May  9 23:20:13 homer kernel: [ 8399.832092] md/raid:md0: read error not correctable (sector 392477464 on sda).
May  9 23:20:13 homer kernel: [ 8399.832093] md/raid:md0: read error not correctable (sector 392477472 on sda).
May  9 23:20:13 homer kernel: [ 8399.832095] md/raid:md0: read error not correctable (sector 392477480 on sda).
```

To me that suggests that there are a number of areas of /dev/sda have had it....

---

### Post by SaturnusDJ on 2013-05-09
Before each assemble command there must not be any arrays active containing the members you use.
So run this every time when trying to assemble:
```
mdadm --stop /dev/md0
```
That's because mdadm partly assembles when members are missing.

I think there is hope. /dev/sda looks to be failing, but the others are in good shape.

---

### Post by lynwode on 2013-05-09
I have been stopping the array prior to each assemble :)

If there is hope are you able to point me in the right direction? I really do appreciate your help so far - here is a virtual thank-you

[IMG]http://www.sherv.net/cm/emoticons/drink/beer.gif[/IMG]

---

### Post by SaturnusDJ on 2013-05-09
Hmm strange, may be because /dev/sdb is marked as spare. With that chances at getting data back are a bit less.

Can you check if the drives are somehow in use (lsof, e.g.)? 

If that's not the case try assembly again and post the output of
```
cat /proc/mdstat
```
Then we know what drive is not being included.

In any case do not use /dev/sda unless asked to. :)

---

### Post by apokkalyps on 2013-05-09
I don't know why /dev/sdb was a spare that time.  Sometimes drives will get marked as spare if mdadm doesn't know what to do with them (this is a naive statement that I can't back up with explanation, I have just seen it happen).  

When you did a force assemble earlier and then said that "it failed" in post #4, how did it fail?

/dev/sda is definatly a failing piece of hardware from your logs in post #10.  I think you should get a new drive from the store, ddrescue your failing disk to it, and then try to force assemble the array with the new drive instead of the failing one.

Here is an example assuming the new drive comes up as "/dev/sdx" when you plug it in.  Also I call the failling drive "/dev/sda", but before running any command like these do
```
sudo mdadm --examine /dev/sda
```
and make sure it is the one whose last update time is 21:46:12 which is your failed drive, as opposed to the others which were last updated at 21:50:46
I say this just as a precaution to make sure you are ddrescue-ing the correct input device if a reboot or something weird causes them to come up in a different order.

```
sudo apt-get install gddrescue
sudo ddrescue -nfC /dev/sda /dev/sdx /ddrescue.log
sudo ddrescue -fC -r 1 /dev/sda /dev/sdx /ddrescue.log

sudo mdadm --stop /dev/md0
sudo mdadm -Af /dev/md0 /dev/sd[bcdx]
```

Also, I'm kindof a noob too, just learning from my own constant disasters, so you might want to wait on someone else's approval of my advice.  Anyone?

---

### Post by lynwode on 2013-05-09
Output from lsof:

```

lsof /dev/sda
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/lynwode/gvfs
      Output information may be incomplete.
root@homer:~# lsof /dev/sdb
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/lynwode/gvfs
      Output information may be incomplete.
root@homer:~# lsof /dev/sdc
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/lynwode/gvfs
      Output information may be incomplete.
root@homer:~# lsof /dev/sdd
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/lynwode/gvfs
      Output information may be incomplete.

```

So this disks aren't in use - rebuilding and mdstat:

```

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc[1] sdb[4] sdd[2]
      2929894536 blocks super 1.2

```

and for good measure mdadm -D /dev/md0

```
mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu May  9 22:45:47 2013
     Raid Level : raid5
  Used Dev Size : 976631296 (931.39 GiB 1000.07 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri May 10 07:39:15 2013
          State : active, FAILED, Not Started 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : homer:0  (local to host homer)
           UUID : 16c61988:b0f22965:0c9bb9ad:6d25b9c0
         Events : 40

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       16        3      spare rebuilding   /dev/sdb


```

So it says its rebuilding but /proc/mdstat show no activity !

---

### Post by apokkalyps on 2013-05-09
Right now you have 4 disks.  sda is failing hardware, sdb is in some kind of screwed up state where it think's it's a spare and I don't know what to make of that, but fwiw if it tries rebuilding on sdb as a spare then sdb will be wiped I think.  

But either way, if you take sda out of the picture (which you have), and sdb is getting added as a spare, you only have 2 actual devices to get data from.  2 of 4 on raid5 is not enough.  Between sdc and sdd there is not the full set of your data for the array, thus it can't assemble, thus it couldn't rebuild B as a spare even if thats what you wanted to do.  

Although sda is failing, the data is still on it, mdadm doesn't want to use it in the array because it's failing and theoretically could put the other array members at risk.  If you have the data from sda copied onto a disk that isn't failing, you should be able to force assemble the array.  

Buy a new hard drive to replace sda, and ddrescue the data off of it.  Force assemble the array with sdc sdd and the new drive.

---

### Post by lynwode on 2013-05-09
Thank you for spelling out my issues in plain English - I have always had trouble understanding disks and the way they work (I must have a few bad blocks/sectors in my own head).

I'm off to the shop to get a whole new set of disks - as the current ones are all from the same batch and one has failed I'm not taking any risks.

I'll post back later today...

---

### Post by lynwode on 2013-05-10
4 brand new WD Blue 1TB  drives purchased. 
The rescue of (what was) /dev/sda is now in progress..... lets see what happens

---

### Post by lynwode on 2013-05-10
Ok so after 12 hours of copying and then rebuilding we appear to have an array 

```
mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu May  9 22:45:47 2013
     Raid Level : raid5
     Array Size : 2929893888 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 976631296 (931.39 GiB 1000.07 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sat May 11 03:20:02 2013
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : homer:0  (local to host homer)
           UUID : 16c61988:b0f22965:0c9bb9ad:6d25b9c0
         Events : 113

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       64        1      active sync   /dev/sde
       2       8       80        2      active sync   /dev/sdf
       4       8       48        3      active sync   /dev/sdd

```

BUT....

```

[COLOR="#FF0000"]mount /dev/md0[/COLOR]
mount: can't find /dev/md0 in /etc/fstab or /etc/mtab
root@homer:~# mount /dev/md0 /data
mount: you must specify the filesystem type


root@homer:~# [COLOR="#FF0000"]mount -t ext4 /dev/md0 /data[/COLOR]
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm going to hit google now but if anyone has any ideas I'd appreciate some pointers.

---

### Post by SaturnusDJ on 2013-05-10
There are several possible causes of this.
One could be that the recreate was not with exact same parameters.
Another that data got corrupt due to wrong recovery/rebuild earlier.

Try to locate a backup fs superblock.

---

### Post by lynwode on 2013-05-10
Ok this looks really bad to me ...
```
dumpe2fs /dev/md0 | grep -i superblock
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Bad magic number in super-block while trying to open /dev/md0
Couldn't find valid filesystem superblock.

```

I'm guessing I'm up the creek minus paddle and canoe with bloody big Croc staring at me

---

### Post by apokkalyps on 2013-05-10
What command did you use to rebuild the array after the drives were copied?  
Did it take a long time to resync or rebuild or anything?

---

### Post by lynwode on 2013-05-10
```
mdadm --assemble --run --force /dev/md0 /dev/sd[bdef]
```

When I added the new disk the letters got shuffled.

The rebuild then took approx 3hours

---

### Post by SaturnusDJ on 2013-05-11
So you bought 4 news disks and one of the 4 disks is in use now?

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/) is what you can try.

But I think the problems lies deeper. At RAID level. That /dev/sdb device is included I see. Is that the original /dev/sdb? I thought the point of buying a new drive to replace the original /dev/sda was to be able to start degraded without the possibly wrong/corrupted content on original /dev/sdb.

---

