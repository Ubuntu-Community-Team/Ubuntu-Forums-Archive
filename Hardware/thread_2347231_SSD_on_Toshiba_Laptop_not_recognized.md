---
title: "SSD on Toshiba Laptop not recognized"
date: 2016-12-22
forum: Hardware
---

### Post by dmfssf on 2016-12-22
I have a Toshiba A105-S2194.  The old drive has bit the dust and I am trying to replace it with a PNY SSD. The BIOS (V5.3) recognizes the drive, but neither Ubuntu 16.04 or Knopix 7.2 will.  There is not much in the BIOS to help.  Is there any thing that can be done or is this laptop trash?

---

### Post by yancek on 2016-12-22
> The BIOS (V5.3) recognizes the drive, but neither Ubuntu 16.04 or Knopix 7.2 will

How did you come to this conclusion?  Did it not show with fdisk, blkid or related commands?  More details, please.

---

### Post by oldfred on 2016-12-22
What are the specs on your system?

I had an old A105 purchased a week before Vista came out. It was XP but said Vista ready. 
Satellite A105 Intel Core2 T5500 with 1.5GB of RAM. 
I did run 64 bit Ubuntu 12.04 on it, but it could not run Unity, so I installed fallback.

You may need Lubuntu or Xubuntu. Or perhaps even more lightweight system if Celeron with 1GB of RAM or less.

---

### Post by dmfssf on 2016-12-23
BIOS showed the correct SSD.  Ubuntu and Knopix ran off of CD but did not show the SSD at all

---

### Post by dmfssf on 2016-12-23
The computer is a Celeron M 1.73 GHz 32 bit with 1.3 GiB memory according to Unbuntu. The drive I am trying to install is a PNY CS1311 210 GB SSD SATA drive.  I will try Lubuntu or Xubuntu to see what will happen.

Thanks

---

### Post by dmfssf on 2016-12-23
I have tried Lubuntu 16.10 and Xubuntu 16.04.1 without the SSD being recognized (it does not show up at all).  Since the BIOS shows the SSD as the correct part number (which means to me that it is installed correctly), I suspect there is some problem in the ubuntu distributions that do not recognize that the disk is available.  I am at a loss as to what to do.

---

### Post by oldfred on 2016-12-23
Does system have AHCI mode. You want drives seen in AHCI, not old IDE nor RAID. But very old systems may not have that mode. Do not remember on my old Toshiba.

Can you see drive from gparted on live installer. Not sure if Xubuntu or Lubuntu include gparted or other partition tools.

---

### Post by Bashing-om on 2016-12-23
dmfssf; Hello;

I too just installed a SSD on old hardware. 
For me to get my system to integrate the SSD I had to move the hard drives (spinners) to their own buss controller - separating the SSD from the hard drive path ( I also updated Bios to the latest available) .

How many ports on the SATA controller do you have ?

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by dmfssf on 2016-12-23
The old drive was SATA, not IDE or RAID.  You can see the drive from BIOS only.  Nothing drive at all shows up from Ubuntu/L or X.  I did run gparted from L and X and no drive shows up except the CD that I booted from.  This is a laptop with only one SATA connector for the disk drive.

---

### Post by oldfred on 2016-12-23
Are there any other settings in BIOS?
Some users have reported they had a setting to turn on/off a drive.
Sometimes even settings that do not seem to apply, may.

If BIOS sees drive, then operating system should see drive.

---

### Post by dmfssf on 2016-12-23
The following is all the choices the BIOS has (5.3 is latest BIOS)
MAIN - System date and time changeable; Language changable
ADVANCED - Pointing Devices - enabled ; Built-in LAN -enabled ; Wakeup on LAN - disabled ; Execute-Disable Bit Capablility - Not available ; Legacy USB support - enabled
DISPLAY - Power on Display - Auto ; LCD Display Stretch - enabled ; TV type - NTSC(us)
SECURITY - User Password - clear ; Supervisor Password - clear ; Set user password - [enter] ; HDD User Password Status - Not registered ; Built-in HDD password Select - [user only] ; Set user password - [enter]
BOOT- 1 CD/DVD ; 2 HDD PNYCS1311 SSD ; 3 FDD ; 4 LAN ; 5 USB Memory

These are the only possibilities in the BIOS.  I wonder if the Security label may have something to do with the problem, altho no passwords have been set.

Thanks for looking at this.

---

### Post by oldfred on 2016-12-23
Rarely on the old BIOS systems did a password do much beyond preventing anyone from changing BIOS settings.
But new UEFI systems the password often opens more settings that were hidden before.

Try a full cold boot. Or remove battery, hold power switch for 10 sec to make sure all power is drained. The boot and see if that makes a difference. It sometimes works on new systems, but I do not have a lot of hope on an old BIOS based system. BIOS system normally reset onto drive the necessary info for system to boot.

Are you able to test if drive works on anther system? And that drive does not have some Windows proprietary software that prevents it from working with old system?

---

### Post by dmfssf on 2016-12-24
This is an old laptop.  No UEFI.  No windows software.  The battery died long ago an I run it connected to power without a battery in it.  Unfortunately, I have no where else to connect the drive to.  I have heard that there are cables that will change the micro SATA connector to regular SATA connectors, and I may get one since I have other systems with SATA drives.

