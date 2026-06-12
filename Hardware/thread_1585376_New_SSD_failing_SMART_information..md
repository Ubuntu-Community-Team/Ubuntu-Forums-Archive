---
title: "New SSD failing? SMART information."
date: 2010-09-30
forum: Hardware
---

### Post by Glaucous on 2010-09-30
I just installed a Corsair Sandforce 60 SSD in my computer running Ubuntu 10.04 x64. I installed / on the SSD.
There aren't any problems I notice myself, but the SMART status worries me.

```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     Corsair CSSD-F60GB2
Serial Number:    10336518580009990133
Firmware Version: 1.1
User Capacity:    60,022,480,896 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x28
Local Time is:    Thu Sep 30 18:33:07 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x02)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (   0) seconds.
Offline data collection
capabilities: 			 (0x7f) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Abort Offline collection upon new
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  48) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   102   102   050    Pre-fail  Always       -       5065649
  5 Reallocated_Sector_Ct   0x0033   096   096   003    Pre-fail  Always       -       384
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       86234353369091
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
171 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
172 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
174 Unknown_Attribute       0x0030   000   000   000    Old_age   Offline  FAILING_NOW 11
177 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
177 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
181 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
181 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
181 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
182 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
182 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
182 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
187 Reported_Uncorrect      <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
187 Reported_Uncorrect      <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
194 Temperature_Celsius     <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
194 Temperature_Celsius     0x0022   025   036   000    Old_age   Always       -       25 (Lifetime Min/Max 0/36)
194 Temperature_Celsius     <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
195 Hardware_ECC_Recovered  <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
195 Hardware_ECC_Recovered  0x001c   102   102   003    Old_age   Offline      -       5065649
195 Hardware_ECC_Recovered  <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
196 Reallocated_Event_Count <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
196 Reallocated_Event_Count 0x0033   100   100   010    Pre-fail  Always       -       0
196 Reallocated_Event_Count <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
231 Temperature_Celsius     <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
231 Temperature_Celsius     0x0013   093   093   000    Pre-fail  Always       -       1
231 Temperature_Celsius     <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
233 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
233 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 128
233 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
234 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
234 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 192
234 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
241 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
241 Unknown_Attribute       0x0032   000   000   000    Old_age   Always   FAILING_NOW 192
241 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
242 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
242 Unknown_Attribute       0x0032   000   000   000    Old_age   Always   FAILING_NOW 128
242 Unknown_Attribute       <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
  0 Unknown_Attribute       <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA

Error SMART Error Log Read failed
Smartctl: SMART Error Log Read Failed
Error SMART Error Self-Test Log Read failed
Smartctl: SMART Self Test Log Read Failed
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

Is this something I should worry about?

---

### Post by droodlol on 2010-10-21
SSDs have only a few smart attributes, they dont need the same params what hdds do.
I wouldnt worry about it but dont forget the cheap MLC SSDs (lowend ones what you probably buy) can die within an unknown short time period. 

I killed 3 so far from the crap "Silicon Power 32Gb SATA MLC ". This brand is a major ****. 

The only trustworthy SSDs are SLCs which cost 2-3 times more. Never trust in MLC SSDs, always backup your stuff.

---

### Post by P4man on 2010-10-21
I was about to post not to worry about the Unknown_Attributes, but the Raw_Read_Error_Rate and Reallocated_Sector_Ct does seem believable and worrisome. Does the value go up over time?

---

### Post by psusi on 2010-10-21
See if there is a firmware update for the drive because the stuff in there now is brain damaged.

---

### Post by P4man on 2010-10-21
Most of the attributes that are recognised seem certainly possible and credible; Temperature of 25C with maximum of 36C seems believable, as does the power cycle count for a new drive. Maybe the relocated sector count and rawread error values are not only accurate but also normal for an SSD (and the firmware handles that), but I wouldnt be too quick to discard it.  Maybe see if corsair has an app to test the drive?

---

### Post by JPorter on 2010-10-21
The most likely explanation is that the SMART information being reported is not correct. Half the attributes being reported in the SMART data block are being parsed as "Unknown_Attribute", so it's just as likely that the data being reported for the "guessed" fields is not correct.

I would make sure you're on the latest drive firmware, run the factory diagnostics to be sure.  If it comes back all OK, then just turn off SMART reporting, and use the drive without SMART until you have a reason to suspect there may be a problem.  SMART is really designed for spinning platter hard drives anyway, you're never going to get a real proactive failure notice on solid state chips.

---

### Post by chrischan on 2010-10-22
Same drive, same os, same problem. Just to let you know its not specific to your drive. I decided for myself that the ssd is ok and smart is wrong, but without any evidence except that everything seems to work fine.

---

### Post by GB_Joe on 2010-12-01
Same drive on Ubuntu 10.10, not getting any read error rate flags but a whole heap of "no description for attribute" warnings. I'm guessing there's nothing to worry about but will post back if the situation changes.

Do you think I should be posting a bug report about this? A bog-standard fresh install with new hardware shouldn't come up with scary messages telling you your hard drive is failing unless it's actually true...

---

