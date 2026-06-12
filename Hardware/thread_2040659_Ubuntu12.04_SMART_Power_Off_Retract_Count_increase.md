---
title: "Ubuntu12.04: SMART Power Off Retract Count increases with every shutdown or STR cycle"
date: 2012-08-11
forum: Hardware
---

### Post by utnubulx on 2012-08-11
Hi, 

about 8 weeks ago I instlled a 750GB 2.5" seagate hdd in my laptop (technical details: see below). Now I realized that the SMART parameter "Power Off Retract Count" increases every time I reboot the laptop or put the laptop into suspend-to-RAM mode. The counter already reached 423 while start-stop count is at 320 and power-cycle-count at 159.  I don't think this is intended (emergency unload stresses the hdd more than a clean unload+power off) and may cause trouble with the hdd in the long run.

Is there a possibility to issue an unload command before the system powers down when shutting the system down?
Are there any log files I could look at to see whether there are some issues with the controller talking to the hdd, etc.?

I don't know whether the issue is related to the new hdd or whether the same happened also for the old drive. I don't have access to the old drive any more...

I hope someone can provide a hint what is going wrong with my laptop.
Thanks! [B]
--[utnubulx]("http://ubuntuforums.org/member.php?u=1718532")

[/B]
=======================================
here're the promised technical details:
=======================================
Laptop: Acer Extensa 5630EZ

SATA controller: lspci | grep SATA
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)

Ubuntu version:
Lubuntu 12.04
/etc/issue:
Ubuntu 12.04 LTS \n \l

kernel:
3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

SMART data: output of smartctl --all /dev/sda 

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-27-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     ST9750422AS
Serial Number:    5WS45xxxxxxxxxxxxx
LU WWN Device Id: xxxxxxxxxxxxxxx
Firmware Version: 0001BSM1
User Capacity:    750.156.374.016 bytes [750 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat Aug 11 16:26:49 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

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
recommended polling time:      ( 142) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       214405552
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       320
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   063   060   030    Pre-fail  Always       -       2610259
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       428
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       159
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   047   045    Old_age   Always       -       46 (Min/Max 27/46)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       423
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       663
194 Temperature_Celsius     0x0022   046   053   000    Old_age   Always       -       46 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   119   099   000    Old_age   Always       -       214405552
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       28063316312485
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       243057881
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2018428344

---

