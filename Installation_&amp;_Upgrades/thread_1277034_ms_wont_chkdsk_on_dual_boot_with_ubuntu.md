---
title: "ms wont chkdsk on dual boot with ubuntu"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2009-09-27
i believe i have bad logical sectors in vista
i have allready ran seagate tools for dos
and hdd regenerator
and smartmon tools


the first 2 turned up nothing

smartmon turned up


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.8 family
Device Model:     ST3300831A
Serial Number:    4NF07L5B
Firmware Version: 3.06
User Capacity:    300,069,052,416 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep 27 20:58:43 2009 EDT
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
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 ( 101) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   058   045   006    Pre-fail  Always       -       2904264
  3 Spin_Up_Time            0x0003   100   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1355
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       142120155343
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4549
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1295
194 Temperature_Celsius     0x0022   045   053   000    Old_age   Always       -       45 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   064   049   000    Old_age   Always       -       11584003
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       8
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       8
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 16 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 16 occurred at disk power-on lifetime: 1781 hours (74 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ba 7e 6f e0  Error: UNC at LBA = 0x006f7eba = 7306938

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 d0 00 ba 7e 6f e0 00      00:06:53.423  READ VERIFY SECTOR(S) EXT
  42 d0 00 6f 7a 6f e0 00      00:06:49.910  READ VERIFY SECTOR(S) EXT
  42 d0 00 6e 7a 6f e0 00      00:06:46.500  READ VERIFY SECTOR(S) EXT
  42 d0 00 28 76 6f e0 00      00:06:43.104  READ VERIFY SECTOR(S) EXT
  42 d0 00 22 76 6f e0 00      00:06:43.085  READ VERIFY SECTOR(S) EXT

Error 15 occurred at disk power-on lifetime: 1781 hours (74 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 b9 7e 6f e0  Error: UNC at LBA = 0x006f7eb9 = 7306937

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 d0 00 6f 7a 6f e0 00      00:06:53.423  READ VERIFY SECTOR(S) EXT
  42 d0 00 6e 7a 6f e0 00      00:06:49.910  READ VERIFY SECTOR(S) EXT
  42 d0 00 28 76 6f e0 00      00:06:46.500  READ VERIFY SECTOR(S) EXT
  42 d0 00 22 76 6f e0 00      00:06:43.104  READ VERIFY SECTOR(S) EXT
  42 d0 00 d7 71 6f e0 00      00:06:43.085  READ VERIFY SECTOR(S) EXT

Error 14 occurred at disk power-on lifetime: 1781 hours (74 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 6e 7a 6f e0  Error: UNC at LBA = 0x006f7a6e = 7305838

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 d0 00 6e 7a 6f e0 00      00:06:53.423  READ VERIFY SECTOR(S) EXT
  42 d0 00 28 76 6f e0 00      00:06:49.910  READ VERIFY SECTOR(S) EXT
  42 d0 00 22 76 6f e0 00      00:06:46.500  READ VERIFY SECTOR(S) EXT
  42 d0 00 d7 71 6f e0 00      00:06:43.104  READ VERIFY SECTOR(S) EXT
  42 d0 00 d6 71 6f e0 00      00:06:43.085  READ VERIFY SECTOR(S) EXT

Error 13 occurred at disk power-on lifetime: 1781 hours (74 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 6d 7a 6f e0  Error: UNC at LBA = 0x006f7a6d = 7305837

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 d0 00 28 76 6f e0 00      00:06:53.423  READ VERIFY SECTOR(S) EXT
  42 d0 00 22 76 6f e0 00      00:06:49.910  READ VERIFY SECTOR(S) EXT
  42 d0 00 d7 71 6f e0 00      00:06:46.500  READ VERIFY SECTOR(S) EXT
  42 d0 00 d6 71 6f e0 00      00:06:43.104  READ VERIFY SECTOR(S) EXT
  42 d0 00 00 70 6f e0 00      00:06:43.085  READ VERIFY SECTOR(S) EXT

Error 12 occurred at disk power-on lifetime: 1781 hours (74 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 fb 27 76 6f e0  Error: UNC at LBA = 0x006f7627 = 7304743

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 d0 00 22 76 6f e0 00      00:06:53.423  READ VERIFY SECTOR(S) EXT
  42 d0 00 d7 71 6f e0 00      00:06:49.910  READ VERIFY SECTOR(S) EXT
  42 d0 00 d6 71 6f e0 00      00:06:46.500  READ VERIFY SECTOR(S) EXT
  42 d0 00 00 70 6f e0 00      00:06:43.104  READ VERIFY SECTOR(S) EXT
  42 d0 00 00 68 6f e0 00      00:06:43.085  READ VERIFY SECTOR(S) EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4543         -
# 2  Short offline       Completed without error       00%         1         -

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

--------------------------------------------------------------------------
but the hd keeps locking up right after i play warcraft 3 frozen throne


i have vista home premium and ubuntu 9.04 ,dual boot system.

Has anyone ever seen a prob where vista wont do a error checking on harddrive i tick scan harddrive and tick error checking for messed up sectors but when i reboot ,like it says in the menu when you right click on the harddrive {in vista},

it just does a boot to grub and i select vista in the boot menu

and then it does the fastest scan disk ever

no scanning

just says its done in about 2 seconds


2 questions 

is there a ubuntu program to scan the logical sectors in vista

or is there a way to bypass grub

---

### Post by lindsay7 on 2009-09-27
Use Gparted and use the menu item "partition/check".

---

### Post by jimbean on 2009-09-28
thankyou i used gparted and it found and repaired some stuff
not that computer smart to know what but the computer is not lockingup yet 15 min `s and counting

---

### Post by raymondh on 2009-09-28
> **jimbean said:**
> thankyou i used gparted and it found and repaired some stuff
not that computer smart to know what but the computer is not lockingup yet 15 min `s and counting

well done.  It's a good idea to manually run a fsck every now and then.

regards,

---

### Post by lindsay7 on 2009-09-28
Great.  You can also right click on the drive (i.e. c: or d:) and set it up so that windows will run check disk on the next start up.  Things I have read say you should do this twice.

I have had good luck just using Gparted as you have done.

---

### Post by jimbean on 2009-10-11
well its been 1 week and all is working 
thankyou 
i just want state a couple of more things 
i ran gparted twice
i ran the chkdsk utility in vista twice
and i set all of my bios options to default
cant remember but am almost sure i had a lockup after my first 
gparted scan
and then today 10/11/09 i ran
sudo smartctl -a /dev/sda5
no new errors
and have been thanking you people  and ubuntu ever since

---

