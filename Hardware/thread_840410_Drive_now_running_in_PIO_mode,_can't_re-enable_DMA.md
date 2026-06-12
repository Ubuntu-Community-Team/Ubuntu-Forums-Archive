---
title: "Drive now running in PIO mode, can't re-enable DMA mode."
date: 2008-06-25
forum: Hardware
---

### Post by Digimer on 2008-06-25
Hi all,

  I've been using Ubuntu 8.04 (update from 7.10 on the day it was released) for a while without trouble. Recently though, I noticed my performance tank and I started looking into why. For some reason, my HDD is now running in PIO mode and I can't re-enable DMA mode. :confused:

My laptop is an IBM Thinkpad T40 running a Seagate Momentus 5400.2 60GB drive. Until recently, the drive was detected under SCSI emulation at '/dev/sda', though now it's found at '/dev/hda'. I am not sure if this changed at the same time, but I guess it's safe to assume so.

Some of the details, thanks for any help!

Digi

```
digimer@akane:~$ uname -a
Linux akane 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
```

```
root@akane:/home/digimer# hdparm -d /dev/hda

/dev/hda:
 using_dma     =  0 (off)
```

```
root@akane:/home/digimer# hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)
```

```
root@akane:/home/digimer# hdparm -I /dev/hda

/dev/hda:

ATA device, with non-removable media
	Model Number:       ST960822A                               
	Serial Number:      3LF255XE
	Firmware Revision:  3.02    
Standards:
	Used: ATA/ATAPI-6 T13 1410D revision 2 
	Supported: 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  117210240
	device size with M = 1024*1024:       57231 MBytes
	device size with M = 1000*1000:       60011 MBytes (60 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = ?
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by CSEL
Checksum: correct
```

```
root@akane:/home/digimer# smartctl -a /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST960822A
Serial Number:    3LF255XE
Firmware Version: 3.02
User Capacity:    60,011,642,880 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Jun 25 11:30:47 2008 EDT
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
data collection: 		 ( 426) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  84) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   060   052   034    Pre-fail  Always       -       242374725
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       609
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       74606459
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7708
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       531
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       534
193 Load_Cycle_Count        0x0032   023   023   000    Old_age   Always       -       154010
194 Temperature_Celsius     0x0022   034   056   000    Old_age   Always       -       34 (Lifetime Min/Max 0/12)
195 Hardware_ECC_Recovered  0x001a   060   052   000    Old_age   Always       -       242374725
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 15 (device log contains only the most recent five errors)
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

Error 15 occurred at disk power-on lifetime: 2640 hours (110 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f8 ca 14 20 e0  Error: UNC 248 sectors at LBA = 0x002014ca = 2102474

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f8 ca 14 20 e0 00      00:00:46.318  READ DMA
  f8 00 00 00 00 00 e0 00      00:00:46.318  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:00:46.316  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 02      00:00:46.302  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:00:46.302  READ NATIVE MAX ADDRESS

Error 14 occurred at disk power-on lifetime: 2640 hours (110 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f8 ca 14 20 e0  Error: UNC 248 sectors at LBA = 0x002014ca = 2102474

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f8 ca 14 20 e0 00      00:00:46.318  READ DMA
  f8 00 00 00 00 00 e0 00      00:00:46.318  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:00:46.316  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 02      00:00:46.302  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:00:46.302  READ NATIVE MAX ADDRESS

Error 13 occurred at disk power-on lifetime: 2640 hours (110 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f8 ca 14 20 e0  Error: UNC 248 sectors at LBA = 0x002014ca = 2102474

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f8 ca 14 20 e0 00      00:00:33.519  READ DMA
  f8 00 00 00 00 00 e0 00      00:00:33.519  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:00:33.511  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 02      00:00:27.153  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:00:27.153  READ NATIVE MAX ADDRESS

Error 12 occurred at disk power-on lifetime: 2640 hours (110 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f8 ca 14 20 e0  Error: UNC 248 sectors at LBA = 0x002014ca = 2102474

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f8 ca 14 20 e0 00      00:00:33.519  READ DMA
  f8 00 00 00 00 00 e0 00      00:00:33.519  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:00:33.511  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 02      00:00:27.153  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:00:27.153  READ NATIVE MAX ADDRESS

Error 11 occurred at disk power-on lifetime: 2640 hours (110 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f8 ca 14 20 e0  Error: UNC 248 sectors at LBA = 0x002014ca = 2102474

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f8 ca 14 20 e0 00      00:00:20.721  READ DMA
  f8 00 00 00 00 00 e0 00      00:00:20.720  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      00:00:20.717  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 02      00:00:27.153  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      00:00:27.153  READ NATIVE MAX ADDRESS

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

### Post by greco8523 on 2008-06-25
check your bios, you might of switched off DMA mode by accident. Sometimes PIO mode can mean the drive is starting to fail. So a change of drive could be in order.

---

### Post by Digimer on 2008-07-07
Meh, never figured out the trouble, so I re-installed and it's been fine since. However, the first time I suddenly couldn't log in after a few reboots and reinstalled again. This time it's all good. As for the drive, SMART hasn't tripped, though I didn't do a full scan.

Oh well.

Thanks for replying.

Digi

---

