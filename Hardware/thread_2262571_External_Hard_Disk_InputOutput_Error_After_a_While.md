---
title: "External Hard Disk Input/Output Error After a While"
date: 2015-01-25
forum: Hardware
---

### Post by Peptid on 2015-01-25
Dear All,

I have a Seagate external 2 TB harddisk. I am trying to copy files to it using rsync. 

Here is the problem; after the process starts, I obtain 'input/output error'. Rsync continues the process, however I cannot read the harddisk directory. This problem only occurs after a while, like one hour later.

Previously I used this harddisk to backup my MacBook and I did not receive this error; the process continued like eight hours without an error. I also use another 1 TB external harddisk without any problem.

I used GParted to partition the disk with gtp partition table and ext4 format. I ran fsck command and did not obtain any errors. 

I also include the last lines of the output of dmesg command.

I am on a Dell Latitude with Linux Mint 17, if this is relevant.

Cheers.

[88701.514439] usb 4-1: new SuperSpeed USB device number 10 using xhci_hcd
[88701.533031] usb 4-1: New USB device found, idVendor=0bc2, idProduct=ab21
[88701.533035] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[88701.533038] usb 4-1: Product: Backup+  BL
[88701.533040] usb 4-1: Manufacturer: Seagate 
[88701.533041] usb 4-1: SerialNumber: NA763GH1
[88701.534485] EXT4-fs error (device sdf1): ext4_put_super:791: Couldn't clean up the journal
[88701.534490] EXT4-fs (sdf1): Remounting filesystem read-only
[88701.545973] usb-storage 4-1:1.0: USB Mass Storage device detected
[88701.547478] scsi17 : usb-storage 4-1:1.0
[88702.553024] scsi 17:0:0:0: Direct-Access     Seagate  Backup+  BL      0143 PQ: 0 ANSI: 6
[88702.553500] sd 17:0:0:0: [sdf] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[88702.554051] sd 17:0:0:0: [sdf] Write Protect is off
[88702.554055] sd 17:0:0:0: [sdf] Mode Sense: 2b 00 10 08
[88702.554574] sd 17:0:0:0: Attached scsi generic sg2 type 0
[88702.554666] sd 17:0:0:0: [sdf] Write cache: enabled, read cache: enabled, supports DPO and FUA
[88702.805698]  sdf: sdf1
[88702.807963] sd 17:0:0:0: [sdf] Attached SCSI disk
[88768.290679] EXT4-fs error (device sde1): ext4_put_super:791: Couldn't clean up the journal
[88856.492924] EXT4-fs (sdf1): recovery complete
[88856.493139] EXT4-fs (sdf1): mounted filesystem with ordered data mode. Opts: (null)
[89109.841466] EXT4-fs warning (device sdd1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[89109.841638] EXT4-fs warning (device sdd1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[89109.844685] EXT4-fs error (device sdd1): ext4_find_entry:1309: inode #2: comm bash: reading directory lblock 0
[89110.767603] EXT4-fs warning (device sdd1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[89110.767843] EXT4-fs warning (device sdd1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[89714.075570] usb 4-1: Disable of device-initiated U1 failed.
[89714.079049] xhci_hcd 0000:00:14.0: URB transfer length is wrong, xHC issue? req. len = 0, act. len = 4294967288
[89714.138057] usb 4-1: USB disconnect, device number 10
[89714.598619] usb 4-1: device not accepting address 10, error -22
[89714.689751] sd 17:0:0:0: [sdf] Unhandled error code
[89714.689755] sd 17:0:0:0: [sdf]  
[89714.689756] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[89714.689758] sd 17:0:0:0: [sdf] CDB: 
[89714.689758] Write(10): 2a 00 3a 40 99 00 00 00 f0 00
[89714.689764] end_request: I/O error, dev sdf, sector 977312000
[89714.689788] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011731 (offset 0 size 159744 starting block 260079910)
[89714.689790] buffer_io_error: 78454 callbacks suppressed
[89714.689791] Buffer I/O error on device sdf1, logical block 260079624
[89714.689793] Buffer I/O error on device sdf1, logical block 260079625
[89714.689795] Buffer I/O error on device sdf1, logical block 260079626
[89714.689796] Buffer I/O error on device sdf1, logical block 260079627
[89714.689797] Buffer I/O error on device sdf1, logical block 260079628
[89714.689798] Buffer I/O error on device sdf1, logical block 260079629
[89714.689799] Buffer I/O error on device sdf1, logical block 260079630
[89714.689800] Buffer I/O error on device sdf1, logical block 260079631
[89714.689802] Buffer I/O error on device sdf1, logical block 260079632
[89714.689803] Buffer I/O error on device sdf1, logical block 260079633
[89714.689812] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011731 (offset 0 size 159744 starting block 260079919)
[89714.689817] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011732 (offset 0 size 65536 starting block 260079936)
[89714.689825] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011733 (offset 0 size 73728 starting block 260079954)
[89714.689832] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011734 (offset 0 size 53248 starting block 260079967)
[89714.689841] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011735 (offset 0 size 8388608 starting block 15311134)
[89714.689854] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011735 (offset 0 size 8388608 starting block 15311164)
[89714.689864] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011735 (offset 0 size 8388608 starting block 15311194)
[89714.689874] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011735 (offset 0 size 8388608 starting block 15311224)
[89714.689884] EXT4-fs warning (device sdf1): ext4_end_bio:317: I/O error writing to inode 65011735 (offset 0 size 8388608 starting block 15311254)
[89714.691291] sd 17:0:0:0: [sdf] Unhandled error code
[89714.691295] sd 17:0:0:0: [sdf]  
[89714.691299] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[89714.691304] sd 17:0:0:0: [sdf] CDB: 
[89714.691307] Write(10): 2a 00 3a 40 99 f0 00 00 f0 00
[89714.691313] end_request: I/O error, dev sdf, sector 977312240
[89714.742869] Aborting journal on device sdf1-8.
[89714.742877] JBD2: Error -5 detected when updating journal superblock for sdf1-8.
[89714.743008] EXT4-fs error (device sdf1) in ext4_reserve_inode_write:4849: Journal has aborted
[89714.743106] EXT4-fs error (device sdf1): mpage_map_and_submit_extent:2245: comm kworker/u8:0: Failed to mark inode 65011735 dirty
[89714.743108] EXT4-fs (sdf1): previous I/O error to superblock detected
[89714.743113] EXT4-fs error (device sdf1) in ext4_writepages:2536: Journal has aborted
[89714.743115] EXT4-fs (sdf1): previous I/O error to superblock detected
[89714.743179] end_request: I/O error, dev sdf, sector 0
[89714.746911] EXT4-fs (sdf1): previous I/O error to superblock detected
[89714.746925] EXT4-fs error (device sdf1): ext4_journal_check_start:56: Detected aborted journal
[89714.746928] EXT4-fs (sdf1): Remounting filesystem read-only
[89714.746930] EXT4-fs (sdf1): previous I/O error to superblock detected
[89715.085435] sd 17:0:0:0: [sdf] Synchronizing SCSI cache
[89715.085465] sd 17:0:0:0: [sdf]  
[89715.085467] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[89715.085598] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c07e1f80
[89715.085601] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c07e1fc0
[89715.191883] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm gvfs-udisks2-vo: reading directory lblock 0
[89715.323663] usb 4-1: new SuperSpeed USB device number 11 using xhci_hcd
[89715.342266] usb 4-1: New USB device found, idVendor=0bc2, idProduct=ab21
[89715.342270] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[89715.342272] usb 4-1: Product: Backup+  BL
[89715.342274] usb 4-1: Manufacturer: Seagate 
[89715.342276] usb 4-1: SerialNumber: NA763GH1
[89715.355408] usb-storage 4-1:1.0: USB Mass Storage device detected
[89715.355457] scsi18 : usb-storage 4-1:1.0
[89716.354074] scsi 18:0:0:0: Direct-Access     Seagate  Backup+  BL      0143 PQ: 0 ANSI: 6
[89716.354274] sd 18:0:0:0: Attached scsi generic sg2 type 0
[89716.354425] sd 18:0:0:0: [sde] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[89716.354946] sd 18:0:0:0: [sde] Write Protect is off
[89716.354948] sd 18:0:0:0: [sde] Mode Sense: 2b 00 10 08
[89716.355576] sd 18:0:0:0: [sde] Write cache: enabled, read cache: enabled, supports DPO and FUA
[89716.446222]  sde: sde1
[89716.447758] sd 18:0:0:0: [sde] Attached SCSI disk
[89759.683166] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm gvfsd-recent: reading directory lblock 0
[90594.218245] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm nemo: reading directory lblock 0
[90610.572272] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm nemo: reading directory lblock 0
[90610.572628] EXT4-fs warning: 2227 callbacks suppressed
[90610.572632] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90630.380040] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90634.193156] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90875.437052] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm bash: reading directory lblock 0
[90875.439272] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm bash: reading directory lblock 0
[90913.829630] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90958.108620] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90958.108776] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90958.108924] EXT4-fs warning (device sdf1): __ext4_read_dirblock:908: error reading directory block (ino 2, block 0)
[90958.114418] EXT4-fs error (device sdf1): ext4_find_entry:1309: inode #2: comm bash: reading directory lblock 0

