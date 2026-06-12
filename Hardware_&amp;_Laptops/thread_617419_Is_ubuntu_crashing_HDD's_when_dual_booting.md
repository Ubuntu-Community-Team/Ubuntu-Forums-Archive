---
title: "Is ubuntu crashing HDD's when dual booting ?"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by cherva on 2007-11-19
Are you sure  that ubuntu doesn't brake (make bad sectors on) HDD's when the PC is dual booting because I crashed 3 hdd's (2 ata, 1 sata) exactly 2 months after installing ubuntu , my second pc's HDD sounds strange ( close to 2 months ) and one of my friends has bad sectors on 1 of his hdd's (again 2 months after installing ubuntu as second OS ) ??????

---

### Post by Tripletaco on 2007-11-19
I am dual booting.  I just posted about a hard drive problem.  Then I noticed your post.  The hard drive seems to spin constantly in windows XP,even with no hard drive activity. very irritating!  It is quiet in Gutsy though.  ????

---

### Post by santiagoward2000 on 2007-11-19
Hi,
That sounds really bad. I've been dual-booting with XP for about a year, and had no problems with my H.D.D.

---

### Post by jfinkels on 2007-11-19
There has been a lot of talk recently about the bug discussed in this article: [http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

You may want to take a look at that. In summary, Ubuntu may be spinning up and spinning down your hard drive more often than you might like, causing it to reach "old age" prematurely.

However, this is most likely not your problem :) Ubuntu is most likely NOT crashing your hard drive. If it is, you are a fringe case and you should report a bug for the software package that you think is causing the problem.

---

### Post by cherva on 2007-11-22
what about this bug could it be it ?
[https://launchpad.net/bug59695.html]("https://launchpad.net/bug59695.html")
But when I type sudo smartctl -a /dev/hda there is no  Load_Cycle_Count at all :confused:

---

### Post by ubuntu_demon on 2007-11-22
> **cherva said:**
> what about this bug could it be it ?
[https://launchpad.net/bug59695.html]("https://launchpad.net/bug59695.html")
But when I type sudo smartctl -a /dev/hda there is no  Load_Cycle_Count at all :confused:

You might have to turn on S.M.A.R.T. :
```

sudo smartctl -s on /dev/hda

```

You might be interested in getting a very rough estimate of the health of your harddrive by :
```

sudo smartctl -H /dev/hda

```

You might want to use the tool recommended by your harddisk manufacturer to test your harddrive for problems (probably included on the ultimate boot cd-rom)

The support thread for the Load_Cycle_Count issue :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Please read the first post :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

### Post by cherva on 2007-11-23
Ok as far as I can understand these posts my HDDs doesn't die from this bug, but ubuntu-demon how can you explain to me why i crashed 3 HDDs exactly 2 months after they started dual booting with windows ?

---

### Post by ubuntu_demon on 2007-11-23
> **cherva said:**
> Ok as far as I can understand these posts my HDDs doesn't die from this bug, but ubuntu-demon how can you explain to me why i crashed 3 HDDs exactly 2 months after they started dual booting with windows ?

We can only say that it's very unlikely that some bug would cause three disks to die within two months. If you want to know more you should investigate yourself.

Maybe you were just being unlucky. Maybe they were old drives (you haven't told anything about the age of the disks). Maybe one of these drives was seeing an extreme increase of Power_Off_Retract_Count (indeed a problem for a very small percentage of disks in Ubuntu but if you would have this problem you would probably be hearing ugly noise when shutting down. It's solved for Gutsy). 

Maybe you can investigate these broken drives with the diagnostic tools recommended by your harddisk manufacturer (probably included on the ultimate boot cd-rom) and with smartmontools. Please report the results of these diagnostic tools.

Some smartmontools commands (replace /dev/sda appriopriately) :

Turn on S.M.A.R.T. :
sudo smartctl -s on /dev/sda

Do a long test :
sudo smartctl -t long /dev/sda

After this test has completed do the following and post the results here  :

Give a very rough estimate about the health of the disk :
sudo smartctl -H /dev/sda
sudo smartctl -a /dev/sda | more
sudo smartctl -a /dev/sda | grep Power-Off_Retract_Count
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
sudo smartctl -a /dev/sda | grep Power_On_Hours

Here's more information about smartmontools :

man smartctl
[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

### Post by cherva on 2007-11-26
root@mitosoft:/home/cherva# smartctl -H /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

root@mitosoft:/home/cherva# smartctl -a /dev/hda 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SP1654N
Serial Number:    S0GEJQSP500740
Firmware Version: BV100-45
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Mon Nov 26 19:16:01 2007 EET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (3677) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  61) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -       6080
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       10
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   253   253   000    Old_age   Always       -       68
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5
187 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   106   106   000    Old_age   Always       -       44
194 Temperature_Celsius     0x0022   106   106   000    Old_age   Always       -       44
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1110109
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        19         -
# 2  Extended offline    Interrupted (host reset)      10%        15         -
# 3  Short offline       Completed without error       00%        13         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Power-Off_Retract_Count
root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Load_Cycle_Count
root@mitosoft:/home/cherva# martctl -a /dev/sda | grep Power_On_Hours
bash: martctl: command not found
root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Power_On_Hours
root@mitosoft:/home/cherva#

P.S All three disks where brand new exept the first one he was 1 year old and died exactly 2 mounts after I started dualbooting

---

### Post by ubuntu_demon on 2007-11-26
> **cherva said:**
> root@mitosoft:/home/cherva# smartctl -H /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

root@mitosoft:/home/cherva# smartctl -a /dev/hda 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SP1654N
Serial Number:    S0GEJQSP500740
Firmware Version: BV100-45
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Mon Nov 26 19:16:01 2007 EET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (3677) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  61) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -       6080
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       10
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   253   253   000    Old_age   Always       -       68
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5
187 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   106   106   000    Old_age   Always       -       44
194 Temperature_Celsius     0x0022   106   106   000    Old_age   Always       -       44
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1110109
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        19         -
# 2  Extended offline    Interrupted (host reset)      10%        15         -
# 3  Short offline       Completed without error       00%        13         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Power-Off_Retract_Count
root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Load_Cycle_Count
root@mitosoft:/home/cherva# martctl -a /dev/sda | grep Power_On_Hours
bash: martctl: command not found
root@mitosoft:/home/cherva# smartctl -a /dev/sda | grep Power_On_Hours
root@mitosoft:/home/cherva#

P.S All three disks where brand new exept the first one he was 1 year old and died exactly 2 mounts after I started dualbooting

That drive looks healthy from smartctl's perspective (it needs to be called /dev/hda instead of /dev/sda in your case). But you didn't do any long tests which might give a little bit more information.

You should run both smartctl and the diagnostic tool recommended by the harddrive manufacturer on all of these drives. 

Maybe you were being just unlucky. Or maybe you rebooted a lot of times each day for dual booting which causes mechanical stress on the drive). A desktop drive should be able to handle a few reboots a day but if you were rebooting tens of times each day that **might** have caused **some** mechanical stress.

