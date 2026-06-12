---
title: "Reading a SMART report"
date: 2017-12-21
forum: Hardware
---

### Post by Superdude_123 on 2017-12-21
I'm trying to figure out why my Ubuntu system is crashing/hanging randomly after being rebooted for just under 5-10 min. Before another random freeze, I was able to pull out a SMART hard drive report. Could someone tell me what they see in this, and how they are reading it? The area that I understand the least in the log is the "Vendor Specific SMART Attributes with Thresholds:".

The report is as follows for my / disk:

```

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.10.0-42-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST2000DM001-1ER164
Serial Number:    XXX
LU WWN Device Id: 5 000c50 0934a0a75
Firmware Version: CC26
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Dec 21 11:04:38 2017 AST
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
data collection: 		(   89) seconds.
Offline data collection
capabilities: 			 (0x73) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
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
recommended polling time: 	 ( 212) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x1085)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       79006672
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       60
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   067   060   030    Pre-fail  Always       -       17202753427
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8444
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       60
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   064   045    Old_age   Always       -       24 (Min/Max 23/24)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       6584
194 Temperature_Celsius     0x0022   024   040   000    Old_age   Always       -       24 (0 13 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       8349h+12m+11.900s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4046108316
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       5894454757

SMART Error Log Version: 1
No Errors Logged

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

### Post by deadflowr on 2017-12-21
The important part is this:
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       79006672
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       60
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   067   060   030    Pre-fail  Always       -       17202753427
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8444
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       60
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   064   045    Old_age   Always       -       24 (Min/Max 23/24)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       6584
194 Temperature_Celsius     0x0022   024   040   000    Old_age   Always       -       24 (0 13 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       8349h+12m+11.900s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4046108316
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       5894454757
```
and the important part of that is the Raw Value field.
That's what your hard drives output is.
The output looks normal,,,, for a seagate barracuda.
(or a least from what I can see/read)

But maybe someone else can see something...

---

### Post by Yellow Pasque on 2017-12-21
I also don't see anything alarming. Seek error rate is high, but it seems that's not critical on its own: [https://kb.acronis.com/content/9107](https://kb.acronis.com/content/9107)
If you boot a LiveUSB/CD and use for a while, does the hanging still occur?
Have you tried memtest?
Are you monitoring temps to make sure your system isn't overheating?

---

### Post by Superdude_123 on 2017-12-21
I haven&#8217;t tried yet with a live disk, however, the system was stable when it ran under memtest (from grub menu) for 4-5 hours. The test showed zero errors. On the subject of over heating, i did check and the values were around 27-32 C, so all looks good there. 

I do have a post in general help that covers the kernel log if you wouldn&#8217;t mind chiming in.

---

### Post by leunam12 on 2017-12-22
Seagate drives always have those high numbers on seek error rate and read error rate. There is a formula to convert them to something understandable somewhere on the internet, search for "Seagate huge seek error rate".

---

