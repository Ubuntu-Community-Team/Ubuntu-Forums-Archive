---
title: "SSD device reported invalid CHS sector 0"
date: 2020-10-29
forum: Hardware
---

### Post by afrodeity on 2020-10-29
I have an ssd which I added to an LVM, after some difficulty, [see this thread here.]("https://ubuntuforums.org/showthread.php?t=2451166")

my system log is reporting

```
blk_update_request: I/O error, dev sdb, sector 54214696 op 0x3:(DISCARD) flags 0x0 phys_seg 1 prio class 0
```


I have booted with an Ubuntu 20.04 install disk, and done
fsck -fy /dev/ubuntu-vg/root

No problems with the filesystem reported, it merely narrowed an inode.


If I dmesg -w
```

ata2.00: device reported invalid CHS sector 0
[ 1514.794944] sd 1:0:0:0: [sdb] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1514.794946] sd 1:0:0:0: [sdb] tag#7 Sense Key : Illegal Request [current] 
[ 1514.794947] sd 1:0:0:0: [sdb] tag#7 Add. Sense: Unaligned write command
[ 1514.794949] sd 1:0:0:0: [sdb] tag#7 CDB: Write same(16) 93 08 00 00 00 00 01 ef d0 00 00 00 07 c8 00 00
[ 1514.794950] blk_update_request: I/O error, dev sdb, sector 32493568 op 0x3:(DISCARD) flags 0x800 phys_seg 1 prio class 0
[ 1647.551366] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1647.551368] ata2.00: irq_stat 0x40000001
[ 1647.551369] ata2.00: failed command: DATA SET MANAGEMENT
[ 1647.551372] ata2.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 7 dma 512 out
                        res 51/04:01:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 1647.551373] ata2.00: status: { DRDY ERR }
[ 1647.551374] ata2.00: error: { ABRT }
```

```
sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       FASTDISK032GB                           
	Serial Number:      AA00000000000108528 
	Firmware Revision:  20130816
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:    16514064
	LBA    user addressable sectors:    61968384
	LBA48  user addressable sectors:    61968384
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:       30258 MBytes
	device size with M = 1000*1000:       31727 MBytes (31 GB)
	cache/buffer size  = 1 KBytes (type=DualPort)
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Vendor, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART self-test
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Data Set Management TRIM supported (limit 1 block)
Checksum: correct

```

My fstab:

```
/dev/mapper/ubuntu--vg-root /     ext4    discard,noatime,errors=remount-ro 0       1
/dev/mapper/ubuntu--vg-swap_1 none     swap    sw    0       0

# SSD tweak : temporary directories as tmpfs
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

# SSD tweak : extra steps (read ahead)
#tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0
tmpfs /var/spool tmpfs defaults,noatime,mode=1777 0 0

```

So there maybe something going on with my fstab settings. Otherwise only other thing I can think of is to replace the cable?

---

### Post by afrodeity on 2020-10-29
```
sudo smartctl -a /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-52-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     FASTDISK032GB
Serial Number:    AA00000000000108528
Firmware Version: 20130816
User Capacity:    31,727,812,608 bytes [31.7 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Oct 29 13:31:11 2020 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x00) 	Offline data collection not supported.
SMART capabilities:            (0x0002)	Does not save SMART data before
					entering power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x00)	Error logging NOT supported.
					No General Purpose Logging support.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   050    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0002   100   100   050    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0000   100   100   050    Old_age   Offline      -       1606
160 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       159
162 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       140
163 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       3
164 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       6203622
165 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       3064
166 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       2978
167 Unknown_Attribute       0x0000   100   100   050    Old_age   Offline      -       3005
192 Power-Off_Retract_Count 0x0000   100   100   050    Old_age   Offline      -       0
194 Temperature_Celsius     0x0000   100   100   050    Old_age   Offline      -       40 (Min/Max 40/40)
195 Hardware_ECC_Recovered  0x0000   100   100   050    Old_age   Offline      -       0
196 Reallocated_Event_Count 0x0000   100   100   050    Old_age   Offline      -       2
198 Offline_Uncorrectable   0x0000   000   000   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       1
241 Total_LBAs_Written      0x0032   100   100   050    Old_age   Always       -       304821
242 Total_LBAs_Read         0x0032   100   100   050    Old_age   Always       -       1708736

SMART Error Log not supported

Read SMART Self-test Log failed: scsi error badly formed scsi parameters

Selective Self-tests/Logging not supported

```

---

### Post by afrodeity on 2020-11-06
So I bought a new gigabyte ssd 120GB at a reasonable price.

then:

