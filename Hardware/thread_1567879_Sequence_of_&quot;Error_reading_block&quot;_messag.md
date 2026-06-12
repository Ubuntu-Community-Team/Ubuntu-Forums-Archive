---
title: "Sequence of &quot;Error reading block&quot; messages from fsck"
date: 2010-09-04
forum: Hardware
---

### Post by shreepads on 2010-09-04
Folks

Got a bit of a scare when my main storage drive (1.5TB Western Digital Caviar Green) returned a partial folder listing today (my main folder is missing).

Output from fdisk -l (/dev/sdb is the problematic one)

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x314b314a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       38913   271610955    f  W95 Ext'd (LBA)
/dev/sda5            5100       17847   102398278+   7  HPFS/NTFS
/dev/sda6           17848       30595   102398278+   7  HPFS/NTFS
/dev/sda7           30596       33027    19535008+  83  Linux
/dev/sda8           33028       33331     2441848+  82  Linux swap / Solaris
/dev/sda9           33332       38913    44837383+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux


```

I tried a reboot but it then crashed during reboot with a message re 'Error reading block nnnn' and asking me to run it manually.

I ran fsck /dev/sdb then and after startup and got the same error both times:

```

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

```

After some fruitless Googling with this error message I realised I should be running fsck /dev/sdb1 not /dev/sdb.

Ran this and now I'm getting a sequence of "Error reading block" messages starting off with the one reported during bootup.

```
Pass 1: Checking inodes, blocks, and sizes
Error reading block 99331 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 99332 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

```

Starting from block 99331, 99332, .... I am now at 99348 in a precisely sequential order.

Assuming this goes thru succesfully, what should I do next?
- Run fsck -c and check for bad blocks throughout the disk
- Backup the disk first? I really don't have another 1.5TB of storage anywhere right now
- Assume that this is a one off problem with the drive and continue work
- Or just go ahead and replace the disk

Thing is this is a fairly new drive with systematic disk checks at boot at the default periods so am hoping this is a one off problem...

---

### Post by shreepads on 2010-09-04
Got tired of clicking 'Yes' at block 99360 so instead stopped it by choosing 'n' and then ran

```
fsck -y /dev/sdb1
```

But this seems to have started off from the first bad block (99331) again:

```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 99331 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 99332 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

```

Wonder why it didn't start off from where I broke off (i.e. at 99361)?

**Edit:**
The 99331 sequence ended at 99586.
Now there's a new sequence starting from 295939... Got to 295954 so far
Run time for the command almost 4 hrs now :-(

**Edit 2:**
Running overnight, almost 11 hrs since it kicked off. Don't want to break it as it will start from the first erro rblock again but this is ridiculous...
No way the drive could have suddenly hit so many bad blocks due to some physical problems

---

### Post by shreepads on 2010-09-06
Well folks after almost 48 hrs of fsck -y /dev/sdb1 the pain has ended with the following:

```
Error reading block 1769705 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

/dev/sdb1: e2fsck canceled.

/dev/sdb1: ********** WARNING: Filesystem still has errors **********

```

From what I can see I've several series of 256 consecutive blocks that face this problem:
- 99331 to 99586
- 295939 to <not recorded>
- <not recorded> to 327937
- 557058 to 557313
- 786434 to 786689
- 1015810 to 1016065
- 1048578 to <not recorded>
- <not recorded> to 1278209
- 1507330 to <not recorded>
- Terminated at 1769705

Seems to be pretty uniformly distributed and given that its only reached around 0.1% of the 1.4 billion odd blocks I've given up hope... I can't make out any pattern in the sequence above..

Any suggestions?

---

### Post by shreepads on 2010-09-06
Output from SMART, although I haven't the slightest idea of how this should be analysed...

```

 sudo smartctl -a -d ata /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EADS-00S2B0
Serial Number:    WD-WCAVY1005937
Firmware Version: 04.05G04
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Sep  6 19:17:25 2010 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (29160) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       65749
  3 Spin_Up_Time            0x0027   148   147   021    Pre-fail  Always       -       9558
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       352
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2023
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       350
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       120
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1393
194 Temperature_Celsius     0x0022   111   101   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always       -       1463
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   198   160   000    Old_age   Offline      -       467

SMART Error Log Version: 1
ATA Error Count: 29796 (device log contains only the most recent five errors)
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

