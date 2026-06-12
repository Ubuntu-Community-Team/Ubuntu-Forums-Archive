---
title: "Hard drive making odd noises when being written to"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by Nate7679 on 2007-05-06
I've noticed that when I'm extracting an archived file to the hard drive in my laptop, it starts to make high pitched squeaking noises. They aren't loud, but they aren't normal hard drive sounds either. I haven't noticed it any other time than when i've unzipped something, so i'm pretty sure its the writing to the drive that does it. I just started noticing this today, so what should I do? I'm going to start by clearing off stuff from my hard drive, because its 95% percent full, but I don't think that could cause it to make these noises. I also might call my computer vendor to see what they recommend. But is there anything I should check to diagnose the problem? Is this something to be getting worried over?

If it helps, I've encluded a snapshot of my hard drive partitions.

Thanks for your help

---

### Post by bukwirm on 2007-05-06
Make sure you back up your files :).

How old is the drive?
And if it's still under warranty, I would talk to the vendor.

---

### Post by joe.turion64x2 on 2007-05-06
I don't want to scare you my friend but your hard drive might fail soon. Make sure you back up all important information and, if it is still under warranty, claim it.

---

### Post by Nate7679 on 2007-05-07
I have all of my important files stored on external hard drives but I'll still back up some of the files on this hard drive. As for my Ubuntu partitions, I can't write to NTFS drives from ubuntu, what should I do to enable this? 

The hard drive itself is only about one to one and a half years old, but I've formated various partitions atleast 5 times, which probably isnt good for it.

---

### Post by tgalati4 on 2007-05-07
sudo apt-get install smartmontools
smartctl -s /dev/hdb
smartctl -t short /dev/hdb
smartctl -l selftest /dev/hdb
smartctl -a /dev/hdb

Note the total number of power-on hours, temperature, and any errors or marginal conditions.

---

### Post by Nate7679 on 2007-05-07
I installed smartctl correctly and this is what I got from the commands:

smartctl -s /dev/hdb

=======> INVALID ARGUMENT TO -s: /dev/hdb
=======> VALID ARGUMENTS ARE: on, off <=======

And when inputting these

smartctl -t short /dev/hdb
smartctl -l selftest /dev/hdb
smartctl -a /dev/hdb

I got

Smartctl open device: /dev/hdb failed: No such file or directory

---

### Post by tgalati4 on 2007-05-07
Try:

man smartctl

smartctl -s on /dev/hdb  

You have to turn SMART on first otherwise the other commands won't work.

Sorry for the brainfart.

---

### Post by Nate7679 on 2007-05-07
"man smartctl" opens up a text document, but I can't find out how to put it in SMART mode.

also, ntfs-config, the program that I got, only allows me to write to my NTFS formatted windows partition, not my NTFS formatted external drives. I need to be able to do this if I am to back up my ubuntu, so is there other software I should try or other settings I should change?

---

### Post by futz on 2007-05-07
> **Nate7679 said:**
> but I've formatted various partitions at least 5 times, which probably isn't good for it.
Why would you think formatting is bad for the drive? That's what they're made for. Doesn't hurt a thing. Do it as many times as you want.

---

### Post by Wiebelhaus on 2007-05-07
Run S.M.A.R.T diags on the drive.....yea , you should back up.

---

### Post by Nate7679 on 2007-05-07
> **futz said:**
> Why would you think formatting is bad for the drive? That's what they're made for. Doesn't hurt a thing. Do it as many times as you want.

I dunno, I'm just paranoid about my hard drives. I've heard too many horror stories of them failing, and I don't want that happening to any of my drives.

---

### Post by tgalati4 on 2007-05-07
sudo smartctl -s on /dev/hdb

This will enable SMART on the drive, assuming hdb is the drive that you are interested in.

The manual pages (man smartctl) has several examples if you page through it (using the spacebar and q to quit)

---

### Post by Nate7679 on 2007-05-07
I tried this and it also didn't work. Ill try looking through that document again though.

---

### Post by tgalati4 on 2007-05-08
Is /dev/hdb the correct device?

What was the error message?

---

### Post by Nate7679 on 2007-05-12
Okay, so I am now able to write to external NTFS formatted drives and I have backed up my ubuntu. The bad news is that the hard drive definitely makes more noise under ubuntu, and sony won't fix it "unless it fails or there are error messages"

So its working fine for right now aside from the noise, and if it fails they'll fix it.

---

### Post by arijarot on 2007-06-05
My hd has also started making a strange static, almost grinding sound... I ran ```
sudo smartctl /dev/hda2 -H
``` with results ```
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```
 but I don't understand these results ```
sudo smartctl /dev/hda2 -a

