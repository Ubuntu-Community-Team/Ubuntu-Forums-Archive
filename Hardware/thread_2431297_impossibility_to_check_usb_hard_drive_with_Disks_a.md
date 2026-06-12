---
title: "impossibility to check usb hard drive with Disks app"
date: 2019-11-14
forum: Hardware
---

### Post by Gingalone on 2019-11-14
I have a recent 3 TB WD usb hard drive (no SSD) which after having worked perfectly for 3 months as a daily backup disk, now get stuck during rsync backup.
I wanted to check the disk integrity with the Disks utility but the menu option "SMART Data & Self-Test..." is grayed out and no disk check is possible.
It looks the Disks app has some problem because even the internal system disk has the same problem...
What's the matter? How can I check my disk?
Thank you for any help

---

### Post by TheFu on 2019-11-14
Install smartmontools, run smartctl with a test, wait for the test to finish, run smartctl to get a test-report.  Look at the raw data column.

If smartctl refuses to grab data, verify that SMART data is enabled in the BIOS settings. Try again.

If smartctl refuses to grab data still, you'll need to figure out the usb disk controller and find what "device option" needs to be used to enable access.

BTW, 3TB disks from every vendor had higher than normal failure rates. Check out the 4 yr old backblaze disk failure statistics.  They post them quarterly, but for 3TB disks, I think 4-6 yrs ago is when they had a few hundred thousand of those devices.  The last few years, backblaze has been using 8, 10, 12TB disks which have turned out to be fairly reliable from all vendors.

---

### Post by Gingalone on 2019-11-15
Thank you TheFu I did what you suggested:```
XPS-13-9370:~$ sudo smartctl --all /dev/sdb1
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               WD
Product:              My Passport 25EA
Revision:             4004
Compliance:           SPC-4
User Capacity:        3,000,558,944,256 bytes [3.00 TB]
Logical block size:   512 bytes
Physical block size:  4096 bytes
LU is resource provisioned, LBPRZ=1
Rotation Rate:        5400 rpm
Form Factor:          2.5 inches
Serial number:        WX51DA6R1534
Device type:          disk
Local Time is:        Fri Nov 15 09:18:51 2019 CET
SMART support is:     Unavailable - device lacks SMART capability.

=== START OF READ SMART DATA SECTION ===
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C

Error Counter logging not supported

No self-tests have been logged
``` It looks the disk doesn't permit a SMART check... Moreover I tried a check on the system SSD:```
XPS-13-9370:~$ sudo smartctl --all /dev/nvme0n1
[sudo] password for gingus: 
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       KXG60ZNV512G NVMe TOSHIBA 512GB
Serial Number:                      Z83A20RJK02N
Firmware Version:                   10604103
PCI Vendor/Subsystem ID:            0x1179
IEEE OUI Identifier:                0x8ce38e
Total NVM Capacity:                 512,110,190,592 [512 GB]
Unallocated NVM Capacity:           0
Controller ID:                      0
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Fri Nov 15 10:04:34 2019 CET
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL *Other*
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat *Other*
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     78 Celsius
Critical Comp. Temp. Threshold:     82 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     6.00W       -        -    0  0  0  0        1       1
 1 +     2.40W       -        -    1  1  1  1        1       1
 2 +     1.90W       -        -    2  2  2  2        1       1
 3 -   0.0500W       -        -    3  3  3  3     1500    1500
 4 -   0.0030W       -        -    4  4  4  4    50000   80000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
Read NVMe SMART/Health Information failed: NVMe Status 0x4002
``` Something (different!) goes wrong also with internal disk... What next?

---

### Post by TheFu on 2019-11-15
Good attempt, but you didn't run the tests FIRST.
> Install smartmontools, run smartctl with a test, wait for the test to finish, run smartctl to get a test-report. Look at the raw data column.
That's 5 steps.  Looks like 2 steps were done, in the wrong order.

---

### Post by Gingalone on 2019-11-15
I am sorry TheFu, I tried several smartctl commands (taking them from [https://sourceforge.net/projects/smartmontools/]("https://sourceforge.net/projects/smartmontools/") since the site [www.smartmontools.org](www.smartmontools.org) is unreachable for me today) and got lots of error messages in response, then I tried:```
XPS-13-9370:~$ sudo smartctl -d sat -t short /dev/sdb1
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Nov 15 14:56:46 2019

