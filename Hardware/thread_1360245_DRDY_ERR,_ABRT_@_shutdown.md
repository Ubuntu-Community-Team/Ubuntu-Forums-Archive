---
title: "DRDY ERR, ABRT @ shutdown"
date: 2009-12-20
forum: Hardware
---

### Post by Tommy599 on 2009-12-20
Hey everyone!

I installed xubuntu 9.10 on this old pc (850Mhz, 384RAM, 20GB) and out of the several issues (login problems when I change resolution, no module loaded for parallel port) I encountered I couldn't solve this one: 


@ shutdown (either from the shutdown button or sudo shutdown now -P) I get this error:

```
[..]ata1.00:exception Emask 0x0 SAct 0x0 SEer 0x0 action 0x0
[..]ata1.00:cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
            res 51/04:00:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[..]ata1.00:status{DRDY ERR}
[..]ata1.00:error{ABRT}
[..]System halted.
```..and then the system just hangs there, no activity and I have to power it off or reset it manually. 


It does **NOT** occur if I press reboot or issue the following commands:  sudo reboot,  sudo shutdown now -r (system reboots normally),  sudo shutdown now. 


**dmesg | grep ata1.00**

```
[    1.300578] ata1.00: ATA-6: ST320410A, 3.39, max UDMA/100
[    1.300588] ata1.00: 39102336 sectors, multi 16: LBA 
[    1.316393] ata1.00: configured for UDMA/100
```**sudo smartctl -a /dev/sda **

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate U Series 6 family
Device Model:     ST320410A
Serial Number:    3FG1RKL5
Firmware Version: 3.39
User Capacity:    20,020,396,032 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 21 00:26:51 2009 EET
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
data collection:          ( 420) seconds.
Offline data collection
capabilities:              (0x1d) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Abort Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  22) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   074   059   025    Pre-fail  Always       -       49306081
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       814
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       81819029846
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6481
 10 Spin_Retry_Count        0x0013   100   083   097    Pre-fail  Always   In_the_past 0
 12 Power_Cycle_Count       0x0032   092   092   020    Old_age   Always       -       8805
194 Temperature_Celsius     0x0022   039   050   000    Old_age   Always       -       39
195 Hardware_ECC_Recovered  0x001a   100   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      6481         -
# 2  Short offline       Completed without error       00%      6480         -

Device does not support Selective Self Tests/Logging
```The smartctl test revealed no errors, I ran a test from the Ultimate boot CD, that didn't detect any bad sectors or anything either. 

I tried booting with noapic and acpi=off, but the error is still there. Yes, I know, it's an old drive (about 7 years) but still, is there any way to at least make the error notification go away?   It's annoying to have to power off the machine manually.  Or maybe somehow simulate a reboot but then power off? (grasping at straws here, been squeezing my brains over this all day...yes, that's how I spent my Sunday)

Any help is greatly appreciated. Thank you!

UPDATE: tried with a live CD, does the exact same thing @ shutdown.

---

### Post by awilkins on 2009-12-31
There are "poweroff" kernels out there that just .. power off your machine when they start.

I use one for my MythTV box because the BIOS wake-up time only gets initialized after a reboot, so it needs to reboot and then shut down to configure the time it should wake up for it's next recording. You need to configure the grub menu to reset the default start item before it boots this kernel and it all starts normally next time.

I'm being hit with this on my dear ol' Mum's system.. an older machine with a cheap motherboard. It works just fine (in Windows 2000 and in Karmic), and she understands the workaround (hold down the power button until the power drops), but it's annoying.

---

### Post by Tommy599 on 2010-01-01
Sounds complicated.

So it's safe to do it like this, manually shutting down? It says the system is halted so it should be safe. I won't be on hand to solve problems in a few days, that's why I need to know if it's safe to use this workaround.

---

