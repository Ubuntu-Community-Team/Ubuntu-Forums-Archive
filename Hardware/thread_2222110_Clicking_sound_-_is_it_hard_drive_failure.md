---
title: "Clicking sound - is it hard drive failure?"
date: 2014-05-05
forum: Hardware
---

### Post by mastablasta on 2014-05-05
yesterday computer started to make clicking sound on boot and could not boot. i noticed that fan on GPU is not spinning so i cleaned it all. rebooted and it worked fine. today i heard that sound again and it could not boot. disk light was on. does that mean hard disk is about to fail? 

will this show on smart tools for the drive? or on testdisk? 
also i have two drives one is OS drive and the other one data. is this the OS drive that is not working? I mean how do i know which disk to replace if it's a failing disk sign?

pressing hard reset button rebooted computer and it booted nomally. i haven't noticed any unusual smart messages it also acted normally from then on. i have listened to disk sounds here [http://datacent.com/hard_drive_sounds.php](http://datacent.com/hard_drive_sounds.php) and although i have WD drives the sound is more like the "Fujitsu laptop hard drive with bad heads making sweeping sound" in the list. but basically it is just clicking. it doesn't click during work.

so is it definatelly a hard disk or could it be something else?

---

### Post by TheFu on 2014-05-05
Impossible to tell from here.  Open the case and touch the drive when the clicking is happening - you should feel which drive is making the noise.  SMART is next to worthless. There are many failures that NEVER show up in the SMART data.  Good backups and tested, validated, restore procedures are always necessary - especially when HDDs make funny noises.

Clicking HDDs mean that a drive head could be hitting a platter and destroying data. That stuff is gone, if true. I would pull that drive immediately, swap in a new one and only use it for backups of backups going forward. Data is too important to risk over a _could be failing_ piece of HW, IMHO.

Or it could be a fan hitting a cable.

Can't tell from here.

---

### Post by mastablasta on 2014-05-05
or apparently some Gigabyte motherboards may also make clicking sound and not boot. found a post on some win7 forums where a user had clicking sound after disconnecting the hard disk and replacing the PSU.

the fact that it's not booting (staying on starting BIOS screen not progressing to RAM and disk test) when it's producing sound is worrying. and the clicking sound is not easy to reproduce. if i turn computer off and turn it back on it might not happen. so i gues i need to open the case and leave it open until it happens again and then try to feel the disks.

if only it's the data disk - that one is much easier to replace - system disk needs a reinstall and stuff since i am not 100% sure cloning it will work. :(

---

### Post by TheFu on 2014-05-05
Cloning any Linux install should work, provided the partitioning honors the 4K-sector boundaries. I've NEVER had an issue with this.

If the HDDs are not spinning (unplugged) and you still hear the clicking and it is not from the PSU, GPU, Fan; then it is probably an electrical short arching across the short. NOT GOOD.  "Burn that house down" - not good.  I've only seen this once, at work.  It caused data corruption in our source code from 1 developer's machine, over and over and over. Swapped out the MB under warranty and all was good again.

---

### Post by tgalati4 on 2014-05-05
Check the voltages in the power supply.  Boot to BIOS and look for voltages there, otherwise use a voltmeter.  The clicking disk could be because the power supply is not providing enough current to get the platters to spin up to speed.  The fact that the GPU fan was not spinning is either coincidence or related to an intermittent power supply.

---

### Post by mastablasta on 2014-05-05
i performed a SMART test and nothing unusual popped out. well besides for the elevated heat but that was showing on this disk since long time ago. disk was always relatively cool to the tocuh and there is no noticable heat coming from it. 

as i tried to get ultimate boot CD to boot from multiboot USB and then CD i had a couple of reboots and some cold boots but it not once the clicking re-occured (i must have done at least 8 or 9 reboots). 

computer was on for the whole day prior to that. no issues. fans are quiet (well i cleaned them as best as i could). system fast & responsive. disk is read fast there is no noticable sloweness. 

it seems the clicking appears only after it is off for a while. so i will see what happens if i leave it off again during the night. Anyway this could indeed mean there is a capacitor issue. and quite possibly in the PSU. It's an old computer. i don't have the voltmeter but i will check the voltages in BIOS to see if there is anything unusual. PSU is the most annoying thing to change (appart from the motherboard itself).

---

