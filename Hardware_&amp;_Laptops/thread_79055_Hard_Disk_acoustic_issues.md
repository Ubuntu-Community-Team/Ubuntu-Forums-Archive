---
title: "Hard Disk acoustic issues??"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by John.Michael.Kane on 2005-10-19
does anyone still get hard disk acoustic issues like a click every 5 sec's with 5.10 i know it was an issue with 5.04.

---

### Post by John.Michael.Kane on 2005-10-21
Does anyone get "clicks" every few seconds when their hard drive is idle? i have not found a fix for this issue, and wonder if anyone else has this problem.

Heres the output of  hdparm -i /dev/hda```
Model=SAMSUNG MP0402H
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78242976
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode

```

---

### Post by John.Michael.Kane on 2005-10-21
Am i the only one with this issue? seems i cant find any other post with this issue in 5.10..

---

### Post by Azrael on 2005-10-21
[quote=SD-Plissken]Am i the only one with this issue? seems i cant find any other post with this issue in 5.10..[/quote] NO. I have it too!

I think it's maybe slightly less frequent than in Hoary -- but that could be my imagination. I would really like to get rid of it too. It is really annoying in a nagging sort of way isn't it? :p 

The "click" is usually accompanied by the blinking of the icon on my Thinkpad T20 which looks (ever so slightly) like this:
._____
 (_____)
 |........|
 | . <--+-->
 |_____|

which indicates the hard drive being accessed I think. I have no idea why it does that during idle times! I thought for a second it might be swap, but it does that even when swap is completely empty.

Here's my output of hdparm -i /dev/hda:

```

 Model=SAMSUNG MP0804H, FwRev=UE100-14, SerialNo=S042J10XC46781
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156368016
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode

``` Very similar, eh? I wonder if this is an issue with Samsung drives?

I used to have Windows 98 SE on the same hardware -- and it never happened there. I guess I'll do some Googling. Unfortunately, this is a hard problem to describe in a clear way...

---

### Post by John.Michael.Kane on 2005-10-21
Well i hope theres is true fix... i thought i was the only one with the issue.

---

### Post by John.Michael.Kane on 2005-10-21
Has anyone else had this same issue other than me and the other poster. if so has there ever been a fix for it.

---

### Post by John.Michael.Kane on 2005-10-21
Seems there is no fix after search on google. so it would seem that this is the norm for linux or my drive is bad. since only one other posted the same issue.

---

### Post by John.Michael.Kane on 2005-10-22
Anyone has this same issue other then one other poster. or does anyone know of a fix?

---

### Post by matthew on 2005-10-22
It happens to me as well, both when I was using Hoary and now under Breezy. An interesting sidenote is that it did not happen with my old hard drive, which was a Toshiba--but that one died a sad and ugly death. When I replaced it with my current Samsung drive the clicking started. There may be some sort of connection to hard drive brand, or maybe my old Toshiba drive didn't do it and that was symptomatic of the impending failure.

I don't know of a fix.

---

### Post by John.Michael.Kane on 2005-10-22
matthew thanks. well i guess i will let the issue beas is. i have also found that the click issue affected Ibm/Hitachi also. so far it would seem the only option is to replace the drive..

Anyone else who has had this issue, and has had it resloved please post.

---

### Post by John.Michael.Kane on 2005-10-22
Since there seems to be no known fix. i'm left to beleave my drive is failing, and will have no choice but to send it back.

---

### Post by AgenT on 2005-10-22
Few things: it is really difficult to know what you are talking about without a good quality sound recording. A click can be many things. 

But you should note a few things. There are hard drives out there that are known to make click noises every time they are used, but not in the normal sense. They have special drive head parking and have the drive parking/unparking make a lot of noise that sounds like a click. This is a hardware issue, not a software one and cannot be solved without buying a new and different hard drive. Note that most, if not all, new hard drive have a drive head parking feature built in. This is done to prevent hard drive failure due in laptops. And your drive *will* be accessed because of logs, etc. every few seconds even if idle. One way to see if this is the cause is to enable laptop mode (laptop-mode-tools) and go on battery. Laptop mode should turn on (make sure that it does) and after a minute or so it should park the drive and should put the drive into a longer buffer state (not exactly sure what this is callled). This will make the actual hard drive not be updated as often. Instead, the updates are buffered in memory and update less often. This is done to save on battery consumption.

