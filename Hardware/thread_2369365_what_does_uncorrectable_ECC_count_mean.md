---
title: "what does uncorrectable ECC count mean?"
date: 2017-08-22
forum: Hardware
---

### Post by ardouronerous on 2017-08-22
About a 3 months ago, on my dad's Dell Inspiron E1505 laptop bought in 2007, I replaced the 120GB WD HDD which has 200+ bad sectors with a 120GB WD Green SSD and installed Lubuntu 16.04 on it.

It's running great and fast, however, I am a little concerned about the uncorrectable ECC count, I know very little about SSD drives since this is my first experience with using a SSD drive.

According to GNOME Disk Utility, the SSD is okay, reallocated sector count is 0 and reported uncorrectable errors is 0, but the uncorrectable ECC count is 197 sectors, is this something I should concerned about?

---

### Post by slickymaster on 2017-08-22
*Thread moved to **Hardware**.*

---

### Post by Bashing-om on 2017-08-22
ardouronerous; Hello;

Here is a thought . Does the bios support AHCI (Advanced Host Controller Interface) ? This is a requirement.
I run a 2007 box, and finding and setting AHCI was a endeavor of discovery ! 

[INDENT][INDENT]worth the effort
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
No option for AHCI on the BIOS unfortunately, I searched the BIOS up and down, I found nothing.

Here's my BIOS info:
```
-BIOS-
Date        : 07/28/2006
Vendor        : Dell Inc. (Dell Computer, [www.dell.com]("http://www.dell.com"))
Version        : A08
```

Although there is a update available for my BIOS, I'm a little hesitant in flashing my BIOS, never done it before, so I might risk bricking my laptop and I don't have the money to do a risk like that.

Here's the results of smartctl:
```
smartctl 6.5 2016-01-24 r4214 [i686-linux-4.10.0-32-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Device Model:     WDC WDS120G1G0A-00SS50
Serial Number:    171301A00E4C
LU WWN Device Id: 5 001b44 8b4ee0216
Firmware Version: Z3311000
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Wed Aug 23 08:14:55 2017 PHT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x11) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   000   100   000    Old_age   Always       -       393
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       77
165 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       4298244138
166 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
167 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
168 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
169 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
170 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
171 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       2
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   062   046   000    Old_age   Always       -       38 (Min/Max 0/54)
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
230 Unknown_SSD_Attribute   0x0032   100   100   000    Old_age   Always       -       60129935374
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       100
233 Media_Wearout_Indicator 0x0032   100   100   000    Old_age   Always       -       55
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       198
241 Total_LBAs_Written      0x0030   253   253   000    Old_age   Offline      -       156
242 Total_LBAs_Read         0x0030   253   253   000    Old_age   Offline      -       200
244 Unknown_Attribute       0x0032   000   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported
```

In GNOME Disk Utility, **uncorrectable ECC count is 198**, while in smartctl, it's referred to as **234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       198**.

---

### Post by Bashing-om on 2017-08-22
ardouronerous; Welp;

We got to have that Advanced Host Controller Interface for the SSD.

My ole Phoemix bios also did/does not have a AHCI setting. But, I found that If I set the controller to raid - and NOT enable raid on my drives - that will enable AHCI !

Maybe yours is similar ?

[INDENT][INDENT]maybe Yes ?
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
How do I set it to RAID? Because when I was checking my BIOS, I found nothing on RAID.

---

### Post by Bashing-om on 2017-08-22
Agoardouronerous; Ouch .

No idea as each and every manufacturer does bios different.
Maybe we can learn . When you boot up on the bios splash screen is the actual Bios and version that you have .
Pass that back here and I see what I can find out .


[INDENT][INDENT]I was pleasantly surprised when I found out howto on my bios
[INDENT][INDENT][INDENT]and hugely relieved as then my ATA errors ceased !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
Okay, I checked again the BIOS, cannot find AHCI or RAID.  The splash screen read, "BIOS Revision A08".