---

### Post by cherva on 2007-11-27
I know this drive is OK (for now), and I didn't rebooted more than 2 times. Any other reasons ?

---

### Post by ubuntu_demon on 2007-11-27
Please investigate the dead drives like I explained before if you want to know more.

Possible causes I can think of (maybe a combination of some of these) : 

* extreme case of bad luck
* maybe something is wrong with your I/O controller / mainboard
* maybe something is wrong with your power supply sending strange currents to your harddrive
* extremely heavy usage of the harddrive (rebooting *a lot* / turning pc off and on *a lot* / installing *a lot* / ...)
* maybe you are transporting your pc *a lot*  (for example to lan parties) 
* [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
only affects certain laptop drives and certain "green" desktop drives which are built like laptop drives (rapid parking)

* [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810) 
only affects a small percentage of harddrives and is fixed in Gutsy

---

### Post by cherva on 2007-11-27
Hmmm maybe something is wrong with my I/O controller because my motherboard was changed ( due to a bug in it ) how can I test it ? Do you have an idea ?

---

### Post by ubuntu_demon on 2007-11-27
Keep monitoring your harddisk using diagnostic tools recommended by your manufacturer (probably included on the ultimate boot cd-rom) and smartctl (use long tests too).

Try and investigate your old broken drives. Maybe you can eliminate power_off-retract_count and load_cycle_count then you'll know it's probably a hardware issue.

If you have a spare mainboard and spare power supply then you can try changing both power supply and mainboard and see whether your harddisks stop dying. 

If you have warranty on your mainboard and power supply you can tell the shop that your harddisks keep dying and that you want replacements to try whether the problem stops.

Maybe your power supply is under-powered or it's a cheap one ? If you think that's the case you might want to consider buying a zalman or other premium brand with a bigger capacity (more Watts). If you buy a decent one you might be able to still use it on your next pc to save some money.

I'm just guessing / trying to help. When you have eliminated power_off-retract_count and load_cycle_count you should probably go to the shop or manufacturer and use your warranty.

---

### Post by cherva on 2007-11-28
I used my warranty, thats why I can't investigate the broken HDDs. But my warranty is till 20th Dec :( I guess if this HDD die I'll sell my PC and buy a new one :)

---

### Post by ubuntu_demon on 2007-11-28
> **cherva said:**
> I used my warranty, thats why I can't investigate the broken HDDs. But my warranty is till 20th Dec :( I guess if this HDD die I'll sell my PC and buy a new one :)
So you still have warranty on your entire pc ? And you have had this issue both with your current mainboard and your previous mainboard ? You can explain that there is a chance that your power supply has caused this trouble (I have no idea how big this chance is). Can't you use your warranty to get a bigger Zalman power supply and pay a few extra bucks ?

---

### Post by cherva on 2007-11-29
No i had other issues with the other one :)

---

### Post by andrew112 on 2008-03-13
Are you saying that if I want to turn my PC on and off frequently its best not to have adual boot?

My computer freezes quite a bit. This was after about 6 months of using a daul boot, maybe turning it on and off several times a day. When it freezes I've been turning it off at the plug (the only thing I could find that worked till I have just discovered Alt Printscr RSEIOU  onthis forum. I've changed the hard disk and currently have a single boot as windows wouldnt load, but this disk has started to freeze too recently, after a few days. 

Maybe theres something else wrong - any recommendations for diagnostic tools?  

I only have 250Mb RAM, could that be part of the proiblem?

Andrew

---