You should also know that there are hard drive monitoring and testing tools available for Linux. Install smartmontools (available in Ubuntu repositories). Then go to [www.thinkwiki.org](www.thinkwiki.org) and look up the article on smartmontools which will show you how to test your hard drive.

---

### Post by John.Michael.Kane on 2005-10-22
laptop mode tool=installed =same click issue

smartmontools=installed no info on thinwiki found info else where

heres the output```
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG MP0402H
Serial Number:    
Firmware Version: UC100-14
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sat Oct 22 04:02:40 2005 EDT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```


```
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

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
data collection:                 (2400) seconds.
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
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  40) minutes.

```


```
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -       2624
  4 Start_Stop_Count        0x0032   072   072   000    Old_age   Always       -       28602
  5 Reallocated_Sector_Ct   0x0033   100   100   011    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       131486
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       236
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       6894
194 Temperature_Celsius     0x0022   118   079   000    Old_age   Always       -       40
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1374476
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   051    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x0012   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0012   100   100   000    Old_age   Always       -       5
225 Load_Cycle_Count        0x0012   077   077   000    Old_age   Always       -       239571
255 Unknown_Attribute       0x000a   100   100   051    Old_age   Always       -       0


```


```
=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 1
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1 occurred at disk power-on lifetime: 58 hours (2 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  02 51 00 03 82 7d e0  Error: TK0NF

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  10 a5 00 03 82 7d e0 00      00:01:46.375  RECALIBRATE [OBS-4]
  91 a5 3f 10 01 80 af 00      00:01:46.375  INITIALIZE DEVICE PARAMETERS [OBS-6]
  c6 03 10 00 00 00 a0 00      00:01:46.375  SET MULTIPLE MODE
  ef 03 0c 00 00 00 a0 00      00:01:46.375  SET FEATURES [Set transfer mode]
  ef 03 45 00 00 00 a0 00      00:01:46.375  SET FEATURES [Set transfer mode]


```

---

### Post by John.Michael.Kane on 2005-10-22
Out put the smartmon info. i guess i will just send the drive back. since laptop mode tools dont work. and cant seem to get any other info or fix...

---

### Post by AgenT on 2005-10-22
You are correct, no information is available at that wiki. Updated link below.

You should run all the tests available for your hard drive and check the logs after each is finished for errors or failures. See the [HOWTO Monitor your hard disk(s) with smartmontools]("http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk%28s%29_with_smartmontools").

As stated above, note that your drive may not be broken but just may be made that way! The clicking noise may be standard for that hard drive. There is even an IBM webpage that discusses this. There may be NO FIX for your problem except getting a DIFFERENT hard drive that does not have clicking head parking. This is considered a "feature" of your hard drive (head parking) and there may be NO FIX for it. The problem, of course, is that the head parking makes an annoying noise. But again, there probably will not be a fix and expect every other hard drive to have head parking as well. If you want to buy another drive, read up on it before buying! Make sure the head parking is not loud.

laptop-mode-tools should stop your hard drive. It should appear to turn off because it will spin down and you will not be able to feel any vibrations at all. If it does not it could be because your hard drive does not support this feature or you do not have laptop-mode working properly. Just because you installed it does not mean it is configured (or even turned on!).

A good way to see if your clicking noise this is a "feature" of your hard drive is just to listen to it while idle. Does it click at a constant frequency? Maybe like every 5 seconds? If yes, then this is probably head parking at work.

---