### Post by mastablasta on 2014-05-06
well i couldn't get into BIOS. the disk clicked 4 or 5 times and then it was all silent. with start screen on (where you choose BIOS, boot menu etc.). this indeed seem to happen only after computer is off for a while. i think i need to hang in there until weekend when i have more time in the morning to do propper testing. the computer is used throughout the day for various activities...

---

### Post by tgalati4 on 2014-05-06
That certainly sounds like a capacitor issue.  When the computer is on it works, but when off for a while, the bad capacitors interfere with the voltage flow making it hard to boot when cold.  It could also be cold junctions--bad solder joints--in the power supply.  When cold they don't conduct, but when hot they work fine.  You can repair yourself if you know how to use a soldering gun and you take some precautions to short the big capacitors so you don't get zapped while working.

---

### Post by mastablasta on 2014-05-10
i am not really skilled with soldering gun (a reason i do not posess it anymore). However this would be capaticor in PSU that is at fault or would it be the motherboards?!

i've managed to make a video to show how this sounds and looks like. at first i boot, and it starts clicking and hangs on first screen. then after clicking i hold the hard reboot button and it continues the boot as if nothing ever happened. here is the you tube video: [http://youtu.be/Xh2Y0DZ_H8o](http://youtu.be/Xh2Y0DZ_H8o)

---

### Post by tgalati4 on 2014-05-10
It sounds like cold junctions in the MOSFET's (metal oxide semiconductor flame-emitting transistors) inside the PSU.  These are the power transistors that are mounted to the heat sink inside the power supply.  When cold, no power flows, but cycle the power a few times and power flows through the cracked solder joints.  This problem is easy to fix, but because PSU's are relatively cheap, it's easier just to change the power supply.  If you continue to have issues after replacing the PSU, then you can assume that your motherboard has issues as well.

Again, it could be bad capacitors in both the PSU and the motherboard.  You have to isolate the components to narrow down the problem.

---

### Post by mörgæs on 2014-05-11
There's no high voltage stored in capacitors in a computer, first of all because it's not likely that there is high voltage DC anywhere. No need for shorting capacitors. 

If you have a flame-emitting transistor (ROFL) there's something seriously wrong. 

FET is an abbreviation of field-effect transistor which is not only used in the powersupply. When they die they don't click.

Mastablasta, the best test you can do is remove the present hard disks and mount a spare. Install Buntu here and run for some time to see if the clicking stops.

---

### Post by mastablasta on 2014-05-11
the clicking is only on boot after i leave it overnight. if i reboot the maschine the clicking stops. if i reboot again or turn it off and back on there is no clicking. the only way to reproduce it is to leave it off for longer period. and even then is not consistent. some day it does this, sometimes it doesn't.

---

### Post by Morbius1 on 2014-05-11
Is this of any use: [Failing Hard Drive Sounds]("http://datacent.com/hard_drive_sounds.php")

It's from a company that provides data recovery services but the sound files they have on that page may help you better define the problem.

---

### Post by mastablasta on 2014-05-12
i was checking those sounds before. i will check them again.

i will also try to boot from USB to see what is going on. perhaps i might obtain an used but working PSU to that it out as well. i just hate there i so much work to find the place of errror. it used to be easy for me to do it but now with kids arround it's hard to get some peace and quiet to think.

i will also perform deep SMART test on larger disk. i bought the same model and at the same time as my brother and his failed suddenly a few weeks ago. it seems it's time for some backups to be remade. i am in the process of getting a more automated backup solution but ofcourse it's all connected with money. the important things already have a copy. but i would like to have something for the less important stuff because if all goes down the drain i would spend plenty of time to "get it all back up and running" (i.e. downloading, installing etc.). my hope is that it is not the motherboard at fault. though it has an old CPU it has served me well. the capacitors on it don't seem to be bulged or leaking.

---

### Post by mörgæs on 2014-05-12
That's a long list of unlikely reasons to the problem. 
As I mentioned I would try replacing the hard disk as a first experiment.

---

### Post by mastablasta on 2014-05-12
i've checkehd the sounds on the website and it shounds like these two:
Western Digital 250GB desktop drive with head crash clicks a few times, then spins down.
Western Digital desktop drive with unstable heads clicks a few times and stops spinning.