Error 29796 occurred at disk power-on lifetime: 2023 hours (84 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 87 07 d8 e0  Error: AMNF 8 sectors at LBA = 0x00d80787 = 14157703

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 87 07 d8 e0 08   2d+04:32:36.222  READ DMA
  ec 00 00 00 00 00 a0 08   2d+04:32:36.214  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08   2d+04:32:36.205  IDENTIFY DEVICE

Error 29795 occurred at disk power-on lifetime: 2023 hours (84 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 87 07 d8 e0  Error: AMNF 8 sectors at LBA = 0x00d80787 = 14157703

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 87 07 d8 e0 08   2d+04:32:30.724  READ DMA
  ec 00 00 00 00 00 a0 08   2d+04:32:30.716  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08   2d+04:32:30.703  IDENTIFY DEVICE

Error 29794 occurred at disk power-on lifetime: 2023 hours (84 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 87 07 d8 e0  Error: AMNF 8 sectors at LBA = 0x00d80787 = 14157703

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 87 07 d8 e0 08   2d+04:32:25.201  READ DMA
  ec 00 00 00 00 00 a0 08   2d+04:32:25.194  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08   2d+04:32:25.184  IDENTIFY DEVICE

Error 29793 occurred at disk power-on lifetime: 2023 hours (84 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 87 07 d8 e0  Error: AMNF 8 sectors at LBA = 0x00d80787 = 14157703

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 87 07 d8 e0 08   2d+04:32:19.708  READ DMA
  ec 00 00 00 00 00 a0 08   2d+04:32:19.700  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08   2d+04:32:19.691  IDENTIFY DEVICE

Error 29792 occurred at disk power-on lifetime: 2023 hours (84 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 87 07 d8 e0  Error: AMNF 8 sectors at LBA = 0x00d80787 = 14157703

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 87 07 d8 e0 08   2d+04:32:14.173  READ DMA
  ec 00 00 00 00 00 a0 08   2d+04:32:14.161  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08   2d+04:32:14.152  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      2023         16001376
# 2  Short offline       Completed without error       00%        89         -

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

### Post by shreepads on 2010-09-06
No joy so have disabled mount and fsck at boot by editing the fstab entry for this partition/ drive by setting noauto and last field to 0...

Submitted a request on Western Digital site but the autoreply just directs me to the following so not very hopeful...

> Question
  	How can I get support for my WD product in LINUX or UNIX?
Answer
  	Western Digital technical support only provides jumper configuration (for EIDE hard drive) and physical installation support for hard drives used in systems running the Linux/Unix operating systems. For setup or other questions beyond physical installation of your Western Digital hard drive, please contact your Linux/Unix vendor. You may also wish to discuss your issue on our Community Forums.

Also there are several complaints re errors with Western Digital Caviar Green drives in the Indian tech forums, so seems like I've got one of them...

But reading a bit about SMART, the numbers above seem to be OK, possibly except for the LCC to PCC ratio which is 4 (should ideally be close to one?) which is supposedly caused by poor interaction between Linux and WD Caviar Green's power savings modes...

So is the drive really OK and all I'm seeing are filesystem errors?

---

### Post by shreepads on 2010-09-06
Mounted the drive and am able to do a basic directory listing (except for my main storage folder) and browse around a bit...

So looks like some parts of the drive are still ok..

Any suggestions on what to do next?

---

### Post by AlexZaim on 2010-09-06
I don't know if i can help you with this... but it would be nice to know what OS  version are you using and what kernel version(uname -a). oh, and what type of a filesystem is your sdb?

---

### Post by shreepads on 2010-09-07
> **AlexZaim said:**
> I don't know if i can help you with this... but it would be nice to know what OS  version are you using and what kernel version(uname -a). oh, and what type of a filesystem is your sdb?

Alex the OS is Ubuntu Hardy 8.04 kernel 2.6.24-28-generic. sdb1 is an ext3 filesystem. Details of creation of the same are available at the following post:
[http://ubuntuforums.org/showthread.php?p=8710291#post8710291](http://ubuntuforums.org/showthread.php?p=8710291#post8710291)

---

### Post by shreepads on 2010-09-07
Reviewed the RMA process on WDC.com which indicates that one should first run their Data Lifeguard Diagnostics before submitting for RMA (in India) as per the link below:
  [http://websupport.wdc.com/warranty/rmainfo.asp?india=y&custtype=end](http://websupport.wdc.com/warranty/rmainfo.asp?india=y&custtype=end)

The diagnostic tool (which is inaccurately labelled as applicable only to Win xx) is basically a bootable CD/ floppy Caldera DR-DOS that can run diagnostics, zeroise the drive etc. It can be downloaded (ISO) from the following link:
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/popup_adp.php?p_faqid=1082](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/popup_adp.php?p_faqid=1082)

The above link mentions that
> As of 9/30/09, we no longer provide download support for Data LifeGuard Tools. We are now making Acronis WD Edition software available as the replacement for Data Lifeguard Tools. Download Acronis WD Edition here

But as the Acronis whatever is a Win xx installer I've stuck to the Data Lifeguard Tools download (ver. 5.04f).

Burnt it, stuck it in, booted and ran the Quick and Extended diagnostics:
- Quick result:
> Test Completed with Read Element Failure
Error/ Status Code: 0007
Please back up your data and then run Extended Test
or run a Full Media scan now to resolve this issue...
- Extended result
> 
Too many errors found - Please contact Technical Support
Error/ Status Code: 0225


As per the following link with error code explanations my drive seems to be semi-bricked for sure.
[http://support.wdc.com/techinfo/general/errorcodes.asp?lang=en#v10](http://support.wdc.com/techinfo/general/errorcodes.asp?lang=en#v10)

---

### Post by shreepads on 2010-09-07
Ran SMART again and results as follows. The SMART attributes themselves are quite close to the earlier run and don't show anything seriously wrong.

However the read failure related error messages at the bottom show the problem clearly.

```
sudo smartctl -a -d ata /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EADS-00S2B0
Serial Number:    WD-WCAVY1005937
Firmware Version: 04.05G04
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Sep  7 23:35:44 2010 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (29160) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       65749
  3 Spin_Up_Time            0x0027   166   147   021    Pre-fail  Always       -       8691
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       357
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2030
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       353
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       122
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1396
194 Temperature_Celsius     0x0022   112   101   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always       -       1463
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   198   160   000    Old_age   Offline      -       467

SMART Error Log Version: 1
ATA Error Count: 30125 (device log contains only the most recent five errors)
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

Error 30125 occurred at disk power-on lifetime: 2029 hours (84 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 01 a8 72 08 e0  Error: AMNF at LBA = 0x000872a8 = 553640

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 01 a8 72 08 e0 00      01:42:48.823  READ VERIFY SECTOR(S)
  40 da 01 a7 72 08 e0 00      01:42:44.295  READ VERIFY SECTOR(S)
  40 da 01 a6 72 08 e0 00      01:42:40.598  READ VERIFY SECTOR(S)
  40 da 01 a5 72 08 e0 00      01:42:36.070  READ VERIFY SECTOR(S)
  40 da 01 a4 72 08 e0 00      01:42:32.373  READ VERIFY SECTOR(S)

Error 30124 occurred at disk power-on lifetime: 2029 hours (84 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 01 a7 72 08 e0  Error: AMNF at LBA = 0x000872a7 = 553639

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 01 a7 72 08 e0 00      01:42:44.295  READ VERIFY SECTOR(S)
  40 da 01 a6 72 08 e0 00      01:42:40.598  READ VERIFY SECTOR(S)
  40 da 01 a5 72 08 e0 00      01:42:36.070  READ VERIFY SECTOR(S)
  40 da 01 a4 72 08 e0 00      01:42:32.373  READ VERIFY SECTOR(S)
  40 da 01 a3 72 08 e0 00      01:42:27.845  READ VERIFY SECTOR(S)

Error 30123 occurred at disk power-on lifetime: 2029 hours (84 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 01 a6 72 08 e0  Error: AMNF at LBA = 0x000872a6 = 553638

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 01 a6 72 08 e0 00      01:42:40.598  READ VERIFY SECTOR(S)
  40 da 01 a5 72 08 e0 00      01:42:36.070  READ VERIFY SECTOR(S)
  40 da 01 a4 72 08 e0 00      01:42:32.373  READ VERIFY SECTOR(S)
  40 da 01 a3 72 08 e0 00      01:42:27.845  READ VERIFY SECTOR(S)
  40 da 01 a2 72 08 e0 00      01:42:24.155  READ VERIFY SECTOR(S)

Error 30122 occurred at disk power-on lifetime: 2029 hours (84 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 01 a5 72 08 e0  Error: AMNF at LBA = 0x000872a5 = 553637

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 01 a5 72 08 e0 00      01:42:36.070  READ VERIFY SECTOR(S)
  40 da 01 a4 72 08 e0 00      01:42:32.373  READ VERIFY SECTOR(S)
  40 da 01 a3 72 08 e0 00      01:42:27.845  READ VERIFY SECTOR(S)
  40 da 01 a2 72 08 e0 00      01:42:24.155  READ VERIFY SECTOR(S)
  40 da 01 a1 72 08 e0 00      01:42:19.320  READ VERIFY SECTOR(S)

Error 30121 occurred at disk power-on lifetime: 2029 hours (84 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 01 a4 72 08 e0  Error: AMNF at LBA = 0x000872a4 = 553636

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 01 a4 72 08 e0 00      01:42:32.373  READ VERIFY SECTOR(S)
  40 da 01 a3 72 08 e0 00      01:42:27.845  READ VERIFY SECTOR(S)
  40 da 01 a2 72 08 e0 00      01:42:24.155  READ VERIFY SECTOR(S)
  40 da 01 a1 72 08 e0 00      01:42:19.320  READ VERIFY SECTOR(S)
  40 da 01 a0 72 08 e0 00      01:42:15.624  READ VERIFY SECTOR(S)

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      2030         16001376
# 2  Conveyance offline  Completed: read failure       90%      2029         16001376
# 3  Extended offline    Completed: read failure       90%      2027         16001376
# 4  Extended offline    Completed: read failure       90%      2023         16001376
# 5  Short offline       Completed without error       00%        89         -

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

Clearly the drive needs to be RMAd, questions:
- Any advice on how to get some data off selectively (as I don't have another 1.5TB drive on hand)
- If they give me cash (unlikely) or a choice of another WD drive (maybe possible) what would you recommend in the same price range but more reliable? Am thinking a 1TB Caviar Black or AV-GP series one....

---