### Post by John.Michael.Kane on 2005-10-22
```
smartctl -H /dev/hda smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

```
smartctl -l error /dev/hda smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 1
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1 occurred at disk power-on lifetime: 58 hours (2 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  02 51 00 03 82 7d e0  Error: TK0NF

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  10 a5 00 03 82 7d e0 00      00:01:46.375  RECALIBRATE [OBS-4]
  91 a5 3f 10 01 80 af 00      00:01:46.375  INITIALIZE DEVICE PARAMETERS [OBS-6]
  c6 03 10 00 00 00 a0 00      00:01:46.375  SET MULTIPLE MODE
  ef 03 0c 00 00 00 a0 00      00:01:46.375  SET FEATURES [Set transfer mode]
  ef 03 45 00 00 00 a0 00      00:01:46.375  SET FEATURES [Set transfer mode]


```

Being that theres an error listedi would think the drive is going as well..

---

### Post by matthew on 2005-10-22
[quote=SD-Plissken]Since there seems to be no known fix. i'm left to beleave my drive is failing, and will have no choice but to send it back.[/quote]
It is possible you misunderstood me. The drive I had that failed did NOT make this noise. The drive I have that is functioning well DOES make it.

As the other poster noted, I think it is just head parking or something similar. On my drive it is a regular, intervalic phenomenon.

---

### Post by John.Michael.Kane on 2005-10-22
matthew seems smartmon says i have some kind of error in the post before so it would seem theres some drive issue.

---

### Post by matthew on 2005-10-22
[quote=SD-Plissken]matthew seems smartmon says i have some kind of error in the post before so it would seem theres some drive issue.[/quote] Oh, okay, my bad. I just wanted to be sure you didn't send back a working drive out of fear.

---

### Post by John.Michael.Kane on 2005-10-22
If you take a look at the smartmon post of mine it seems to say theres some error ,and  checked it more than once so it would seem theres an issue with the drive.

thanks to all.

---

### Post by danpre on 2005-10-23
[QUOTE=Azrael]NO. I have it too!

I think it's maybe slightly less frequent than in Hoary -- but that could be my imagination. I would really like to get rid of it too. It is really annoying in a nagging sort of way isn't it? :p 

The "click" is usually accompanied by the blinking of the icon on my Thinkpad T20 which looks (ever so slightly) like this:

...

Unfortunately, this is a hard problem to describe in a clear way...[/QUOTE]


I have the same SAMSUNG disk.
And the same problem.
Can this cause disk failure in future? Or shorten disk lifetime?

DANIeL

---

### Post by John.Michael.Kane on 2005-10-23
danpre maybe not sure. i however have filed out the rma forms for my drive..
i have looked over every know method on how to fix it. and it has not solved it for me so i'm left to beleave that my drive is failing..

---

### Post by blueturtl on 2005-10-23
This idle clicking noise is evident in certain new Seagate hard-disks as well and after extensive studying I have come to find that it is not a hardware flaw, but a feature in the drives that keep them in shape. It's been a while now since I last looked into it, so it's not fresh in my memory, but I think it had something to do with aligning the read/write heads continually while idling. Some kind of calibration. This is what I dug up for you:

> Dedicated Servo vs. Embedded Servo

Dedicated Servo is a head positioning technique that requires a "dedicated" platter surface and head to position the read/write heads. Servo information is contained on the dedicated platter, which is tracked by the dedicated head. The remaining read/write heads are then slaved to the dedicated head. Dedicated servo drives require thermal calibration cycles to update head position at regular intervals, which can cause dropouts in the recorded audio or stuttering during playback. When purchasing a dedicated servo drive, we recommend getting a drive with A/V firmware installed. A/V will interrupt the thermal calibration cycle until the drive has completed a command.

Embedded Servo is a head positioning technique that intersperses servo information between the data tracks on all platter surfaces. The read/ write heads transmit the servo information to the drive's electronics, which in turn position the actuator arms so that the heads receive the maximum signal from the servo bursts. Maximum signal occurs only when the heads are directly over the center of the track. The read/write heads constantly receive tracking information, and therefore, are always aligning themselves. Embedded servo drives do not require thermal calibration cycles to update head position. The embedded servo technique can be found in most drives on the current market, and is highly recommended for use with Session.

---

### Post by John.Michael.Kane on 2005-10-23
That may explain seagate drives. however i see no use of it in the samsung drive specs i have found.

---

### Post by blueturtl on 2005-10-23
Somebody suggested once that you might have some timed tasks run after booting if you don't keep your computer on 24/7. However if it's constant, I would say you may have purchased a "Dedicated Servo" drive. I doubt this is a Seagate-only technology. I too thought my drive had gone mad or that there was something running in the background but the behaviour of the drive suggested this article might have something to do with it. If for instance your drive does this clicking very regularly, then stops for a while and does it again after sometime it could mean it's using Dedicated Servo. If it does that, and also interrupts it for whatever else you may need the drive for, that could be a good sign.

---

### Post by John.Michael.Kane on 2005-10-23
it clicks 2-5secs how is this norm. and i tried everything and listed the out put above.

---

### Post by JKMB111 on 2005-10-29
I have a similar constant clicking problem with my laptop when I do NOT load the  X server (Gnome desktop)...  I do get the clicking when I install part of the KDE desktop.  I "think" it happens around the time I install kdeutils.....  I don't get the clicking when running the Windows XP that came with the laptop.   I first experienced it 10 weeks ago when I had Debian Sid loaded... I did NOT have the problem with Etch and initially did not have it with Breezy until recently.  I now experience the clicking with a new install of the current Etch..... I do NOT have the problem with the standard install of Breezy when Gnome is loaded and I have not added KDE apps..... Well I have added Kontact and Kmail without any clicking.  It has been two days now without any clicks.

---

### Post by harobed on 2005-10-30
[QUOTE=SD-Plissken]Does anyone get "clicks" every few seconds when their hard drive is idle? i have not found a fix for this issue, and wonder if anyone else has this problem.
[/QUOTE]

I've same problem.

It's acpi power save which do this "clicks". This stuff do :
```

hdparm -S 4 /dev/hda
hdparm -B ??? /dev/hda

```

to stop it, you can do 

```

/etc/init.d/laptop-mode stop
hdparm -S 0 /dev/hda
hdparm -B 255 /dev/hda

```

This command disable totaly hard disk spin down.

To do this permanent, you can do that :

```

rm /etc/rc2.d/S20laptop-mode

```

and in your /etc/hdparm file add or update that :

```

command_line {
       hdparm -q -m16 -q -W0 -q -d1 -S 20 -B 255 /dev/hda
}

```

Not hesitate to comment it.

Cheers,
-- Stéphane

---

### Post by telmo on 2005-11-06
[QUOTE=harobed]I've same problem.

It's acpi power save which do this "clicks". This stuff do :
```

hdparm -S 4 /dev/hda
hdparm -B ??? /dev/hda

```

to stop it, you can do 

```

/etc/init.d/laptop-mode stop
hdparm -S 0 /dev/hda
hdparm -B 255 /dev/hda

```

This command disable totaly hard disk spin down.

To do this permanent, you can do that :

```

rm /etc/rc2.d/S20laptop-mode

```

and in your /etc/hdparm file add or update that :

```

command_line {
       hdparm -q -m16 -q -W0 -q -d1 -S 20 -B 255 /dev/hda
}

```

Not hesitate to comment it.

Cheers,
-- Stéphane[/QUOTE]

It's known that some thinkpad models (with hitachi drives) do these anoying clicks. Is this solution for this specific case or it just works with everything?

I have a Thinkpad X41 with a Hitachi drive, and the clicking really SU*KS! But this problem isn't Breezy specific. It also happens with Wind'hoes (that i so hapilly removed from my beautifull laptop)

Here a link to this situation that may help:

[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")

---

### Post by telmo on 2005-11-06
Hey... clicking continues... :(

---

### Post by rado_london on 2005-11-09
Hey the temporary thing works:
```
sudo laptop-mode start
```
but is only temporary.i also tried the method above but it says there is no such file of directory.
Is there any other way to make this working from starting the machine?

---

### Post by mips on 2005-11-09
I installed Breezy on my HP nx6110 yesterday and that click you are talking about is still there. More like at 15sec intervals though.

---

### Post by erez1012 on 2005-11-10
is anyone solvd this problam?????
my hdd crazy me:((

---

### Post by rado_london on 2005-11-10
i didnt it stopped doing this noise for a day and now is doing it again
This drives me crazy.
Please help the newbies?

Best Regards

---

### Post by beijingjj on 2005-12-16
I started noticing this clicking noise a few days ago on my IBM Thinkpad T42.  It's the sort of thing I think I would have noticed if it had been doing it earlier.  I've been racking my brain trying to think what I changed that would have caused this to start but nothing has come to me yet.

running "laptop-mode start" just now actually seems to have made a difference.  I'll have to test it out more thoroughly tomorrow.  The noise is not very loud to begin with but it does irritate the h3ll out of me when the room is quiet.  When the room has some noise in it the clicking sound is still grinning at me with that knowing look that says it's going to rear its head as soon as there is quiet.  

I had a similar experience with my Dell Inspiron a couple of years ago.  The clicking noise was louder and more of a "clucking" than a "clicking."  It bothered me so much that I even bought a new HDD.  This didn't help.  After spending a long time researching it I finally found the solution, which I see others have posted in this thread.  it is "hdparm -B 255 /dev/hda."  Interestingly this newer HDD does not make those clucking noises when I leave power management enabled.

Has one of these two solutions *not* worked for anyone?

---

### Post by teaker1s on 2005-12-16
Ibm replaced some drives with firmware, others with fujitsu drives- It's a head parking problem on notebooks
desktops hitachi/ibm deskstar =deathstar they die mine did and so did may others

---

### Post by mips on 2005-12-17
The IBM/Hitachi Travelstar dirves are the best laptop drives out there, ask any professional data recovery company. the worst 2.5" drive is Seagate.

I think this is a Linux issue as it does not seem to happen under windows.

---

### Post by M3ta7h3ad on 2005-12-17
Not that this is whats happening here, but I always took clicking noises on a harddrive a sign that there is a failure about to occur, at least when using windows.

I'd advise you all going through the Smartmon check (listed further back in the thread) and if you get an error, assume the worst, start backing up your data, and shop around for a new hard drive.

---

### Post by mips on 2005-12-17
The clicking noise is not the same as when you are about to experience a hard drive failure. Lol, i heard that kinda click 2 weeks ago on a friends laptop but it was already to late for him.

---

### Post by ninotob on 2005-12-17
[QUOTE=SD-Plissken]Am i the only one with this issue? seems i cant find any other post with this issue in 5.10..[/QUOTE]

No -- I am too.  I only notice it on my old laptop because the drive is noisy -- my desktop itself has enough fan noise to block it out.  I worry sometimes that it will shorten the HD life, but I'm not sure if it that's paranoid or rational thinking.  However, I do know that Suse ... maybe 9.1 or 9.2? did this on the laptop of somebody I know.  It may not be limited to ubuntu.

---

### Post by ninotob on 2005-12-17
[QUOTE=SD-Plissken]matthew thanks. well i guess i will let the issue beas is. i have also found that the click issue affected Ibm/Hitachi also. so far it would seem the only option is to replace the drive..

Anyone else who has had this issue, and has had it resloved please post.[/QUOTE]

I have seagate and maxtor in my Desktop -- the maxtor is old and noisy though and the seagate very quiet -- I see the HD light flash every 2.5 seconds but hear no sound.  I'm in Breezy BTW.  I doubt it's a drive manufacturer issue.

---

### Post by ninotob on 2005-12-17
[QUOTE=telmo]
Here a link to this situation that may help:

[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")[/QUOTE]

Thank you (and harobed as well).  This solved the issue on my firewall (with an old laptop drive I pulled out of an ibook and have now in a desktop mini-itx system).  It had been clicking 1x every 15 seconds.

hdparm -B 255 /dev/hda

cured the problem.  This turns power management off completely.

---

### Post by mips on 2005-12-17
The problem stems from the drives power management feature of parking the heads during idle time, that is the clicking sound.

The problem is fixable but I would not know how to do it in Linux. I'll try and find out some more.

Lots of people report using Intel's Application Accelerator in Win to change a drives power settings. Apparently drive manufacturers also have their own utils for this available. 

So this is done via software, thus it should be possible to do in Linux.

---

### Post by wh0rd on 2005-12-31
I've also been getting the clicks under Kubuntu 5.10. At first I thought I had mice and bought mouse traps, but then I realized the sound was coming from my laptop. I have a Sony Vaio PCG-Z1WA with a Toshiba 6021GAS hard drive and I've replaced the hard drive recently. The previous hard drive crashed running Ubuntu 5.04. So I don't  think the clicking issue is with the hard drive. One more thing is that when i'm running my Windows XP partition on the same hard drive there is no clicking sound. I don't have enough technical background to pin point the issue but maybe it's the way Ubuntu deals with hard drives?

---

### Post by John.Michael.Kane on 2005-12-31
[QUOTE=wh0rd]I've also been getting the clicks under Kubuntu 5.10. At first I thought I had mice and bought mouse traps, but then I realized the sound was coming from my laptop. I have a Sony Vaio PCG-Z1WA with a Toshiba 6021GAS hard drive and I've replaced the hard drive recently. The previous hard drive crashed running Ubuntu 5.04. So I don't  think the clicking issue is with the hard drive. One more thing is that when i'm running my Windows XP partition on the same hard drive there is no clicking sound. I don't have enough technical background to pin point the issue but maybe it's the way Ubuntu deals with hard drives?[/QUOTE]



You will have to edit hdparm.config to make the drive quiet during the boot process. i dont know the code off hand, however i know it has to be added the comand line at the bottom of the file.

---

### Post by Arto on 2006-01-03
Thanks, guys; the constant clicking (usually every 10-15 sec or so) had been driving me crazy for some time now, but disabling HDD power management per the instructions in this thread has solved the problem.

I can confirm a sweet absence of horrid clicks, for half an hour now, after running the command:

```
sudo hdparm -B 255 /dev/hda
```

Oh, and it seems that in order to make the change permanent, you just need to edit /etc/hdparm.conf and uncomment the following directive (line no 26 on Hoary):

```
# -B apm setting
apm = 255
```

---

### Post by John.Michael.Kane on 2006-01-06
If anyone here has a laptop using hdparm, and has udma 100 enabled and the clicking to stop please post your working config.

---

### Post by John.Michael.Kane on 2006-01-21
For those still having this clicking issue. I have posted my hdparm command line. This is being used on and ibm based drive, and has quiet the clicking. adjust for your drive..

```
command_line {
       hdparm -q -B255 -q -M128 -q -c1 -q -m16 -q -W0 -q -d1 /dev/hda
}

```


hope this helps..

---

### Post by StacyR on 2006-02-04
i know this is blasphemy in a linux board but does anyone know if there is a windows program the can do hdparm to fix clicking sound? i'm on the road without an external cdrom so i can't run any of the firmware or anything!

---

### Post by mips on 2006-02-04
StacyR,

Yes there is but I cannot remember what it is called, will have to check.

What Brand HD do you have ???

---

### Post by StacyR on 2006-02-04
its a hitachi 60 gb HD that comes in a thinkpad x41 tablet

thanks alot!

---

### Post by mips on 2006-02-04
Intel Application Accelerator is one but only for Intel chipset devices.

---

### Post by mips on 2006-02-04
[QUOTE=StacyR]its a hitachi 60 gb HD that comes in a thinkpad x41 tablet

thanks alot![/QUOTE]

Deja Vu, i actually have one of those lying right next to me on the desk, but this one is kinda broke.

Will let you know what i find

---

### Post by mips on 2006-02-04
Have a look at [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

Proceed with caution and read the manuals first.
Feature Tool (v2.00)
Power Booster
DDD-SI

---

### Post by paritybit on 2006-04-22
I know I am really late to the party but there is a pretty simple solution for all this. The clicking from what I have read around the place is caused by the hdd spinning back up after being put to sleep. If the hdd hasn't been used on battery for 5 secs it will be put to sleep by default. This can be changed. You will need to edit /etc/laptop-mode/laptop-mode.conf (assuming you have laptop-mode-tools installed which I think it is by default).
Anywhoo, read through there it is pretty well commented but for the simple solution, go down to where there is a line similar to this:
```
# Should laptop mode tools control the hard drive idle timeout settings?
CONTROL_HD_IDLE_TIMEOUT=1
```
You can set this to 0 and stop laptop-mode-tools from spinning down your hdd which will cause some problems when it comes to power usage. I edited some other lines below this and set some custom values:
```
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 5 seconds
# for battery and for AC with laptop mode on.
LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=30
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
```
This just means that when laptop mode is enabled with ac plugged in it will spindown after 60 sec and on battery it will take 30sec. However, I assume this means after 30sec of inactivity the hdd will spindown. This is a large timeout and really should be more like 15 or 10 seconds.... I just don't care a lot as I have about 5 hours of battery on my laptop.
Now you will need to do a 
```
sudo /etc/init.d/laptop-mode restart
```
and the clicking should be fixed, well not really, it will remain but only if you don't use your hdd for the amount of time specified.... or turn off hdd spindown and try your luck.
PS- I take no responsibility if you follow these instructions and they make you sterile, stupid or both. You shouldn't follow instructions you don't understand.
PPS- To be honest I don't really understand them/am not a guru on the subject but these changes make sense and that is what Linux is all about. I never have a problem and go "why the hell is it doing that" I am usually saying "well that was bleeding obvious wasn't it"

---

### Post by cskeide on 2006-04-30
[QUOTE=paritybit]
```
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 5 seconds
# for battery and for AC with laptop mode on.
LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=30
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
```
[/QUOTE]

I had these problems after installing dapper, and found this solution in another thread a few weeks ago. Today, however, there was a couple of updates to acpi-tools and laptop-mode among others. I can't belive that laptop-mode.conf still has a 5 second idle timeout as default...! There might be a good reason for it, but to me it seems ridiculous. Anyways, the 60 and 30 second timeouts works great for me. =)

---

### Post by paritybit on 2006-05-01
Yeah, did this today too, just re-edited the file, 9 out of 10 times you can keep old config files (well on my debian systems it works fine).

---

### Post by Talisker on 2006-08-16
I'm glad to find this thread...*S*
I have the same HD "beep" issue with my IBM drive. Ich changed the timeout settings restarted laptop mode and it was nice and quiet. Then, after the display suspend mode got activated I got the message the a failure in the Gnome power managment occured and if I want to restart the application. I click yes. I checked laptop mode and suddenly it is disabled?:confused: 

Do I have to disable power managment when using laptop mode?
And how do I enable power management? The start command doesn't do anymore.

Thanks

---

### Post by MonsterDog on 2006-10-09
Thank you all,

I didn't really think the clicking was all that annoying until I took my battery out.  I didn't really realize how frustrating it was until it went away.  hdparm worked for me.  I haven't made it automatic yet because I quite enjoy clicking the SHUTUP icon on the desktop.

Thanks again,
MD

---

### Post by Average Joe on 2006-11-07
I know this thread is pretty old, but it really helped me solving the clicking sound of my hard disk.

I recently bought a new Seagate Momentus 160GB hard disk for my laptop, since my old hard disk had given up. I also heard the annoying clicks every 15 seconds or so. It kind of freaked me out since I didn't want my new hard disk to die immediately.

But after typing:
```
sudo hdparm -B 192 /dev/hda
```
there was silence. I don't have to disable the Advanced Power Management (apm) completely (-B 255) to stop the clicking. I tried lowering the value in steps of 16, and this was the lowest value for which it works. For -B 176 it is still clicking.

I added:
```
/dev/hda {
               apm = 192
}
```
at the end of my /etc/hdparm.conf file so now it is the default setting for my hard disk when booting up.

Hope this helps for other people having clicking problems with their hard disk.

P.S. Paritybit's solution (adjusting the laptop-mode.conf file) didn't work for me.

---

### Post by esaym on 2006-11-08
I have had this problem with my laptop too.  I am aware of laptop hard dives having head parking features.  I am familiar with the noise which is way it never bothered me much.  It wasn't until I read this thread that I realized that it was parking way too much and thus limiting that life.  Well atleast from what I have read it is limiting the life.

I found that the parking only stopped with hdparm -B254 instead of -B255

Also I am using ext2 filesystem to try and cut down on the frequent disk access.  It seems almost impossible to eliminate.  Anyone know what might cause this? [http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713](http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713)

Reading info:

[http://web.glandium.org/blog/?p=54](http://web.glandium.org/blog/?p=54)
[http://www.pcmag.com/article2/0,1895,1879486,00.asp](http://www.pcmag.com/article2/0,1895,1879486,00.asp)
[http://www.ariolic.com/activesmart/smart-attributes/load-unload-cycle-count.html](http://www.ariolic.com/activesmart/smart-attributes/load-unload-cycle-count.html)

---

### Post by schrauberfuchs on 2007-01-12
Hi folks!
Yes, i've also these acoustic issues, so I'm glad to find this thread.

Ok: I've got an refurbished IBM Thinkpad T23, 30GB, 256MB, using ubuntu 5.10. The first disk ****** up with read-errors in block28 and 7x 
=> dealer => warranty => new (used?) HDD.

History of the dead first disk:
got T23. Ubuntu 5.10 installation. everything was fine, the HDD didn't draw my attention.
Then I did my special "battery-refresh-cycle" (brc) as follows: 
switch Notebook to BIOS. disconnect power. Do nothing till battery is empty. It will be really empty ;) Next morning I reconnechted power, Booting 5.10, After the System was up, I heard 
this clicking sound and the drive restarting. This was repeating all the time.
I still had access to the menues, but slower (waiting for HDD).
I shut down the System the normal soft way, and tried to reboot. Then I got the read errors above.
Block28 and 7x.
=> dealer => warranty => new (used?) HDD "disk2".

disk2:
Ubuntu 5.10 installation. everything's fine but there still the sound of the HD. 
At the moment the System ist running idle. There are 2 HDD-accesses every 20sec,
the HDD-LED ist blinking then.  

/dev/hda HITACHI_DK23DA-30GB

OK, now I'll try to get hdparm-information to post soon...

Thanks!

---

### Post by schrauberfuchs on 2007-01-12
Here my output:

hdparm -i /dev/hda

```
/dev/hda:

 Model=HITACHI_DK23DA-30B, FwRev=00J1A0B6, SerialNo=10X8H8
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/15/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/15/63, CurSects=15481935, LBA=yes, LBAsects=58605120
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:

 * signifies the current active mode
```

HDD works but still sounds too clicky...

Thanks a lot!

---

### Post by W. Irving on 2007-02-01
schrauberfuchs, your battery cycling is going to kill your battery before it has a chance to die on its own accord. Lithium ion batteries do not have the memory effect. Recharging them fully causes some wear to the cells, and eventually they will refuse to hold any charge. If you want to be good to your battery, charge it, then disconnect and store in a drawer for a month or two before charging it again. :)

I read the whole thread, and the page at Thinkwiki: [http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking)
These are my conclusions.

I have a T23 with a Hitachi Travelstar (IC25N030ATMR04-0) and XUbuntu 6.10. My drive clicks from time to time, sometimes several minutes pass, and in other instances only a few seconds inbetween clicks. Acoustic management is set to 254. Running smartctl -a (it's included in smartmontools package, for those that didn't know) you'll see lots of information concerning the drive. Look for Load_Cycle_Count, remember the number, wait until the drive clicks again, then execute smartctl -a and have a look at Load_Cycle_Count again. You'll see it has increased by 1.

What happens if you disable head parking entirely is that your drive might be damaged if for some reason the heads should come in contact with the platters (I think I read somewhere the distance is only roughly 120 atoms) with accompanying data loss.
I believe the ultimate solution is to allow the drive park its heads as it wishes, but enable laptop mode to increase the write buffer. Also check /var/logs for frequent disk writes, and disable if suitable.

Setting a 5 second spindown is just plain sadistic, not to mention stupid. You'll kill your drive in no time doing that. A more reasonable spin down time is at least 30 mins. That does indeed mean the drive will probably never sleep - but they are also built to be running, not spooling up and down all the time!

---

### Post by esaym on 2007-02-01
battery info: [http://www.batteryuniversity.com/](http://www.batteryuniversity.com/) :D

---

### Post by schrauberfuchs on 2007-03-11
Hi folks!
Thanks for your battery hints.
Where did you see, that i 'm activating the parkingmode every 5secs?
I agree that this is stupid and a very good way to kill the drive
Anyway - I changed it to an 80G HDD running dapper ubuntu 6.06. 
no clicking, everyting is fine.

A friend of mine asked me to install linux on her T23 instead of MSWin.
She´s got also a 30GB HDD - i`ll see if it will click...

Thanks for your help :)

---

### Post by W. Irving on 2007-03-11
I'm pretty sure the head parking is a feature of the drive, not the OS, so it will click regardless of what OS you're using. Head parking is essential if you don't want to destroy your drive. The platters are spinning at 4200 RPM, and the heads are hovering a fraction of a millimetre next to them. It takes some force to shove the head into the platter, but if it happens you'll kill that particular platter, and you will regret all your nasty words about head parking.

See my previous post about detecting head parking clicks.

---

### Post by mirceade on 2007-11-24
Dudes, like... Take a look at this [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) .

---

