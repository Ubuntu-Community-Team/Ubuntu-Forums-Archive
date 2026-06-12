---
title: "System freeze / 'exception Emask'"
date: 2008-06-24
forum: Hardware
---

### Post by izi on 2008-06-24
I've been having this problem a while but can't understand why.
Every now and then the system either freezes for a few seconds or completely crashes (hard reboot) and i get:


```
[49854.904768] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[49854.904782] ata3.00: cmd c8/00:08:9d:df:f3/00:00:00:00:00/e5 tag 0 dma 4096 in
[49854.904784]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[49854.904787] ata3.00: status: { DRDY }
[49854.904801] ata3: soft resetting link
[49855.076724] ata3.00: configured for UDMA/133
[49855.076741] ata3: EH complete
[49855.119054] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[49855.134712] sd 2:0:0:0: [sda] Write Protect is off
[49855.134721] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[49855.154650] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I've checked with smartctl /dev/sda -a and it doesn't seem to report a hardware failure:
```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE (Serial ATA) family
Device Model:     WDC WD800JD-00LUA0
Serial Number:    WD-WMAMD3034919
Firmware Version: 06.01D06
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jun 24 08:22:08 2008 IDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (2460) seconds.
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
recommended polling time: 	 (  33) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   182   164   021    Pre-fail  Always       -       1891
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1115
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   061   061   000    Old_age   Always       -       28578
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1073
190 Temperature_Celsius     0x0022   065   035   045    Old_age   Always   In_the_past 35
194 Temperature_Celsius     0x0022   108   078   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       40
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

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

Help anyone ?
is this (yet another) SATA issue ?
I found something a bit similar but I didn't really understand if it's the same problem:
[http://mhalligan.livejournal.com/77689.html](http://mhalligan.livejournal.com/77689.html)

---

