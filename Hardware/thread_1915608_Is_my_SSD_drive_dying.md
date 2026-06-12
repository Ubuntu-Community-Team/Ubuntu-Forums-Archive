---
title: "Is my SSD drive dying?"
date: 2012-01-26
forum: Hardware
---

### Post by hamoid on 2012-01-26
Hi,

I've replaced the HD on my laptop with a OCZ-VERTEX3 SSD half year ago. Things have been working fine. 

Two or three times during the last week my drive suddenly disappeared. The top bar in Ubuntu 11.10 was empty and I could not access any folders, start a terminal or even shut down the computer.

One time it happened while playing a movie in VLC, today it happened while saving a file using SooperLooper (an audio looping program)

I could press CTRL+ALT+F2, but when I tried logging in I saw:
[ 2467.951226 ] EXT4-fs (sda1): previous I/O error to superblock detected
[ 2467.951300 ] EXT4-fs error (device sda1): ext4_find_entry:934: inode #2490369: comm getty: reading directory listing iblock 0

After rebooting I tried: sudo smartctl --all /dev/sdX
which I can't really interpret. This is the output:

```
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-15-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     OCZ-VERTEX3
Serial Number:    OCZ-4GD??????????
LU WWN Device Id: 5 e83a97 f0d4ebb49
Firmware Version: 2.11
User Capacity:    60,022,480,896 bytes [60.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 revision 3
Local Time is:    Thu Jan 26 19:36:19 2012 EET
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
data collection: 		( 2097) seconds.
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
SCT capabilities: 	       (0x0021)	SCT Status supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   120   050    Pre-fail  Always       -       0/0
  5 Retired_Block_Count     0x0033   100   100   003    Pre-fail  Always       -       0
  9 Power_On_Hours_and_Msec 0x0032   098   098   000    Old_age   Always       -       2134h+10m+19.600s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       280
171 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       1
177 Wear_Range_Delta        0x0000   000   000   000    Old_age   Offline      -       0
181 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   128   129   000    Old_age   Always       -       128 (Min/Max 127/129)
195 ECC_Uncorr_Error_Count  0x001c   100   100   000    Old_age   Offline      -       0/0
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       0
201 Unc_Soft_Read_Err_Rate  0x001c   100   100   000    Old_age   Offline      -       0/0
204 Soft_ECC_Correct_Rate   0x001c   100   100   000    Old_age   Offline      -       0/0
230 Life_Curve_Status       0x0013   100   100   000    Pre-fail  Always       -       156654637154404
231 SSD_Life_Left           0x0013   100   100   010    Pre-fail  Always       -       0
233 SandForce_Internal      0x0000   000   000   000    Old_age   Offline      -       497
234 SandForce_Internal      0x0032   000   000   000    Old_age   Always       -       322
241 Lifetime_Writes_GiB     0x0032   000   000   000    Old_age   Always       -       322
242 Lifetime_Reads_GiB      0x0032   000   000   000    Old_age   Always       -       1116

SMART Error Log not supported
SMART Self-test Log not supported
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

My question are:

1. Did some kernel update cause this?
2. Is maybe my laptop battery failing while the SSD uses too much power?
3. Is this how SSD drives die?
[S]4. Is the drive really 128 degrees celsius? That sounds like a lot. The fan is not on all the time...[/S] The temperature reading is not valid.
5. Anything I can do, except backups? I just did this: [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/) Now the computer is even faster. Too bad I did not discover that half year ago.

After a reboot things are fine, but now I'm worried about when will this happen again. The file I tried to save when it happened last is gone. Disappeared.

---

### Post by BC59 on 2012-01-26
I don't have SSD experience, so I checked wikipedia for details. As I see, the temperature of SSD is lower than a HDD. There is something strange here.
[http://en.wikipedia.org/wiki/Solid-state_drive](http://en.wikipedia.org/wiki/Solid-state_drive)

---

### Post by hamoid on 2012-01-26
After reading a bit, I think the high temperature is a false reading. It's never changing. Probably the software is not able to read the correct temperature.

---

### Post by aldorgan on 2012-01-26
There are no temperature sensors on a ssd, so there are no program that can read it, it is just a number it does't mean anything.

---

### Post by jonnyboysmithy on 2012-01-26
May this be temperature related? I had bad superblock errors and I/O errors when my laptop got to hot. I figured that one out because it kept happening when I was using it on the bed :-\":biggrin: (the cpu was ok but the ram was waay to hot)

---

### Post by Grenage on 2012-01-27
> **hamoid said:**
> 1. Did some kernel update cause this?

It's possible, but it doesn't seem that likely

> **hamoid said:**
> 2. Is maybe my laptop battery failing while the SSD uses too much power?

Unlikely; I'd expect the whole laptop to power down - SSDs use far less power than mechanical drives.

> **hamoid said:**
> 3. Is this how SSD drives die?

If hardware died only one way, life would sure be simple.

> **hamoid said:**
> 5. Anything I can do, except backups?

Not really, back everything up and keep it backed up.  Keep a close eye on it, move a load of data around, let it idle for an hour, stream a movie, et cetera.  At 6 months old, it's in warranty, so that's something.

---

### Post by stefangr1 on 2012-01-27
Make sure there are no bad contacts. The alst time I had problems with a harddrive, it was also working well now and then, to then suddenly fail. That was due to a somewhat loose connection.

---

### Post by hamoid on 2012-01-30
Thanks a lot for your replies. I'll keep everything backed up and my fingers crossed while I'm not typing :)

---

### Post by BC59 on 2012-01-30
After a lot of reading, because I like to buy a SSD for myself, looks like the SSDs are almost unbreakable (comparing to HDDs). So in your case, just check around SSD, means look for failed cables, connections etc and not for the SSD itself, which is very unlikely to have problems.

---

### Post by Grenage on 2012-01-30
> **BC59 said:**
> After a lot of reading, because I like to buy a SSD for myself, looks like the SSDs are almost unbreakable (comparing to HDDs). So in your case, just check around SSD, means look for failed cables, connections etc and not for the SSD itself, which is very unlikely to have problems.

They're not vulnerable to mechanical failure, but like any computer component, can die at the drop of a hat.

---

