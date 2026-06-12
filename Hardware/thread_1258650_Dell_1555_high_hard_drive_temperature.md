---
title: "Dell 1555 high hard drive temperature"
date: 2009-09-05
forum: Hardware
---

### Post by andrek on 2009-09-05
Hi!

I'm experiencing high hard drive temps on my new Dell Studio 1555. It is WDC WD2500BEVT-75ZCT2 and, as GNOME Sensors Applet indicates, its temperature goes even up to 49 when idle. Is that safe? System Monitor Applet shows that hard drive's usage is very low, though its temperature is pretty high.

sudo smartctl -a gives me :

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXE409RS4433
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Sep  5 16:41:05 2009 CEST
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
data collection: 		 (7800) seconds.
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
recommended polling time: 	 (  93) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   187   186   021    Pre-fail  Always       -       1616
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       146
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       362
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       144
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       35
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5503
194 Temperature_Celsius     0x0022   101   092   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       331
241 Unknown_Attribute       0x0032   171   171   000    Old_age   Always       -       29197113599841
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       1242114678

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -

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

Thanks for any piece of advice.

---

### Post by Gizenshya on 2009-09-05
according to the manufacturer...

Operating : -0° C to 60° C

Non-operating (aka while off) : -40° C to 65° C

Dell 1555 doesn't mean anything actually.  They make cases and put stuff together, but the hardware is made by other companies.  Some of those products are "re-branded" (for instance, an Dell ASDF1000 or HP ASDF1000 which is actually an Adaptec or some other company's product with different plastic on it).  The hard drive is a Western Digital "WDC WD2500BEVT-75ZCT2"  and looking at the Western Digital website gives the design operating ranges.

So, in short, no.  That temperature is within the design specs of the drive.  However... that printout also shows the max reading, which is significantly higher than design.  Computer manufacturers like HP, Dell, Compaq, etc. are norotious for poor ventillation on their hard drive compartments.  I have yet to see one that does not regularly exceed operating temps for its hard drive.  If I were you, I would look for a hard drive cooler or maybe just installing a fan where it blows on the circuit board of the drive.  I haven't looked up that Dell model, but even on the lower end models (especially the older ones) they have at least one extra fan hookup on the motherboard.  A little $2 fan would do just fine (that's what I use).

I've had hard drives fail before in my HP machines because of heat, but not after installing an extra fan that used to be a case fan in an older computer.

Also, how often do you dust the inside of your case?  You should do it often, at least once a week if you use it daily.  Go buy one of those compressed air cans and you're set.  Don't use regular compressed air, because moisture condenses inside and could short your board.

---

### Post by andrek on 2009-09-05
Thanks for the reply.

What is this "max reading" thing about? Where did you exactly get it from? Is it serious enough to start worrying about it? Is this somehow related to the "Load cycle count" case that was terrifying laptop users about a year ago?

As for the temperature, you may have a good point. However, I'm currently on Windows 7 and hwmonitor shows that hd's temp is 43 C now, so it's about ~5 C degrees lower than on Ubuntu. But that's not a big deal, I guess.

---

