---
title: "False SMART drive errors in BIOS"
date: 2013-01-20
forum: Hardware
---

### Post by mister_p_1998 on 2013-01-20
Hi All,
Switched on this morning and got a warning (From the BIOS) that SMART check is bad and drive should be backed up and replaced. I ran  a quick (2 mins) and full (4 1/2 hours) and they found no errors at all. Is the BIOS giving a false error? I've heard a borderline PSU can give a false SMART error msg.

Ubuntu Hardy

Heres the short test result.

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD154UI
Serial Number:    S1XWJ1KZ309608
Firmware Version: 1AG01118
User Capacity:    1,500,301,910,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Sun Jan 20 18:49:00 2013 GMT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection: 		 (19214) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (  33) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   068   068   011    Pre-fail  Always       -       10480
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1096
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       1
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       10833
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       12771
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       2
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1096
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   090   068   000    Old_age   Always       -       168230922
194 Temperature_Celsius     0x0022   085   067   000    Old_age   Always       -       15 (Lifetime Min/Max 0/3847)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       24921
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       1
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12771         -
# 2  Extended offline    Aborted by host               90%     12770         -
# 3  Short offline       Completed without error       00%     12769         -
# 4  Short offline       Completed without error       00%     12766         -
# 5  Extended offline    Aborted by host               00%     12766         -
# 6  Conveyance offline  Aborted by host               60%     12761         -
# 7  Extended offline    Aborted by host               90%     12760         -
# 8  Short offline       Completed without error       00%     12760         -

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

TIA
Steve

---

### Post by tgalati4 on 2013-01-20
Was the machine cold when booted?  It could be a slow spin up causing a temporary SMART error that is captured by BIOS.  Once the drive is spinning, then it passes the standard read/write and mechanical tests.  Back up your data regardless.  A slow spin up could be indication of incipient bearing failure.

Also, your drive might have buggy firmware.  Have you tried the following switches?

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

By my calculation, your drive has been spinning for 1.46 years, so it's possible there are some wear indicators that would trip a SMART warning.

---

### Post by mister_p_1998 on 2013-01-21
> **tgalati4 said:**
> Was the machine cold when booted?  It could be a slow spin up causing a temporary SMART error that is captured by BIOS.  Once the drive is spinning, then it passes the standard read/write and mechanical tests.  Back up your data regardless.  A slow spin up could be indication of incipient bearing failure.

Also, your drive might have buggy firmware.  Have you tried the following switches?

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

By my calculation, your drive has been spinning for 1.46 years, so it's possible there are some wear indicators that would trip a SMART warning.

Yes it was a cold boot, after a 2nd reboot it fired up fine with no smart error, I tried disconnecting my XP drive in case it was a psu issue, and it booted up fine cold with no smart warning, Im thinking it might be the PSU on the way out.

---

