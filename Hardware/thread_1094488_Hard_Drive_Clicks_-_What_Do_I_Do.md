---
title: "Hard Drive Clicks - What Do I Do?"
date: 2009-03-12
forum: Hardware
---

### Post by zak89 on 2009-03-12
I am running Ubuntu Hardy on a Dell Latitude D531. Just today the hard drive started clicking. It usually click for several seconds, then stops for maybe a minute or too, then starts up again. Is my hard drive failing? Most of my data is backed up (and I am copying off the rest right now). Is there anything I can do to save the drive?

---

### Post by partsdale on 2009-03-12
I'm not any kind of expert, but I believe backing up is a prudent move. I think you described a pretty classic symptom of a dying hard drive.

Good luck

---

### Post by JBA2337 on 2009-03-12
Clicking is a bad sign that the drive may be failing. First, it would be a good idea to test your hard drive. There are many different free hard drive test programs that you can find on the Internet. If you bought the hard drive, it most likely came with a diagnostic program. Write down the drive's model no. and serial no. Go to the manufacturer's web site and determine if the drive is still in warranty.

JBA

---

### Post by zak89 on 2009-03-13
Do you guys have any hints on a good hard driver testing app for linux? I tried smart, and it seems to tell me everything's fine:

```
**root@silverchalice-mobile:~#** smartctl -i /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.2
Device Model:     ST9120823AS
Serial Number:    5NJ03ESZ
Firmware Version: 3.ADB
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Mar 13 09:42:14 2009 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

**root@silverchalice-mobile:~#** smartctl -s on -d ata /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

**root@silverchalice-mobile:~#** smartctl -d ata -H /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

**root@silverchalice-mobile:~#** smartctl -d ata -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.2
Device Model:     ST9120823AS
Serial Number:    5NJ03ESZ
Firmware Version: 3.ADB
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Mar 13 09:42:30 2009 CDT
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
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.
SCT capabilities: 	       (0x0035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   098   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1810
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   052   052   030    Pre-fail  Always       -       2302195206065
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3614
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1757
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   098   098   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   062   049   045    Old_age   Always       -       38 (Lifetime Min/Max 22/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1461
193 Load_Cycle_Count        0x0022   012   012   000    Old_age   Always       -       177988
194 Temperature_Celsius     0x001a   038   051   000    Old_age   Always       -       38 (0 12 0 0)
195 Hardware_ECC_Recovered  0x0012   073   062   000    Old_age   Always       -       181070691
197 Current_Pending_Sector  0x0010   092   092   000    Old_age   Offline      -       164
198 Offline_Uncorrectable   0x003e   092   092   000    Old_age   Always       -       164
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0
254 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      2730         -
# 2  Short offline       Completed without error       00%      2729         -
# 3  Short offline       Completed without error       00%         2         -
# 4  Short offline       Completed without error       00%         1         -

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

Do you guys see anything wrong with the above output?

I'm still getting the clicking sound.

---

