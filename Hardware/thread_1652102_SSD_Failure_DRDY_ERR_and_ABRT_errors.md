---
title: "SSD Failure??? DRDY ERR and ABRT errors"
date: 2010-12-24
forum: Hardware
---

### Post by fxRichard on 2010-12-24
I installed an SSD in my laptop last night, I have been running it in my desktop for about a year and never had any issues then again I didn't pay attention to the kern.log at the time because nothing prompted me to.  Anyway after installing it in my laptop and reinstalling ubuntu 10.10 on it my kern.log is now littered with the following:

```

Dec 24 07:39:41 richard-laptop kernel: [  110.162142] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Dec 24 07:39:41 richard-laptop kernel: [  110.162150] ata1.00: irq_stat 0x40000001
Dec 24 07:39:41 richard-laptop kernel: [  110.162164] ata1.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 0 dma 69632 out
Dec 24 07:39:41 richard-laptop kernel: [  110.162167]          res 51/04:01:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
Dec 24 07:39:41 richard-laptop kernel: [  110.162173] ata1.00: status: { DRDY ERR }
Dec 24 07:39:41 richard-laptop kernel: [  110.162177] ata1.00: error: { ABRT }
Dec 24 07:39:41 richard-laptop kernel: [  110.162187] ata1.00: device reported invalid CHS sector 0
Dec 24 07:39:41 richard-laptop kernel: [  110.162238] end_request: I/O error, dev sda, sector 533248


```

Is it going bad? Or is there a setting that could be causing this?  I did perform most of the SSD tips in the following article (but NOT the no journaling).

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Any ideas?

---

### Post by butonic on 2011-01-07
Same here:

```
[  449.058973] end_request: I/O error, dev sda, sector 75768527
[  449.058986] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  449.059006] ata3.00: irq_stat 0x40000001
[  449.059060] ata3.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 0 dma 8192 out
[  449.059069]          res 51/04:01:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[  449.059093] ata3.00: status: { DRDY ERR }
[  449.059110] ata3.00: error: { ABRT }
[  449.059145] ata3.00: device reported invalid CHS sector 0
[  449.059237] end_request: I/O error, dev sda, sector 75772367
[  455.069059] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  455.069092] ata3.00: irq_stat 0x40000001
[  455.069159] ata3.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 0 dma 12288 out
[  455.069170]          res 51/04:01:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[  455.069196] ata3.00: status: { DRDY ERR }
[  455.069214] ata3.00: error: { ABRT }
[  455.069264] ata3.00: device reported invalid CHS sector 0
[  455.069370] end_request: I/O error, dev sda, sector 78946655

```

This is a Maxflash Rapstore 128GB (SSD128GNOB-HSM1) with ext4 and discard enabled. Kernel 2.6.35-020635-generic. The laptop runs fine and there are no other hiccups. Hints, anyone?

---

### Post by psusi on 2011-01-07
Fire up the disk utility and check the SMART stats.

---

### Post by butonic on 2011-01-07
```
# sudo smartctl --all /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SSD128GNOB-HSM1
Serial Number:    <censored>
Firmware Version: 1571
User Capacity:    128.035.676.160 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jan  7 23:14:19 2011 CET
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
data collection: 		 (   0) seconds.
Offline data collection
capabilities: 			 (0x1d) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Abort Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x00)	Error logging NOT supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   0) minutes.
Extended self-test routine
recommended polling time: 	 (   0) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   007   000   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   202   001   000    Old_age   Offline      -       0
 12 Power_Cycle_Count       0x0000   169   000   000    Old_age   Offline      -       0
184 End-to-End_Error        0x0000   018   000   000    Old_age   Offline      -       0
195 Hardware_ECC_Recovered  0x0000   000   000   000    Old_age   Offline      -       0
196 Reallocated_Event_Count 0x0000   000   000   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0000   000   000   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0000   131   213   000    Old_age   Offline      -       38503
199 UDMA_CRC_Error_Count    0x0000   021   007   000    Old_age   Offline      -       39935
200 Multi_Zone_Error_Rate   0x0000   016   197   000    Old_age   Offline      -       401
201 Soft_Read_Error_Rate    0x0000   197   047   000    Old_age   Offline      -       173
202 Data_Address_Mark_Errs  0x0000   164   115   000    Old_age   Offline      -       2
203 Run_Out_Cancel          0x0000   030   103   000    Old_age   Offline      -       2
204 Soft_ECC_Correction     0x0000   000   000   000    Old_age   Offline      -       0
205 Thermal_Asperity_Rate   0x0000   160   134   000    Old_age   Offline      -       1
206 Flying_Height           0x0000   001   000   000    Old_age   Offline      -       0
207 Spin_High_Current       0x0000   219   006   000    Old_age   Offline      -       0
208 Spin_Buzz               0x0000   067   000   000    Old_age   Offline      -       0
209 Offline_Seek_Performnce 0x0000   100   000   000    Old_age   Offline      -       0
210 Unknown_Attribute       0x0000   238   000   000    Old_age   Offline      -       0
211 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline      -       0

Warning: device does not support Error Logging
Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging

```

The values don't change when dmesg spits out the errors given above.

---

### Post by psusi on 2011-01-07
You have 38,503 bad sectors.  Time to RMA the drive if it is still under warranty.

---