---

### Post by Bashing-om on 2017-08-22
ardouronerous; Yukl

A 1st look and not looking too promising:
[http://en.community.dell.com/support-forums/servers/f/906/t/19453767](http://en.community.dell.com/support-forums/servers/f/906/t/19453767)

I continue to see what I can find to support you.

edit:
Nope not looking good for the home team:
[https://www.dell.com/support/article/us/en/19/sln155274/how-to-configure-raid-on-a-dell-desktop-pc?lang=en](https://www.dell.com/support/article/us/en/19/sln155274/how-to-configure-raid-on-a-dell-desktop-pc?lang=en)

[INDENT][INDENT]help where I can
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
Yes, based off reading the link, doesn't look like A08 supports RAID.

Is a uncorrectable ECC count something I should be worried about though? Because based off performance, I don't see a problem really.

[IMG]https://kbimg.dell.com/library/legacy/kcswisdom/images/kcswisdom_sol_20140108152039/1372949617120.sata_operation.jpg[/IMG]

The option "Drives" doesn't even come out in my BIOS.

---

### Post by Bashing-om on 2017-08-22
ardouronerous; Honestly-

I would be very skeptical about getting a SSD functional on that hardware .
All I find in quick look-a-bout says NO .
For instance:
[http://en.community.dell.com/support-forums/laptop/f/3518/t/19002761](http://en.community.dell.com/support-forums/laptop/f/3518/t/19002761) .

[INDENT][INDENT]U wish I had better news
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
Weird though, but the SSD runs fine though on the laptop, I'm typing this on the laptop right now.

No problems with performance at all, the SSD is running fast and smooth, even GNOME Disk Utility says the SSD is okay, other than the uncorrectable ECC count.

---

### Post by Bashing-om on 2017-08-22
ardouronerous;

Run it . As it performs . great . I could accept that the info provided as errors have no basis as there is no a solid interface structure .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
You mean smartctl could be in error when it recorded the uncorrectable ECC count?

---

### Post by Bashing-om on 2017-08-22
ardouronerous; Hey;

Most assuredly :
> 
smartctl could be in error 

It "might" be erroneous .
" SMART attributes -- both what ID number maps to what capability/feature, and the the encodings of the 6-byte RAW_VALUE field -- are not defined per any T13 ATA standard.  Welcome to the nature of the beast that is SMART"
There is no standard that each manufacturer follows.
 
As you Ran:
```

smartctl -a /dev/sda

```
Well, you see:
" Device is:        Not in smartctl database [for details use: -P showall] "

So yeah .. you can not rely on what is reported.
Now Western Digital "might" be able to offer some help .

[INDENT][INDENT]as is
[INDENT][INDENT][INDENT]can not say
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-22
I looked into that, and the Western Digital diagnostic utilities are for Windows 7, 8 and 10, no Linux support and I don't have access to Windows.

Oh well, let's hope this is all a false positive and there's nothing wrong with my SSD.

Thanks for the help :)

---

### Post by Bashing-om on 2017-08-23
ardouronerous' Well.

In this situation of " Device is: Not in smartctl database " We have nothing definitive out of the box.
As the SSD performs - wonderful in and of it's self - use it .\; see what happens.
Watch the logs and make sure they are not being spammed and swamped .

[INDENT][INDENT]hopefully
[INDENT][INDENT][INDENT]all good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-08-23
What logs are you referring to? And what do you mean by not being spammed and swamped?

---

### Post by Bashing-om on 2017-08-23
ardouronerous; Hey -

System logs are in the directory /var/log/
Of particular interest in growth:
kern.log
syslog

I like to have a working familiarity with the boot messages:
```

journalctl -b -0

```
interesting read what all takes place just to boot the system .

[INDENT][INDENT]nothing happens on the system
[INDENT][INDENT][INDENT]that is not logged somewhere
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