``` with results ```
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     IBM/Hitachi Deskstar GXP-180 family
Device Model:     IC35L060AVV207-0
Serial Number:    VNVB02G2GS3TYV
Firmware Version: V22OA66A
User Capacity:    60,000,000,000 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a
Local Time is:    Tue Jun  5 23:10:07 2007 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (1452) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  24) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   060    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   154   154   050    Pre-fail  Offline      -       231
  3 Spin_Up_Time            0x0007   122   122   024    Pre-fail  Always       -       156 (Average 114)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1111
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       26822
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1108
192 Power-Off_Retract_Count 0x0032   099   099   050    Old_age   Always       -       1275
193 Load_Cycle_Count        0x0012   099   099   050    Old_age   Always       -       1275
194 Temperature_Celsius     0x0002   148   148   000    Old_age   Always       -       37 (Lifetime Min/Max 18/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short captive       Completed without error       00%     18279         -
# 2  Short captive       Completed without error       00%      5412         -
# 3  Short offline       Completed without error       00%         0         -

Device does not support Selective Self Tests/Logging

```

Any interpreters? :) (specifically sections "Vendor Specific SMART Attributes with Thresholds:" [e.g., old age (?) or pre-fail (?)] and "SMART Self-test log structure revision number 1")

EDIT: if PASSED, why the [new] strange noise?

---

### Post by tgalati4 on 2007-06-06
Those Hitachi's are called DeathStars for a reason.  Items of interest:  Power On hours:  97 good, 22,000 hours is bad.  Temperature 37 C is good, 65 C is bad.  Any other errors will get flagged and logged.  As drives get old, spin-up times get longer and this will also get logged.  Remember SMART only catches perhaps 2/3's of the failure scenarios.  The other 1/3 are spontaneous--without notice.

There are some quiet parameters that you can try:

man hdparm

for some ideas or search the forums for what others have done.

If this is a 7,200 rpm or 10k rpm drive, then they are noisy by design.  You wouldn't notice the noise in a server room.

Good luck.

---

### Post by arijarot on 2007-06-06
> **tgalati4 said:**
> Those Hitachi's are called DeathStars for a reason.  Items of interest:  Power On hours:  97 good, 22,000 hours is bad.  Temperature 37 C is good, 65 C is bad.  Any other errors will get flagged and logged.  As drives get old, spin-up times get longer and this will also get logged.  Remember SMART only catches perhaps 2/3's of the failure scenarios.  The other 1/3 are spontaneous--without notice.

There are some quiet parameters that you can try:

man hdparm

for some ideas or search the forums for what others have done.

If this is a 7,200 rpm or 10k rpm drive, then they are noisy by design.  You wouldn't notice the noise in a server room.

Good luck.

no, I'm pretty sure it's 5400 and its never made any noise before, just recently. could it just be "old age," as it >5yrs old?

EDIT: I just remembered too: I recently opened the tower... could it be that the drive got moved accidental and is "vibrating" in the case because it's not seated properly?

---

### Post by xlingk on 2007-06-06
I once had a hard drive make a loud high pitched sound when it was being written to / read from. it didn't make it when the system was idle. after i reset it, it did it all the time. i swapped out the h/d then  i took  it apart and what i found out was the barings in side were dry. 

just my two cents.

---

### Post by arijarot on 2007-06-06
> **xlingk said:**
> I once had a hard drive make a loud high pitched sound when it was being written to / read from. it didn't make it when the system was idle. after i reset it, it did it all the time. i swapped out the h/d then  i took  it apart and what i found out was the barings in side were dry. 

just my two cents.

OK, this makes sense... what did you do to lubricate[?] the bearings? and for that matter, what are the bearings in a hd, as I'm only familiar with bearings in my rollerblades ;)

EDIT: the noise is not loud and high pitched, it's more of a low rumbling sound...

---

### Post by joe.turion64x2 on 2007-06-07
> **tgalati4 said:**
> Those Hitachi's are called DeathStars for a reason.  Items of interest:  Power On hours:  97 good, 22,000 hours is bad.  Temperature 37 C is good, 65 C is bad.  Any other errors will get flagged and logged.  As drives get old, spin-up times get longer and this will also get logged.  Remember SMART only catches perhaps 2/3's of the failure scenarios.  The other 1/3 are spontaneous--without notice.

There are some quiet parameters that you can try:

man hdparm

for some ideas or search the forums for what others have done.

If this is a 7,200 rpm or 10k rpm drive, then they are noisy by design.  You wouldn't notice the noise in a server room.

Good luck.
I did not know that Hitachi drive's nick name. My laptop's original hard drive was a Hitachi one (120GB, 4200RPM) and was somewhat noisy (at least it is more than my current Fujitsu at 5400RPM). I had to replace the drive because Linux once discovered some unreadable sectors somewhere in the middle of it, then the MBR became lost. However it didn't just fail: I had plenty of time to back up my important data; in fact once I disabled the NTFS partition which held the unreadable sectors the computer became absolutely stable (before I had lots of freezes).

The drive already works but it is used for experimental purposes only.

Joe.

---

