---
title: "HDD fails .. EXT4 completely crashed.. but no obvious reason"
date: 2010-08-16
forum: Hardware
---

### Post by sofamensch on 2010-08-16
I was lately installing on a second partition (ext4). Out of nothing, i started getting Hard Disk errors in the console. (I cannot recall them, but it were the usual Error Reading Sector **** outputs).

This took a few seconds, so i decided to run fsck. It didnt really suceed, because when i typed "sudo fsck" it gave me "sudoers file couldnt be found".
Ok, no deal, i rebooted with a live disk, fsck -a worked for 10 minutes, finally leaving just 500 mb's on the hard disk.

After re-setting up grub i can still without any problem use the first partition. I was running smart-tools, and i get absolutely NO SMART indications for any hardware errors! How could it then crash SO bad?

> smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     IBM/Hitachi Travelstar 60GH and 40GN family
Device Model:     IC25N030ATCS04-0
Serial Number:    CSH308DHJAXN5B
Firmware Version: CA3OA71A
User Capacity:    30,005,821,440 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 3
Local Time is:    Mon Aug 16 11:34:51 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 246)	Self-test routine in progress...
					60% of test remaining.
Total time to complete Offline 
data collection: 		 ( 645) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   3) minutes.
Extended self-test routine
recommended polling time: 	 (  38) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   148   148   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   098   098   000    Old_age   Always       -       3693
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   087   087   000    Old_age   Always       -       5895
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       2782
191 G-Sense_Error_Rate      0x000a   099   099   000    Old_age   Always       -       65537
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       337
193 Load_Cycle_Count        0x0012   082   082   000    Old_age   Always       -       187682
194 Temperature_Celsius     0x0002   130   130   000    Old_age   Always       -       42 (Lifetime Min/Max 6/61)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       2

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
      -
# 2  Short offline       Completed without error       00%      5890         -
# 3  Extended offline    Completed without error       00%      5810         -

Device does not support Selective Self Tests/Logging


---

