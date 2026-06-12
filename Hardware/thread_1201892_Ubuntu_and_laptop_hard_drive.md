---
title: "Ubuntu and laptop hard drive"
date: 2009-07-01
forum: Hardware
---

### Post by flylehe on 2009-07-01
Hi,
I just heard that ubuntu might hurt laptop hard drive. So I try running "smartctl -a /dev/sda". Here is the output:
> 
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 4200.2 Series
Device Model:     ST9100822A
Serial Number:    3LG0PHW8
Firmware Version: 3.01
User Capacity:    100,030,242,816 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Jul  1 14:44:40 2009 EDT
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
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   054   049   034    Pre-fail  Always       -       153494981
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2107
  5 Reallocated_Sector_Ct   0x0033   099   099   036    Pre-fail  Always       -       54
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       264864705
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21549
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2161
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       2174
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1933553
194 Temperature_Celsius     0x0022   043   052   000    Old_age   Always       -       43 (0 4 0 0)
195 Hardware_ECC_Recovered  0x001a   054   049   000    Old_age   Always       -       153494981
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

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



According to some post online, by looking at Load_Cycle_Count and Temperature_Celsius, my hard drive seems not have much lifetime left. Is it really serious?

Thanks and regards!

---