---

### Post by weatherman2 on 2015-01-25
Check the drive's S.M.A.R.T. Attributes with GSmartControl - see if any Attributes are highlighted in pink or red.  Also the short S.M.A.R.T. test (about 2 min).  If GSmartControl can't directly see the drive, try adding parameters for smartctl such as "-T permissive" and "-d sat"  (without the quotes).

Make sure the USB connection is secure and not loose.  Some USB connectors get worn and wind up making loose connections after years of repeated use.

---

### Post by Peptid on 2015-01-26
Hi,

Thanks for the advice. Below I put the output of smartctl -a. As far as I understood everything is working fine.

sudo smartctl -a -T permissive -d sat /dev/sdb1 

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-24-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Device Model:     ST2000LM003 HN-M201RAD
Serial Number:    S32WJ9CF116590
LU WWN Device Id: 5 0004cf 20c2facec
Firmware Version: 2BC10001
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Jan 26 10:33:50 2015 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
Total time to complete Offline 
data collection:         (23340) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 389) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   089   087   025    Pre-fail  Always       -       3478
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       43
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       47
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       31
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   055   055   000    Old_age   Always       -       45 (Min/Max 20/45)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       347

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        47         -
# 2  Short offline       Completed without error       00%        47         -

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Self_test_in_progress [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by Peptid on 2015-01-29
Hi,

After a bit of research, I found that it was related with the power options. I basically followed the solution here [http://askubuntu.com/questions/80638/how-to-disable-auto-power-off-of-usb-devices-like-usb-mouse](http://askubuntu.com/questions/80638/how-to-disable-auto-power-off-of-usb-devices-like-usb-mouse) . Particularly, for my system 

Disabling auto suspending USB
     for i in /sys/bus/usb/devices/*/power/autosuspend;     do echo 2 > $i;     done   

Disable USB autosuspend
for foo in /sys/bus/usb/devices/*/power/level; do echo on > $foo; done 

commands solved the problem.

---