in their description.
> Usually this is a sign of damaged or crashed heads and it means the drive needs to be opened in a class 100 clean room environment in order to replace head stack assembly. Don't try to open the drive by yourself - you could damage the platters making your data unrecoverable.
Western Digital drives also have common problem with spindle seizure. Usually this occurs after a fall and the drive either doesn't spin up at all with a siren sound: or starts up with loud noise unable to gain enough rotational speed: .


there is a loud noise on startup and the sound does sound like head crash clicks and a spin down afterwards.
i will try smart test on bigger disk and also i need to get a replacement disk to try it out ( i only have an ATA disk in the other mashcine). i may need to get through the week like this and then on weekend try with USB oot and no disk on. plugging out one by one to see which one is having the issue in starting up. or even USB boot with disks inside. like i said the problem is i can only do this early in the morning as during the daytime computer is being used.

i guess there is no other software that could tell me what is wrong...

---

### Post by mastablasta on 2014-05-13
just tried to boot with USB stick inside but this happens before all that it would seem. as it had no effect and i couldn't select the boot menu. it i sdifficult to test all this since i tcan only be done in the morning. and only once (at the very first boot). the new development is that i need to reboot 2 or 3 times now to get the system to boot.

i perofrmed the SMART tests and system drive does have failure on heat. however i believe it was reporting high heat for quite some time now.