```
 sudo pvcreate /dev/sdc1
WARNING: ext4 signature detected on /dev/sdc1 at offset 1080. Wipe it? [y/n]: y
  Wiping ext4 signature on /dev/sdc1.
  Physical volume "/dev/sdc1" successfully created.

sudo lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sda1   [    <223.57 GiB] LVM physical volume
  /dev/sdb1   [     <29.55 GiB] LVM physical volume
  /dev/sdc1   [    <111.79 GiB] LVM physical volume
  0 LVM physical volume whole disks
  3 LVM physical volumes

 sudo vgextend ubuntu-vg /dev/sdc1
  Volume group "ubuntu-vg" successfully extended

sudo lvextend -l +100%FREE /dev/ubuntu-vg/root
  Size of logical volume ubuntu-vg/root changed from <252.16 GiB (64552 extents) to 363.94 GiB (93169 extents).
  Logical volume ubuntu-vg/root successfully resized.

sudo resize2fs -p /dev/mapper/ubuntu--vg-root
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/ubuntu--vg-root is mounted on /; on-line resizing required
old_desc_blocks = 32, new_desc_blocks = 46
The filesystem on /dev/mapper/ubuntu--vg-root is now 95405056 (4k) blocks long.

```

---

### Post by afrodeity on 2020-11-06
Now to remove the 30Gb volume on /dev/sdb1

```

sudo resize2fs -p /dev/mapper/ubuntu--vg-root 325G
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/ubuntu--vg-root is mounted on /; on-line resizing required
resize2fs: On-line shrinking not supported

```

Ok, I should have done the calculation of total space minus the drive I want to remove to begin with.
"[Resize the filesystem to a size that is lower than the total of the LVM array size after the drive is removed.]("https://www.networkinghowtos.com/howto/remove-disk-from-lvm-array-on-ubuntu/")"

Looks like I going to have to boot up with a live disk

---

### Post by afrodeity on 2020-11-06
```

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/mapper/ubuntu--vg-root
e2fsck 1.45.5 (07-Jan-2020)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/ubuntu--vg-root: 2938497/23855104 files (0.9% non-contiguous), 63141511/95405056 blocks
ubuntu@ubuntu:~$ sudo resize2fs -p /dev/mapper/ubuntu--vg-root 325G
resize2fs 1.45.5 (07-Jan-2020)
Resizing the filesystem on /dev/mapper/ubuntu--vg-root to 85196800 (4k) blocks.
Begin pass 3 (max = 2912)
Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/mapper/ubuntu--vg-root is now 85196800 (4k) blocks long.

sudo lvreduce -L 330G /dev/mapper/ubuntu--vg-root
  WARNING: Reducing active logical volume to 330.00 GiB.
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce ubuntu-vg/root? [y/n]: y
  Size of logical volume ubuntu-vg/root changed from 363.94 GiB (93169 extents) to 330.00 GiB (84480 extents).
  Logical volume ubuntu-vg/root successfully resized.

sudo pvs
  PV         VG        Fmt  Attr PSize    PFree 
  /dev/sda1  ubuntu-vg lvm2 a--  <223.57g     0 
  /dev/sdb1  ubuntu-vg lvm2 a--   <29.55g     0 
  /dev/sdc1  ubuntu-vg lvm2 a--  <111.79g 33.94g

```

now remove physical extant off the failing drive.

```

sudo pvmove -i 600 -v /dev/sdb1
  Archiving volume group "ubuntu-vg" metadata (seqno 10).
  Creating logical volume pvmove0
  activation/volume_list configuration setting not defined: Checking only host tags for ubuntu-vg/root.
  Moving 7564 extents of logical volume ubuntu-vg/root.
  activation/volume_list configuration setting not defined: Checking only host tags for ubuntu-vg/root.
  Creating ubuntu--vg-pvmove0
  Loading table for ubuntu--vg-pvmove0 (253:2).
  Loading table for ubuntu--vg-root (253:0).
  Suspending ubuntu--vg-root (253:0) with device flush
  Resuming ubuntu--vg-pvmove0 (253:2).
  Resuming ubuntu--vg-root (253:0).
  Creating volume group backup "/etc/lvm/backup/ubuntu-vg" (seqno 11).
  activation/volume_list configuration setting not defined: Checking only host tags for ubuntu-vg/pvmove0.
  Checking progress before waiting every 600 seconds.
  /dev/sdb1: Moved: 0.01%

```

Making some coffee while I wait for this operation to complete.
And check this [post.]("https://sysadmins.co.za/create-a-logical-storage-volume-using-lvm-on-ubuntu/")

---

