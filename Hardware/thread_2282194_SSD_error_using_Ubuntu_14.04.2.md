---
title: "SSD error using Ubuntu 14.04.2"
date: 2015-06-12
forum: Hardware
---

### Post by pranithkumar on 2015-06-12
Hi,

I have two drives in my system, an SSD and a rust disk. I got the following error on my desktop when doing a kernel compile. Can anyone tell me if this can be fixed or if I need to replace the hard disk? ata10.00 seems to be the SSD.

root@evgadesktop:~# dmesg | grep ata10
[    0.621811] ata10: SATA max UDMA/133 abar m512@0xef420000 port 0xef420180 irq 50
[    1.101938] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.103346] ata10.00: ATA-9: INTEL SSDSC2CW180A3, 400i, max UDMA/133
[    1.103351] ata10.00: 351651888 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.113238] ata10.00: configured for UDMA/133

dmesg:

[ 2304.274460] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2304.274465] ata10.00: irq_stat 0x40000001
[ 2304.274469] ata10.00: failed command: DATA SET MANAGEMENT
[ 2304.274475] ata10.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 22 dma 512 out
[ 2304.274475]          res 51/04:00:01:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[ 2304.274478] ata10.00: status: { DRDY ERR }
[ 2304.274480] ata10.00: error: { ABRT }
[ 2304.274492] sd 9:0:0:0: [sdb]  
[ 2304.274494] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2304.274496] sd 9:0:0:0: [sdb]  
[ 2304.274498] Sense Key : Aborted Command [current] [descriptor]
[ 2304.274501] Descriptor sense data with sense descriptors (in hex):
[ 2304.274502]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2304.274511]         00 00 00 00 
[ 2304.274514] sd 9:0:0:0: [sdb]  
[ 2304.274516] Add. Sense: No additional sense information
[ 2304.274518] sd 9:0:0:0: [sdb] CDB: 
[ 2304.274520] Write same(16): 93 08 00 00 00 00 03 ee 23 28 00 00 00 18 00 00
[ 2304.274530] end_request: I/O error, dev sdb, sector 65938216

Smartctl output for both drives:

```

root@evgadesktop:~# smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WMAZA9363887
LU WWN Device Id: 5 0014ee 206f763e2
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Jun 12 12:16:48 2015 EDT
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
data collection: 		(37980) seconds.
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
recommended polling time: 	 ( 366) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   167   162   021    Pre-fail  Always       -       6625
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       110
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   069   069   000    Old_age   Always       -       22753
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       108
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       80
193 Load_Cycle_Count        0x0032   127   127   000    Old_age   Always       -       221899
194 Temperature_Celsius     0x0022   123   106   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     22750         -

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

root@evgadesktop:~# smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Intel 520 Series SSDs
Device Model:     INTEL SSDSC2CW180A3
Serial Number:    CVCV204406BL180EGN
LU WWN Device Id: 5 001517 bb2823ab8
Firmware Version: 400i
User Capacity:    180,045,766,656 bytes [180 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Jun 12 12:16:51 2015 EDT
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
data collection: 		( 2097) seconds.
Offline data collection
capabilities: 			 (0x7f) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Abort Offline collection upon new
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  48) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x0021)	SCT Status supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   000    Old_age   Always       -       0
  9 Power_On_Hours_and_Msec 0x0032   000   000   000    Old_age   Always       -       914442h+55m+33.390s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       77
170 Available_Reservd_Space 0x0033   100   100   010    Pre-fail  Always       -       0
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   000    Old_age   Always       -       0
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       76
184 End-to-End_Error        0x0033   100   100   090    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       76
225 Host_Writes_32MiB       0x0032   100   100   000    Old_age   Always       -       154033
226 Workld_Media_Wear_Indic 0x0032   100   100   000    Old_age   Always       -       65535
227 Workld_Host_Reads_Perc  0x0032   100   100   000    Old_age   Always       -       17
228 Workload_Minutes        0x0032   100   100   000    Old_age   Always       -       65535
232 Available_Reservd_Space 0x0033   100   100   010    Pre-fail  Always       -       0
233 Media_Wearout_Indicator 0x0032   100   100   000    Old_age   Always       -       0
241 Host_Writes_32MiB       0x0032   100   100   000    Old_age   Always       -       154033
242 Host_Reads_32MiB        0x0032   100   100   000    Old_age   Always       -       32386
249 NAND_Writes_1GiB        0x0013   100   100   000    Pre-fail  Always       -       6020

SMART Error Log not supported

SMART Self-test Log not supported

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