(mostly) System disk SMART report:
google drive link: [https://docs.google.com/document/d/1breHEafWnPZ9b-5s4c6_OX71EIDKUdwkVDyagr4gj2o/edit?usp=sharing](https://docs.google.com/document/d/1breHEafWnPZ9b-5s4c6_OX71EIDKUdwkVDyagr4gj2o/edit?usp=sharing)
```
[COLOR=#000000][FONT=Arial]smartctl 5.43 2012-06-30 r3573 [i686-linux-3.10.4-pmagic] (local build)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]=== START OF INFORMATION SECTION ===[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Model Family: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Western Digital Caviar SE Serial ATA[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device Model: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]WDC WD1600JS-00NCB1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Serial Number:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]WD-WCANMD451028[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Firmware Version: 10.02E02[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]User Capacity:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]160,040,803,840 bytes [160 GB][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector Size:  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]512 bytes logical/physical[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device is:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]In smartctl database [for details use: -P show][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ATA Version is:   7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ATA Standard is:  Exact ATA specification draft version not indicated[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Local Time is:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Mon May 12 20:12:47 2014 CEST[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Available - device has SMART capability.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Enabled[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]=== START OF READ SMART DATA SECTION ===[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART overall-health self-assessment test result: PASSED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]See vendor-specific Attribute list for marginal Attributes.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]General SMART Values:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Offline data collection status:  (0x84)    Offline data collection activity[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] was suspended by an interrupting command from host.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Auto Offline Data Collection: Enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Self-test execution status:  [/FONT][/COLOR][COLOR=#000000][FONT=Arial](   0)    The previous self-test routine completed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] without error or no self-test has ever[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] been run.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Total time to complete Offline[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]data collection:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial] ( 4980) seconds.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Offline data collection[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]capabilities:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]  (0x7b) SMART execute Offline immediate.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Auto Offline data collection on/off support.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Suspend Offline collection upon new[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] command.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Offline surface scan supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Conveyance Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Selective Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART capabilities:        [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x0003)    Saves SMART data before entering[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] power-saving mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Supports SMART auto save timer.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Error logging capability:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x01)    Error logging supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] General Purpose Logging supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Short self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      (   2) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extended self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      (  60) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Conveyance self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      (   6) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SCT capabilities:        [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x103f)    SCT Status supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SCT Error Recovery Control supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SCT Feature Control supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SCT Data Table supported.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Attributes Data Structure revision number: 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vendor Specific SMART Attributes with Thresholds:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ID# ATTRIBUTE_NAME      [/FONT][/COLOR][COLOR=#000000][FONT=Arial]FLAG [/FONT][/COLOR][COLOR=#000000][FONT=Arial]VALUE WORST THRESH TYPE  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]UPDATED  WHEN_FAILED RAW_VALUE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  1 Raw_Read_Error_Rate [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x000f   200   200   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  3 Spin_Up_Time        [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0003   183   181   021[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]3833[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  4 Start_Stop_Count    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   098   098   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2316[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  5 Reallocated_Sector_Ct   0x0033   200   200   140[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  7 Seek_Error_Rate     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x000f   200   200   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  9 Power_On_Hours      [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   051   051   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]36359[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 10 Spin_Retry_Count    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0013   100   100   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 11 Calibration_Retry_Count 0x0012   100   100   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 12 Power_Cycle_Count   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   099   099   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1791[/FONT][/COLOR]

[B][COLOR=#ff0000][FONT=Arial]190 Airflow_Temperature_Cel 0x0022   042   036   045[/FONT][FONT=Arial]Old_age   Always   FAILING_NOW 58[/FONT]
[/COLOR][/B]
**[COLOR=#ff0000][FONT=Arial]194 Temperature_Celsius [/FONT][FONT=Arial]0x0022   089   083   000[/FONT][FONT=Arial]Old_age   Always   [/FONT][FONT=Arial]-   [/FONT][FONT=Arial]58[/FONT][/COLOR]**

[COLOR=#000000][FONT=Arial]196 Reallocated_Event_Count 0x0032   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]197 Current_Pending_Sector  0x0012   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]198 Offline_Uncorrectable   0x0010   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Offline  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]199 UDMA_CRC_Error_Count[/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x003e   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]4118[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]200 Multi_Zone_Error_Rate   0x0009   200   200   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Offline  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Error Log Version: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No Errors Logged[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Self-test log structure revision number 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Num  Test_Description[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Status              [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Remaining  LifeTime(hours)  LBA_of_first_error[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# 1  Extended offline[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Completed without error   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]00% [/FONT][/COLOR][COLOR=#000000][FONT=Arial]36249     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# 2  Short offline   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Completed without error   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]00% [/FONT][/COLOR][COLOR=#000000][FONT=Arial]36245     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# 3  Short offline   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Completed without error   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]00%  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1073     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Selective self-test log data structure revision number 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]4    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]5    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Selective self-test flags (0x0):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT][/COLOR]


```

data disk report:
google drive link: [https://docs.google.com/document/d/1hLusMgFcI1KPxdqN9n4433PcIJ7COSoixyn1uDWa62o/edit?usp=sharing](https://docs.google.com/document/d/1hLusMgFcI1KPxdqN9n4433PcIJ7COSoixyn1uDWa62o/edit?usp=sharing)
```
[COLOR=#000000][FONT=Arial]smartctl 5.43 2012-06-30 r3573 [i686-linux-3.10.4-pmagic] (local build)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]=== START OF INFORMATION SECTION ===[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Model Family: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Western Digital Caviar Green (Adv. Format)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device Model: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]WDC WD10EARS-00Y5B1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Serial Number:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]WD-WCAV5E015619[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]LU WWN Device Id: 5 0014ee 2af536610[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Firmware Version: 80.00A80[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]User Capacity:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]1,000,204,886,016 bytes [1.00 TB][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector Size:  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]512 bytes logical/physical[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device is:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]In smartctl database [for details use: -P show][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ATA Version is:   8[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ATA Standard is:  Exact ATA specification draft version not indicated[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Local Time is:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Mon May 12 23:41:03 2014 CEST[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Available - device has SMART capability.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Enabled[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]=== START OF READ SMART DATA SECTION ===[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART overall-health self-assessment test result: PASSED[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]General SMART Values:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Offline data collection status:  (0x82)    Offline data collection activity[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] was completed without error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Auto Offline Data Collection: Enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Self-test execution status:  [/FONT][/COLOR][COLOR=#000000][FONT=Arial](   0)    The previous self-test routine completed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] without error or no self-test has ever[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] been run.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Total time to complete Offline[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]data collection:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial] (18960) seconds.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Offline data collection[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]capabilities:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]  (0x7b) SMART execute Offline immediate.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Auto Offline data collection on/off support.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Suspend Offline collection upon new[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] command.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Offline surface scan supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Conveyance Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Selective Self-test supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART capabilities:        [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x0003)    Saves SMART data before entering[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] power-saving mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] Supports SMART auto save timer.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Error logging capability:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x01)    Error logging supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] General Purpose Logging supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Short self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      (   2) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extended self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      ( 219) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Conveyance self-test routine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]recommended polling time:      (   5) minutes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SCT capabilities:        [/FONT][/COLOR][COLOR=#000000][FONT=Arial](0x3031)    SCT Status supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SCT Feature Control supported.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SCT Data Table supported.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Attributes Data Structure revision number: 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vendor Specific SMART Attributes with Thresholds:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ID# ATTRIBUTE_NAME      [/FONT][/COLOR][COLOR=#000000][FONT=Arial]FLAG [/FONT][/COLOR][COLOR=#000000][FONT=Arial]VALUE WORST THRESH TYPE  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]UPDATED  WHEN_FAILED RAW_VALUE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  1 Raw_Read_Error_Rate [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x002f   200   200   051[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  3 Spin_Up_Time        [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0027   127   125   021[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]6608[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  4 Start_Stop_Count    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   096   096   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]4594[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  5 Reallocated_Sector_Ct   0x0033   200   200   140[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Pre-fail  Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  7 Seek_Error_Rate     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x002e   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  9 Power_On_Hours      [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   068   068   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]23794[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 10 Spin_Retry_Count    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   100   100   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 11 Calibration_Retry_Count 0x0032   100   100   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 12 Power_Cycle_Count   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   099   099   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1381[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]192 Power-Off_Retract_Count 0x0032   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]41[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]193 Load_Cycle_Count    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   169   169   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]95275[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]194 Temperature_Celsius [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0022   098   094   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]49[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]196 Reallocated_Event_Count 0x0032   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]197 Current_Pending_Sector  0x0032   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]198 Offline_Uncorrectable   0x0030   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Offline  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]199 UDMA_CRC_Error_Count[/FONT][/COLOR][COLOR=#000000][FONT=Arial]0x0032   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Always   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]200 Multi_Zone_Error_Rate   0x0008   200   200   000[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Old_age   Offline  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Error Log Version: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No Errors Logged[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Self-test log structure revision number 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Num  Test_Description[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Status              [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Remaining  LifeTime(hours)  LBA_of_first_error[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# 1  Extended offline[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Completed without error   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]00% [/FONT][/COLOR][COLOR=#000000][FONT=Arial]23794     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# 2  Short offline   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Completed without error   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]00% [/FONT][/COLOR][COLOR=#000000][FONT=Arial]23791     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]-[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]SMART Selective self-test log data structure revision number 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]4    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]5    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]0  Not_testing[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Selective self-test flags (0x0):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  After scanning selected spans, do NOT read-scan remainder of disk.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT][/COLOR]


```

ok so the code tags didn't help as google messed it all up. i iwll try to post better version when i get back home later in the day. i've marked red& bold the part that i got red and bright red on the test.

---

### Post by m-dw on 2014-05-13
Sorry for replying late, but this was the exact symptoms I had with the substandard PSU in my server build.  A ticking sound, disks not spinning and no POST, although for me it completely refused to post no matter how many times I pushed the reset button.

The seller tried the same combination of psu and board and was able to get it to post the first time he tried but then the same symptoms.  I'd vote PSU problems too.

---

### Post by mastablasta on 2014-05-17
it seems it's the disk.

there are 2 disks in the box. let's call them data (3 or 4 years old) and system (close to 10 years old).

I replaced the PSU with a known working one. Same thing doesn't boot, clicking sound... so it's not the PSU.

I unplaged all disk drives and used DVD to boot. it boots no clicking sound, no nothing.
plugged both drives back in to see if it will boot and again clicking and no boot.

unplugged the data drive. turn on the PC and got the clicking sound & no boot. so it appears the system drive is damaged. i am searching for replacement drive and will be creating system images and other backups (i have some less important stuff on it like saved games etc..)

---

### Post by mastablasta on 2014-05-19
ok so now i am in hunt mode for new hard drive and i have two questions:

the drive that is failing also has windowsXP home which i want to move since i am still using it for games. i noticed they do not sell drives with capacity less than 500 GB here, so it means partitions need to be aligned i guess (500 GB might get away with older version i am not sure). i cloned the disk and all partitions using redobackup (parted). if i use 1TB drive for system disk (i am thinking WD blue) would the windows XP system boot? - i plan to clone it there and possibly enlarge the system partition...

can clonezilla clone it bit by bit directly - not to an image but directly to new disk? is this possible? i am askign since the old disk (for now is still working) it just needs a couple of reboots and after that it works quietly and nicely. so i am thinking if it would be possible to somehow just copy bit by bit the old disk onto new one partition by partition (if possible).
_*Edit: i found how to do this with clonezila so onthe first question remains... hmmm and that one is no longer linux question though it is about hardware.*_

---

