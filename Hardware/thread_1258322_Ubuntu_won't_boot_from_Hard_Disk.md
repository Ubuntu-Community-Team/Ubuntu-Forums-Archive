---
title: "Ubuntu won't boot from Hard Disk"
date: 2009-09-04
forum: Hardware
---

### Post by Trent T on 2009-09-04
My Sad Story:
My wife turned off the Ubuntu 8.0.4 computer at the power switch one day.  When she called me in to fix it, I saw a black screen that kept repeating something like;

"Insert disk or media with some sort of OPERATING SYSTEM on it the next time you start up, OK??"  [not the computer's exact words]

BIOS told me that my 6-year-old IDE 200 GB hard drive now had a physical drive space of "0".  Oh well..

I installed a new SATA drive and, with the help of the Ubuntu 9.04 Jaunty Jackalope CD, formatted it to Ubuntu.  

When I try to boot from the new HDD, I get the black screen of death with a blinking cursor about 2 cm down from the top.

Other Problem:

On boot-up, I hear two short beeps of distress from the AMI BIOS.  
Could it be a parity error?  How would I tell?
Could my wife have damaged the BIOS??  Hmmm...

Things I Have Tried So Far That Did Not Work, But Should Have:

Moved HDD SATA Cable to the other 3 slots.
Tried fixing it with Super Grub.
Tried a different SATA HDD--in all SATA slots.
Tried changing SATA Cable.
Tried putting each 1 GB DIMM SDRAM in slot 1 (to test for bad memory).

Things It Can Still Do, But Should Not Be Able To:

It boots from the Ubuntu 9.04 Disk.  
     I (mistakenly?) believe that, if I had bad memory/parity error, OR BIOS damage, it should not boot at all.

When running from the CD in "Live Session User" mode, I can see all the new Ubuntu 9.04 directories on my new SATA drive.  I can copy sample files from the new HDD to a flash drive.  I can connect to the internet.
Jaunty Jackalope is THERE in all its crunchy goodness :popcorn: --The only thing it won't do is start up from my HDD.

Questions For The Studio Audience:

Any ideas on what to try next?
Flash the BIOS, perhaps? 
Replace the motherboard?
[I have already respectfully asked my wife to keep her lightning-bolt fingers away from the power switch...] 

All suggestions gratefully considered.

--Trent T.

My system:
OS:  ubuntu Linux 9.04 - Jaunty Jackalope
Motherboard: MSI MS-7366, version: 1.0 width: 32 bits
Firmware BIOS: American Megatrends Inc. version: V3.3 ( 03/07/2008 )64KiB
CPU Intel(R) Celeron(R) CPU  E1200  @ 1.60GHz version: 6.15.13 1600MHz @200MHz
Memory DIMM SDRAM Synchronous 2 GiB width: 64 bits
Audio-Motherboard: MCP73 High Definition Audio, nVidia version: a1
Audio-add-in: SB Live! EMU10k1 by Creative Labs, V.7 33MHz
Hard Drive: Seagate ATA - ST3160815AS size: 149GiB (160GB) partitioned:dos
            configuration: created=2009-09-03 02:15:45 filesystem=ext3 modified=2009-09-03 03:21:47 mounted=2009-09-03 03:21:47 state=clean
            
CD/DVD Read/Write: SATA HP DVD Writer 1070d

Printer - HP Photosmart C4400

---

### Post by Trent T on 2009-09-05
Mike/compurepair at [www.fixya.com](www.fixya.com) solved it;


Compurepair
Compurepair

Rank: Wiz 
Rating: 84.01% , 731 votes
Hi,

Parity is a memory ( Ram problem ) try removing 1 Stick. or changing it into another slot. if you suspect Bios. remove power cable. locate The CMOS Battery. remove for 10-15 seconds, And replace it. this will reset the bios to it,s default settings. you,ll know if your asked on boot-up to run setup to change time/date.

Mike @ Compurepair.

=================

When I popped out the CMOS battery, it was severely corroded.  I replaced the battery, re-entered the time and date, and the system booted right up!

---

