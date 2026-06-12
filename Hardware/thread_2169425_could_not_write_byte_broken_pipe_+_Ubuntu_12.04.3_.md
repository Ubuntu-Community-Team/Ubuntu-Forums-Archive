---
title: "could not write byte: broken pipe + Ubuntu 12.04.3 LTS"
date: 2013-08-22
forum: Hardware
---

### Post by Hrakleaz on 2013-08-22
Its time to change my HDD, or its nothing at the moment?

Until now, i had one "could not write byte: broken pipe", before the login page, and i couldn't log in. I format my hdd and i'm fine now.

> n~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

```
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6
Device Model:     ST9320325AS
Serial Number:    5VD1T91V
LU WWN Device Id: 5 000c50 01bc86f06
Firmware Version: 0010LVM1
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Aug 22 09:42:25 2013 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  95) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103b)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   034    Pre-fail  Always       -       34064166
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3172
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       245547515
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       222079873985200
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3129
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       4295033013
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   056   037   045    Old_age   Always   In_the_past 44 (1 142 44 28)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       122
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       227
193 Load_Cycle_Count        0x0032   078   078   000    Old_age   Always       -       45962
194 Temperature_Celsius     0x0022   044   063   000    Old_age   Always       -       44 (0 4 0 0)
195 Hardware_ECC_Recovered  0x001a   057   049   000    Old_age   Always       -       34064166
196 Reallocated_Event_Count 0x000f   088   088   030    Pre-fail  Always       -       10734 (17427, 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

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

### Post by nns2006 on 2014-02-15
It is also affecting me. In my case, I installed a so-called update[http://www.omgubuntu.co.uk/2014/02/ubuntu-12-04-4-released-new-kernel]("http://www.omgubuntu.co.uk/2014/02/ubuntu-12-04-4-released-new-kernel") using "sudo apt-get install linux-generic-lts-saucy xserver-xorg-lts-saucy" and rebooted. Since then I have not been able to log into Ubuntu.
Hope somebody will help.

---