---

### Post by Bashing-om on 2016-12-24
dmfssf; Hey ///

Got me guessing too ..
As Bios sees the SSD we "should" be able to see it from some perspective.
Booted up from a liveDVD what returns:
```

sudo fdisk -lu

```
And while booted into the liveDVD, what does the partition editor GParted see ?

With the thought here that there is no file system on the SSD and the system thus has nothing to mount .

[INDENT][INDENT]maybe as simple as that
[/INDENT][/INDENT]

---

### Post by dmfssf on 2016-12-25
Booted Lubuntu and ran fdisk and gparted.  fdisk saw  the following devices (looks like standard memory to me)
sudo fdisk -lu
Disk /dev/ram0  thru ram15 all 64 MiB
Disk /dev/loop0 864.3 Mib
Disk /dev/zram0 688.3 MiB

gparted showed only the DVD /dev/sr0 904 GiB  which was partitioned into /dev/sr0p1 3.53 Gib

---

### Post by efflandt on 2016-12-27
Is it possible to use another computer to check out the drive or install Linux on it (using BIOS, not UEFI)?

Your post prompted me to dig up my old Satellite A105-S4384 from 2006 which has Core 2 Duo T5500 (1.66 GHz I think), originally had 1 GB RAM (upgraded to only 2.5 GB since it had 32-bit WinXP), and 160 GB 5400 rpm hard drive that was no faster than an external USB hard drive. That drive also has old Ubuntu on it, but I forget which version (maybe 10.04?). I previously used that laptop to install an Ubuntu version (maybe 11.10) on an old Intel 80 GB SSD just to see what it would do (about 4 times faster than 5400 rpm drive on SATA1) before moving the SSD to my desktop (currently used for grub and as backup boot system in case my hard drive fails, which it did 3 years ago). That SSD (2X faster than 7200 rpm drive on SATA2, 8X faster than 5400 rpm on SATA1 laptop) on my desktop is currently running 14.04 as a grub/backup boot system.

I have an MSI gaming laptop from Oct 2013 that now fails to even boot to its BIOS splash screen and have been trying to figure out what to do with the Crucial M550 512 GB mSATA I had installed in it for 64-bit Ubuntu 14.04. So I had already ordered an mSATA to 2.5" SATA drive adapter. For some reason that mSATA/SATA adapter is not even recognized in a SATA caddy using USB or eSATA or using a Mini-USB port on the adapter. But it worked for a Toshiba laptop from 2009 that I was updating Windows 7 for someone with no Internet access.

So I thought I would give the mSATA/SATA adapter a shot on the old Toshiba A105. 64-bit 14.04 booted up quickly and quietly with no issues other than having to switch MAC address in wireless settings for wireless to connect automatically. I forgot how nice that screen is, only 1280x800, but clear, sharp, and smooth playing 18 minutes of movie trailers on YouTube in Google Chrome, other than one pause after a commercial. Once the battery is charged, I will have to see how long it lasts with the mSATA SSD.

But with old Intel graphics, it is no gaming machine. So I will have to see how it compares with a year older Dell Inspiron 6400 that I inherited from work, with better, but same speed CPU, same RAM (more if I consolidate the 2 laptops), and faster legacy ATI Radeon X1300 mobile graphics, which can at least play minecraft (unlike the Toshiba A105).

---

### Post by dmfssf on 2016-12-29
Since I was installing a SSD on the Toshiba, I expected it to show up as a disk drive.  Is it possible that it would show up as memory instead?

---

### Post by dmfssf on 2017-01-03
I attached the SSD to a desktop computer running Ubuntu 16.10.  That computer is a dual boot with Windows XP.  Results were the same as on the Toshiba.  SSD showed up on BIOS but not under Ubuntu.  XP saw something and said it was working correctly, but did not show any new disks.  I am beginning to think the SSD is bad.

---

### Post by dmfssf on 2017-01-08
I finally figured out what the problem was.  The SSD must be initialized before Ubuntu will even recognize it.  Since I could not find any way under Ubuntu to do the initialization, I booted another computer with the SSD installed and used Windows XP (of all things!) to do the initialization.  The drive then could be seen on Ubuntu by Gparted and could be formatted.  If there is a way to initialize a new disk under Linux, I would like to know.

Unfortunately, the disk is still not recognized on the Toshiba but at least I can use it on another system (and it is amazingly fast).

---

### Post by oldfred on 2017-01-08
I have purchased two new SSD and one years ago that was small. 
And had no issues with gparted partitioning & formatting them.
Not sure what you mean by initialization?

If you use XP, you may have issues with SSD. But if then partitioned with gparted then it should be ok.
XP started first partition at sector 63, but all new tools since Windows 7 & Linux tools start first partition at sector 2048 and maintain correct sectors for newer drives.

       sudo parted /dev/sda align-check opt 


 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by dmfssf on 2017-01-09
I am not sure exactly what I did under XP.  I was trying everything I could think of.  The problem was that the SSD would not show up in Ubuntu until I used XP.  It would not show in gparted (standalone), xubuntu, lubuntu, or even XP until I hit the right combination.  If it doesn't show up it is impossible to do anything with it.  Once it showed up I had no problems.

I am probably missing something that is necessary for a drive straight from the factory, but I don't know what it is.

---