### Post by afrodeity on 2020-11-06
```
 Checking progress before waiting every 600 seconds.
  /dev/sdb1: Moved: 0.01%
  /dev/sdb1: Moved: 100.00%
  Polling finished successfully.

```
```

sudo vgreduce ubuntu-vg /dev/sdb1
  Removed "/dev/sdb1" from volume group "ubuntu-vg"

```
```

sudo pvremove /dev/sdb1
  Labels on physical volume "/dev/sdb1" successfully wiped.

```

```
sudo vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  14
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               335.35 GiB
  PE Size               4.00 MiB
  Total PE              85850
  Alloc PE / Size       84725 / <330.96 GiB
  Free  PE / Size       1125 / 4.39 GiB
  VG UUID               PsnpQf-GoXN-hm04-bJxr-462u-9VOh-RlpLfx
   
```
```

ubuntu@ubuntu:~$ sudo lvextend -l +100%FREE /dev/ubuntu-vg/root
  Size of logical volume ubuntu-vg/root changed from 330.00 GiB (84480 extents) to 334.39 GiB (85605 extents).
  Logical volume ubuntu-vg/root successfully resized.
ubuntu@ubuntu:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  15
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               335.35 GiB
  PE Size               4.00 MiB
  Total PE              85850
  Alloc PE / Size       85850 / 335.35 GiB
  Free  PE / Size       0 / 0   
  VG UUID               PsnpQf-GoXN-hm04-bJxr-462u-9VOh-RlpLfx
   
```
```

ubuntu@ubuntu:~$ sudo resize2fs -p /dev/mapper/ubuntu--vg-root
resize2fs 1.45.5 (07-Jan-2020)
Resizing the filesystem on /dev/mapper/ubuntu--vg-root to 87659520 (4k) blocks.
The filesystem on /dev/mapper/ubuntu--vg-root is now 87659520 (4k) blocks long.

```

Success :guitar:

---

### Post by afrodeity on 2020-11-17
Its been a week since I installed the new SSD (sdb) ata4
 
I now have a sleep resume issue:

logs
```

ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x50000 action 0x6 frozen
ata4: SError: { PHYRdyChg CommWake }
ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x50000 action 0x6 frozen

```

dmesg

```

[ 6049.308712] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 6049.310637] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 6049.310698] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 6049.310703] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 6049.312580] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 6049.312585] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 6049.312589] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 6049.312720] ata4.00: configured for UDMA/33
[ 6049.312724] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[ 6049.312821] ata4: EH complete
[ 6173.920097] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x50000 action 0x6 frozen
[ 6173.920105] ata4: SError: { PHYRdyChg CommWake }
[ 6173.920111] ata4.00: failed command: WRITE DMA
[ 6173.920123] ata4.00: cmd ca/00:08:00:2a:07/00:00:00:00:00/e3 tag 10 dma 4096 out
[ 6173.920127] ata4.00: status: { DRDY }
[ 6173.920133] ata4: hard resetting link

```

---

### Post by afrodeity on 2020-11-17
```

sudo smartctl -a -d ata /dev/sdb
[sudo] password for afropunk: 
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-53-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     GIGABYTE GP-GSTFS31120GNTD
Serial Number:    SN201408908856
Firmware Version: SBFM61.3
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-4 (minor revision not indicated)
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Tue Nov 17 10:16:26 2020 SAST
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
data collection: 		(65535) seconds.
Offline data collection
capabilities: 			(0x79) SMART execute Offline immediate.
					No Auto Offline data collection support.
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
recommended polling time: 	(   2) minutes.
Extended self-test routine
recommended polling time: 	(  30) minutes.
Conveyance self-test routine
recommended polling time: 	(   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       481
 12 Power_Cycle_Count       0x0012   100   100   000    Old_age   Always       -       818
168 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       0
170 Unknown_Attribute       0x0003   100   100   000    Pre-fail  Always       -       66
173 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       262175
192 Power-Off_Retract_Count 0x0012   100   100   000    Old_age   Always       -       764
194 Temperature_Celsius     0x0023   067   067   000    Pre-fail  Always       -       33 (Min/Max 33/33)
218 Unknown_Attribute       0x000b   100   100   050    Pre-fail  Always       -       0
231 Temperature_Celsius     0x0013   100   100   000    Pre-fail  Always       -       99
241 Total_LBAs_Written      0x0012   100   100   000    Old_age   Always       -       158

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       473         -

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

### Post by afrodeity on 2020-11-17
:popcorn: Okay, so if anyone happens to stumble upon this thread, here is the outcome. I replaced the cable twice, three times. It was still kicking up the problem. Then I moved the Second SSD to Ata2, where the old SSD had been installed. The new one had been installed on Ata4. Now its humming along just fine, and also replaced a fan that was bothering me. I guess I should invest in some quality cables. Is this sign that my Ata controller is buggy? Most likely it has something to do with the kernel or Mobi not coping with the new setup.

---