Use smartctl -X to abort test.
XPS-13-9370:~$
``` It looked this time the command ran OK, but after 30 mins I got no response of any kind... So I did, as suggested by the command,```
XPS-13-9370:~$ sudo smartctl -X
[sudo] password for gingus: 
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

ERROR: smartctl requires a device name as the final command-line argument.


Use smartctl -h to get a usage summary
XPS-13-9370:~$
``` so tried ```
XPS-13-9370:~$ sudo smartctl -X /dev/sdb1
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

Abort self test failed [unsupported field in scsi command]
XPS-13-9370:~$
``` and got that... At this point I gave up, the problem is above my knowledge...
Help!

---

### Post by TheFu on 2019-11-15
You did some good work and got really close.  Nice job.

First, SMART data is for the entire disk, not 1 partition.
sdb == entire disk
sdb1 == 1st partition on disk

SMART uses whole disk devices, not partitions.

Assuming that *-d sat* is correct and necessary (it might not be), 

```
# Short Test
sudo smartctl -d sat -t short /dev/sdb
# Long test
sudo smartctl -d sat -t long /dev/sdb
```
No need to run both short and long tests.

```

# Request the report
sudo smartctl -d sat -a /dev/sdb
```

Using the correct device type on every smartctl command is required.  The data and reports are stored inside the drive. Without the correct type of device used, the software can't talk using the right dialect needed by the disk.

Running a long test once a week and looking at the report will let you see changes over time.  As the attributes change from new to old to near failure, you'll get a feel for which matter.  If there is 1 relocated sector and no more for another year, I wouldn't worry.  If there are 20 relocated sectors in 1 week, I'd buy a replacement drive ASAP.  If there are any "pending relocated sectors", that means you have data loss already.
Hopefully, you will automate running the long test, perhaps at 5am on Saturday morning and have the report emailed to you 8 hrs later ...   Best to have automatic reminders, right?

---

### Post by Gingalone on 2019-11-20
OK, TheFu thank you for support (and sorry for late reply) the test ran OK, the report:```
XPS-13-9370:~$ sudo smartctl -d sat -a /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-1064-oem] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30NMZW-59GX6S1
Serial Number:    WD-WX51DA6R1534
LU WWN Device Id: 5 0014ee 65cda5c46
Firmware Version: 01.01A01
User Capacity:    3,000,559,424,000 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Nov 20 09:55:15 2019 CET
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
data collection: 		(47700) seconds.
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
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  39) minutes.
SCT capabilities: 	       (0x30b5)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   251   250   021    Pre-fail  Always       -       4408
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
194 Temperature_Celsius     0x0022   130   108   000    Old_age   Always       -       22

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        49         -
# 2  Short offline       Completed without error       00%        47         -

Selective Self-tests/Logging not supported
```IT looks the disk is OK, the only remaining doubt in my mind is if ```
...
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
...
```why in the Disks app this disk still gets the menu option "SMART Data & Self-Test..." grayed out ...

---

### Post by TheFu on 2019-11-20
All the data please. The other attributes can provide hints.

GUI programs aren't as flexible as the real tools. They (GUI programs) usually provide 20% of the functionality available, which is often all that 80% of the users need.  You need more functionality with this specific controller.  Unless 'Disks' has some method to add the device "sat" to the config for this single disk, I don't see how it could possibly work.

I've never used 'Disks' for anything after seeing that it didn't provide the raw data column.  Plus, it isn't available on 95% of my systems and GUIs cannot be automated to run weekly sending a report after completed.  Non-desktop systems don't have GUIs.

Assuming the SMART data is fine, then the next step would be to run **fsck** on each *file system*.  To accomplish that, the file system cannot be mounted or otherwise 'in-use'.  For backup storage, that's easy.  fsck doesn't work on NTFS or fat-whatever storage.  Use Windows tools for those file systems, but for xfs, ext2/3/4, jfs, f2fs and other native Linux file systems, there will be an fsck tool.
```
sudo fsck /dev/sdb1
```
See how the partition number is needed this time?  IF you use LVM, point it at the LV device name, not the VG or PV device names. If you don't use LVM, don't worry about that.

---

### Post by Gingalone on 2019-11-25
OK TheFu, the disk is safe and sound: ```
XPS-13-9370:~$ sudo fsck /dev/sdb1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
BigGainus: clean, 115440/183140352 files, 63146754/732557824 blocks
``` So probably the rsync backup got stuck on some "strange" file: I removed the .googleearth folder the rsynk backup and the process was completed without troubles. (I can't figure what problems can a file have to lock a rsync process).

---

