---
title: "dma errors - harddrive soon crashing ?"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by th0mas on 2007-02-22
I had a lot of freezes the last weeks.
And I think it coincides with my dist-upgrade to edgy...

Here is the problem. I can use my laptop correctly for several hours, then I have a weird freeze and I can hear some weird noises around the harddrive area. It does a "click" every  2 seconds. It usually lasts 15 seconds. In the meantime, one application is not responding (sometimes Thunderbird, sometimes OOo or firefox, mousepad...) but the mouse is responding correctly...

Here my /var/log/syslog :

```

Feb 22 22:29:59 localhost kernel: [17217736.148000] hda: dma_timer_expiry: dma status == 0x21
Feb 22 22:30:12 localhost kernel: [17217746.148000] hda: DMA timeout error
Feb 22 22:30:12 localhost kernel: [17217746.148000] hda: dma timeout error: status=0xd0 { Busy }
Feb 22 22:30:12 localhost kernel: [17217746.148000] ide: failed opcode was: unknown
Feb 22 22:30:12 localhost kernel: [17217746.148000] hda: DMA disabled
Feb 22 22:30:12 localhost kernel: [17217748.740000] ide0: reset: success

```

I have a sony vaio k115s with a Samsung 80Go harddrive I bought 18 months ago.
I don't know how to decipher these errors.
Do you think my harddrive is slowly dying ?
Help !

---

### Post by redman0570 on 2007-02-22
The clicking is the problem.  The clicking is a sign the HD is going bad.

---

### Post by th0mas on 2007-02-22
what do you think of these S.M.A.R.T. values ?

```

smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG MP0804H
Serial Number:    S042J10Y676304
Firmware Version: UE100-14
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Fri Feb 23 00:11:38 2007 CET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 245)	Self-test routine in progress...
					50% of test remaining.
Total time to complete Offline 
data collection: 		 (4800) seconds.
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
recommended polling time: 	 (  80) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   033   025    Pre-fail  Always       -       4288
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2319
  5 Reallocated_Sector_Ct   0x0033   100   100   011    Pre-fail  Always       -       2
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       874844
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       811
191 G-Sense_Error_Rate      0x0012   096   096   000    Old_age   Always       -       48768
194 Temperature_Celsius     0x0022   064   040   000    Old_age   Always       -       58
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       30783876
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x000a   100   100   051    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x0012   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0012   099   099   000    Old_age   Always       -       1464
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1285002
255 Unknown_Attribute       0x000a   100   100   051    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 4
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

Error 4 occurred at disk power-on lifetime: 5524 hours (230 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 c1 4c 75 e1  Error: ICRC, ABRT 8 sectors at LBA = 0x01754cc1 = 24464577

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c1 4c 75 e1 00      00:01:37.563  READ DMA
  ca 00 08 a1 6f 19 e1 00      00:01:36.750  WRITE DMA
  ca 00 48 59 6f 19 e1 00      00:01:36.750  WRITE DMA
  ca 00 08 89 01 6c e1 00      00:01:36.750  WRITE DMA
  ca 00 08 91 94 69 e1 00      00:01:36.750  WRITE DMA

Error 3 occurred at disk power-on lifetime: 5524 hours (230 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 40 f1 58 73 e1  Error: ICRC, ABRT 64 sectors at LBA = 0x017358f1 = 24336625

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f1 58 73 e1 00      00:01:28.250  READ DMA
  ca 00 08 61 6c 19 e1 00      00:01:26.438  WRITE DMA
  ca 00 d8 89 6b 19 e1 00      00:01:26.438  WRITE DMA
  ca 00 00 89 6a 19 e1 00      00:01:26.438  WRITE DMA
  ca 00 08 46 45 13 e2 00      00:01:26.438  WRITE DMA

Error 2 occurred at disk power-on lifetime: 5524 hours (230 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 10 11 66 c5 e1  Error: ICRC, ABRT 16 sectors at LBA = 0x01c56611 = 29713937

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 10 11 66 c5 e1 00      00:01:19.063  READ DMA
  c8 00 10 01 66 c5 e1 00      00:01:19.063  READ DMA
  c8 00 08 b1 4a 96 e1 00      00:01:19.000  READ DMA
  c8 00 10 29 35 96 e1 00      00:01:19.000  READ DMA
  c8 00 08 61 2e 95 e1 00      00:01:19.000  READ DMA

Error 1 occurred at disk power-on lifetime: 5524 hours (230 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 59 2b e5 e1  Error: ICRC, ABRT 8 sectors at LBA = 0x01e52b59 = 31796057

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 59 2b e5 e1 00      00:01:18.688  READ DMA
  c8 00 10 e1 65 c5 e1 00      00:01:18.625  READ DMA
  c8 00 08 39 eb c4 e1 00      00:01:18.625  READ DMA
  c8 00 08 59 2b c1 e1 00      00:01:18.625  READ DMA
  c8 00 08 91 4d c1 e1 00      00:01:18.625  READ DMA

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
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

Do i need to worry ?
My computer is offline 10% of the time, I bought this harddrive about 18 months ago

---

