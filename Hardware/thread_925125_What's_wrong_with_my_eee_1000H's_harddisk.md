---
title: "What's wrong with my eee 1000H's harddisk?"
date: 2008-09-20
forum: Hardware
---

### Post by Olnex on 2008-09-20
I bought a new EEE 1000H, however, when I check the smart data, I got the followings:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST980811AS
Serial Number:    5LYB510R
Firmware Version: 3.ALC
User Capacity:    80,026,361,856 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep 21 00:02:36 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

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
  1 Raw_Read_Error_Rate     0x000f   117   100   006    Pre-fail  Always       -       123737460
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       36
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       774262
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       23
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       39
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   063   044   045    Old_age   Always   In_the_past 622919717
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       15
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       476
194 Temperature_Celsius     0x0022   037   056   000    Old_age   Always       -       37 (Lifetime Min/Max 0/22)
195 Hardware_ECC_Recovered  0x001a   085   065   000    Old_age   Always       -       185902832
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

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



Notice these items:
  1 Raw_Read_Error_Rate     0x000f   117   100   006    Pre-fail  Always       -       123737460
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       774262
190 Temperature_Celsius     0x0022   063   044   045    Old_age   Always   In_the_past 622919717
195 Hardware_ECC_Recovered  0x001a   085   065   000    Old_age   Always       -       185902832

these look strange, is there anything wrong with my harddisk? I used ubuntu 8.04.1 with Adamm's kernel: [http://forum.eeeuser.com/viewtopic.php?id=38030](http://forum.eeeuser.com/viewtopic.php?id=38030), when the system starts, I heard strange clicking noise which scared me, so I set hdparm -B 255.
This model used to use WinXP, I remembered it also has these problems.

---

### Post by Olnex on 2008-09-20
the command "smartctl -a /dev/sda | ECC" shows the ECC increases tooooo fast:

195 Hardware_ECC_Recovered  0x001a   082   065   000    Old_age   Always       -       188725177
hzxu@hzxu-laptop:~$ sudo smartctl -a /dev/sda | grep ECC
195 Hardware_ECC_Recovered  0x001a   082   065   000    Old_age   Always       -       188764833
hzxu@hzxu-laptop:~$ sudo smartctl -a /dev/sda | grep ECC
195 Hardware_ECC_Recovered  0x001a   082   065   000    Old_age   Always       -       188794934
hzxu@hzxu-laptop:~$ sudo smartctl -a /dev/sda | grep ECC
195 Hardware_ECC_Recovered  0x001a   082   065   000    Old_age   Always       -       188840501
hzxu@hzxu-laptop:~$ sudo smartctl -a /dev/sda | grep ECC
195 Hardware_ECC_Recovered  0x001a   082   065   000    Old_age   Always       -       188840787

---

### Post by IntuitiveNipple on 2008-09-20
That's perfectly normal and to be expected. It is reporting the time between ECC recoveries (automatic part of reading). The lower the value (close to zero) the worse it is. Those values look to be almost as high as they could be.

For reference:
```

$ sudo smartctl -a /dev/sda | grep ECC

195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       10730

$ sudo smartctl -a /dev/sda | grep ECC

195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       11815

$ sudo smartctl -a /dev/sda | grep ECC

195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       12994

```

---

### Post by aurelieng on 2008-09-29
I have the same problem here, any idea on how to remove this scary clicking noise ?

---

### Post by surfed on 2008-10-29
The clicking noise is your hd-heads parking. Seagate has aggressive values for that build into the drive, the idea is that when you move your eee around its saver to have the heads parked. Now the problem is that most likely you use a journaled filesystem with low commit values and/or you have tracker running and/or your logs are producing high output. All those things and others that access your HD cause the head to go out of park to write/read whatever. Currently i am using the command "sudo hdparm -B 254 /dev/sda" to bypass this,data gets cached and written when cache gets full, reducing disk access but upon sleep/hybernate it resets to default of the HD. I am researching a better way of solving this, most likely somwhere within the acpi scripts.

---

