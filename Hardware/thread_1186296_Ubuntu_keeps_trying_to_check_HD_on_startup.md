---
title: "Ubuntu keeps trying to check HD on startup"
date: 2009-06-13
forum: Hardware
---

### Post by Corvias on 2009-06-13
Each time I start up my Ubuntu Jaunty 64-bit machine, it keeps trying to check one of my hard disks (/dev/sdc). The entire drive is dedicated to one ext3 partition. I have let ubuntu check it completely several times, but it just tries to check /dev/sdc1 again next reboot anyway. The drive seems to work just fine. Is this a bug or should I be worried about this HD? I turned on SMART monitoring and did a short test. Things seem OK. I am in the process of doing an extended test. Here is the output from "smartctl /dev/sdc -a"

```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD7500AACS-00ZJB0
Serial Number:    WD-WCASJ0139711
Firmware Version: 01.01B01
User Capacity:    750,156,374,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jun 13 08:19:53 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 249)	Self-test routine in progress...
					90% of test remaining.
Total time to complete Offline 
data collection: 		 (20400) seconds.
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
recommended polling time: 	 ( 235) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   180   178   021    Pre-fail  Always       -       7991
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       819
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       6658
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       817
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       61
193 Load_Cycle_Count        0x0032   157   157   000    Old_age   Always       -       130387
194 Temperature_Celsius     0x0022   124   106   000    Old_age   Always       -       28
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6658         -

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

Also, here is the output from executing "tune2fs /dev/sdc1 -l"

```
Filesystem volume name:   Multimedia
Last mounted on:          <not available>
Filesystem UUID:          48f120ee-3736-4be1-873c-f6e096059590
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              91586560
Block count:              183143000
Reserved block count:     0
Free blocks:              40928176
Free inodes:              91414095
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      980
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sun Feb 17 17:38:31 2008
Last mount time:          Sat Jun 13 07:56:56 2009
Last write time:          Sat Jun 13 07:56:56 2009
Mount count:              14
Maximum mount count:      25
Last checked:             Sun Jun  7 06:13:59 2009
Check interval:           15552000 (6 months)
Next check after:         Fri Dec  4 05:13:59 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      d8e1d59a-fda6-4f1b-b9ab-5b83fef0aae0
Journal backup:           inode blocks
```

---

### Post by Bucky Ball on 2009-06-13
I'm not sure where you set this and will have a bit of a look when I have some time, but I think you can set the default (normally 30) number of boots before your hard drive is checked. Perhaps for some reason your default is set to 1.

Not sure what file to look in but you could have a search and a sniff for the appropriate one or any more clues on the net.

---

### Post by Corvias on 2009-06-13
> **Bucky Ball said:**
> I'm not sure where you set this and will have a bit of a look when I have some time, but I think you can set the default (normally 30) number of boots before your hard drive is checked. Perhaps for some reason your default is set to 1.

But that's the weird part! the results of "tune2fs /dev/sdc1 -l" (see above) show the following pertinent bits of info:

```
Mount count:              14
Maximum mount count:      25
Last checked:             Sun Jun  7 06:13:59 2009
Check interval:           15552000 (6 months)
Next check after:         Fri Dec  4 05:13:59 2009
```

So the partition should be checked every 6 months, or every 25 mounts - whichever comes first. As you can see, the last check I let it finish was June 7th, 2009, and it is still 11 mounts away from 25. So, why does ubuntu keep trying to check the drive at each boot?

---

### Post by Corvias on 2009-06-13
OK. I think I might have at least partially figured this out. It seems to be all Microsoft's fault (as usual):p

I have a winxp partition I occasionally boot into to sate the gaming needs ubuntu can't accommodate. For some reason, after I have booted into windows, it seems to trigger a disk check on /dev/sdc1 the next time I boot into Ubuntu. I'm not sure why, but I have a hunch it has to do with Ext2fs. For those not familiar, Ext2fs is a piece of software for windows by Stephan Schreiber which allows you to mount ext2/ext3 partitions in windows.

---

### Post by Bucky Ball on 2009-06-13
It could possibly be because Windows has no idea what an EXT3 partition is and may think there is something faulty so wants to check. Probably some such.

There must be a way to fix this as it seems a pretty rare problem. Never heard that one before, will keep thinking.

When you shutdown Windows, you are doing a restart? Do you get the same problem if you shutdown and boot the machine again afresh into Ubuntu? I'm just wondering if the Windows partition is somehow being left open and is checking/trying to close at boot of Ubuntu (cos Ubuntu not sure what open partition is doing there).

---

