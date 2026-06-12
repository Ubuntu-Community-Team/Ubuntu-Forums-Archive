---
title: "SSD errors"
date: 2011-06-22
forum: Hardware
---

### Post by mike.doherty on 2011-06-22
Hello,

I recently found my laptop unable to mount filesystems on my Vertex 2 SSD. I've attached two logs that reveal errors like:
```

ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }

```
and
```

ACPI Error (psargs-0359): [GTF0] Namespace lookup failure, AE_NOT_FOUND
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT0._SDD] (Node ffff880133a427e0), AE_NOT_FOUND

```

The sections of interest begin at:
```

Jun 21 22:44:45 charron kernel: [    1.670805]

```

Upon booting into a rescue environment, I repaired these ext4 filesystems with fsck, which found many errors. On rebooting, further repair with fsck was required, but the system did boot, and seems stable at present. SMART diagnostics are shown here:
```

smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     OCZ Vertex SSD
Device Model:     OCZ-VERTEX2
Serial Number:    OCZ-3OWQ25NP3F33QV35
Firmware Version: 1.24
User Capacity:    90,028,302,336 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Wed Jun 22 22:14:23 2011 ADT
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
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   102   100   050    Pre-fail  Always       -       5236453
  5 Reallocated_Sector_Ct   0x0033   100   100   003    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   ---   ---   ---    Old_age   Always       -       13504606432855549028
 12 Power_Cycle_Count       0x0032   ---   ---   ---    Old_age   Always       -       38823012
171 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   000   000   000    Old_age   Offline      -       47
177 Wear_Leveling_Count     0x0000   000   000   000    Old_age   Offline      -       1
181 Program_Fail_Cnt_Total  0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   085   085   000    Old_age   Always       -       15
194 Temperature_Celsius     0x0022   001   129   000    Old_age   Always       -       1 (0 127 0 129)
195 Program_Failure_Blk_Ct  0x001c   ---   ---   ---    Old_age   Offline      -       343176209510
196 Erase_Failure_Blk_Ct    0x0033   ---   ---   ---    Pre-fail  Always       -       25700
231 Temperature_Celsius     0x0013   100   100   010    Pre-fail  Always       -       0
233 Media_Wearout_Indicator 0x0000   000   000   000    Old_age   Offline      -       2944
234 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       1792
241 Total_LBAs_Written      0x0032   000   000   000    Old_age   Always       -       1792
242 Total_LBAs_Read         0x0032   000   000   000    Old_age   Always       -       3008

Error SMART Error Log Read failed: Input/output error
Smartctl: SMART Error Log Read Failed
Error SMART Error Self-Test Log Read failed: Input/output error
Smartctl: SMART Self Test Log Read Failed
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

I would appreciate help digesting the logs - if there is a hardware problem, then the drive is under warranty and I'll seek an RMA. Otherwise, I'd like to understand the cause of these errors - the other likely cause is a kernel bug, which I'd like to seek a resolution for.

Luckily, I have little of value on this SSD, and what is valuable has been backed up on a regular basis.

Thanks,
-Mike

---

