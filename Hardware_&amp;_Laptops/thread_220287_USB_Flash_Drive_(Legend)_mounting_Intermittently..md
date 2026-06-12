---
title: "USB Flash Drive (Legend) mounting Intermittently."
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by casperl on 2006-07-21
I have a USB flash drive that auto-mounts intermittently in Breezy

I have a 2Gb Legend external USB Flash drive.
It mounts Intermittently on one PC with Ubuntu Linux under USB 2.0 but mounts every-time on a second Ubuntu PC with USB 1.0.
The thumb drive is a "high performance" USB-2.0 device.
Initially the drive mounted error-free under Windows-XP (formatted as Ext 3 casper-cow device at present)

lsusb always reports following:
Bus 001 Device 005: ID 05e3:0700 Genesys Logic, Inc. SIIG US2256 CompactFlash Card Reader

Drive is seen by Ubuntu PC as /dev/sdc (or /dev/sdb) dependent on USB port plugged into.

Gnome System > Preferences > Removable Drives and Media settings are all checked ie: Mount removable drives, mount removable media, browse removable media, auto-run programs  (occasionally random checking/unchecking at this point would cause an immediate mount of the flash drive)

dmesg reports:

> 
[4295046.316000] usb-storage: device scan complete
[4295046.394000] usb 5-1: USB disconnect, address 8
[4295051.049000] usb 5-1: new high speed USB device using ehci_hcd and address 9
[4295051.330000] scsi7 : SCSI emulation for USB Mass Storage devices
[4295051.333000] usb-storage: device found at 9
[4295051.333000] usb-storage: waiting for device to settle before scanning
[4295056.334000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 2364
[4295056.334000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4295056.337000] SCSI device sdc: 4093952 512-byte hdwr sectors (2096 MB)
[4295056.339000] sdc: Write Protect is off
[4295056.339000] sdc: Mode Sense: 02 00 00 00
[4295056.339000] sdc: assuming drive cache: write through
[4295056.350000] SCSI device sdc: 4093952 512-byte hdwr sectors (2096 MB)


The USB drive does not automount - supposedly line below is where problem lies:

>>> 4295051.333000] usb-storage: waiting for device to settle before scanning

At this point /dev/sdc (sdb) does not exist.

* The flash drive has to be re-inserted many times before it automounts, which causes an occasional total lockup of all USB access until a restart.
* Restarting Linux does not help.
* Booting with/without flash drive inserted does not help.
* Drive was formatted Fat32 - now reformatted as Ext3 casper-cow device - no difference in automounting problem.
* Putting a mount point in fstab does not help - /dev/sdc does not exist until drive is 'seen' by system and actually automounted.
* Other USB devices works fine on system except for a certain model MMC reader that presents the identical symptoms, while other MMC/SD readers works every time.
* Problem exists on every USB port on specific system

I have trolled Ubuntuforums for a month, searching for every solution mentioned without success. (*,) 

Any suggestions (except for changing OS) will be appreciated.

Thanks

Casper

---

### Post by casperl on 2006-07-27
Since formatting the USB flash drive as a super-cow volume with an Ext3 format, the situation has improved somewhat.

I still have to insert the flash disk repeatedly to be recognised, but lately Ubuntu does recognise the drive after the second (or more) attempts.

---

### Post by philippe_carlo on 2006-07-27
It may pay off to upgrade to Dapper.

---

### Post by absolutomer on 2006-07-31
I'm actually using Dapper 6.06 and also getting this intermittent behavior...

Any advice would be greatly appreciated!

Thanks.

---

### Post by casperl on 2006-07-31
Absolutomer, what is your USB hardware as under GNome / System / Administrator / Device Manager?

It is becoming increasingly a hardware issue that has to do with timing.  If the Legend USB disk is not mounted, but plugged in, I have a 75% chance of the hardware being mounted after re-plugging it in after 5-10 minutes.

My USB hardware is:

Vendor: VIA Technologies, Inc
Product: VT82xxxxx UHCI USB 1.1 Controller
OEM Vendor: Giga-byte Technology
OEM Product: GA-7VAX Mainboard

It appears to be timing related where the USB device is seen as unsettled or not stable on the above hardware.  On a different Ubuntu Breezy PC it is recognised and mounted 100% of the time, even at first boot-up.  In the case of the above hardware, the USB device is mounted 0% of the time at first bootup, 75% of the time on the second insertion.  

DMesg frequently reports the following:

> [4298722.693000] usb-storage: device found at 6
[4298722.693000] usb-storage: waiting for device to settle before scanning


I am going to disable on-board USB and add a PCI usb controller as my next step and will report the results here.

---

### Post by absolutomer on 2006-07-31
I'll take a look at those when I get back home from work.  I'm basically trying to use a 1GB PNY USB flash drive on my IBM T41.

When my laptop was running Windows XP the usb ports were not recognized as 2.0.  I think Ubuntu tried using them as 2.0 (the speed of download from the flash memory, when it was working, was much higher than before).  Perhaps that's where the problem arises.

I read somewhere that maybe setting the ports as 1.1 in the BIOS helps...?

---

### Post by casperl on 2006-08-01
Update:
1) I have upgraded from Breezy to Dapper and the intermittent behaviour continues.  
2) I have disabled BIOS support for USB 2 and left USB 1.1 as the active USB interface.  Immediately the Legend Flash drive was recognised upon bootup - the first time this has happened on this particular system.

My version of Ubuntu now is: Ubuntu 6.06 LTS
My kernel version is: Linux ubuntu 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

---

### Post by KuriKai on 2006-09-07
I have this same problem. I have just put ubuntu on her computer. It detects my "myflash" flash disk but not my sisters 128mb legend flashdisk.
I looked in the bios for usb1.1 options but found nothing. Anyone know another way to fix it?
I am also using 6.06

---

### Post by bbfuller on 2006-09-07
I'm glad I'm not the only one seeing this problem. I have, among others, two outwardly identical Kingston 512MB USB Pens. One automounts every time, the other just once in a while. If the drive does not automount then I too have to restart the machine before USB becomes functional again.

Interestingly a similar IGB Kingston drive never automounts.

The behaviour seems consistent over three machines. A 64 bit Athlon, a 32 bit Athlon and a Toshiba Celeron Laptop. Other nachines that have different Linux distributions on them don't seem to suffer the same problem.

I'll watch the outcome of this thread with interest.

---

### Post by wezlo on 2006-09-11
I have the same problem with my usb 2.0 thumb-dirve and my usb 2.0 card-reader.  My digital camera usb 1 and iRiver player (usb 1) mount ok....this worked fine in breezy but since upgrading to dapper it's been a pain...

---

### Post by skirkpatrick on 2006-09-11
I have a problem with the front USB ports on my desktop.  Evidently the cabling from the motherboard to the front ports is not USB 2.0 compliant and Linux will talk to the drive in 2.0 mode but won't be able to mount it.  It will work fine if I plug it into one of the rear ports.  This happens for either USB Flash drives or USB hard drives.

---

### Post by StanleyPoh on 2006-12-18
I installed Ubuntu 6.10 edgy eft and tried my 512MB Pendrive USB drive. The USB drive cannot be accessed. The same USB drive is tested on several windows XP, it can be accessed normally there but not on the 6.10 edgy.

Then I tried my old toshiba usb2.0 128MB USB drive, Ubuntu 6.10 edgy got it and I can access it without any problem. After that I borrowed one of my friend 256MB USB drive, and I can access it without any problem. Finally I tried the 512MB again, but alas not accessible.

May be Ubuntu 6.10 edgy has a problem accessing large USB drive 512MN and above properly?

Any one can help?

---

### Post by tomoiaga on 2007-02-12
> May be Ubuntu 6.10 edgy has a problem accessing large USB drive 512MN and above properly?

It might be so, or even to badly support some small USB Flash drive vendors. I had/have problems using both a 128Mb ang 1Gb pen drives. The copy speed is also stunning small ... on the windows machine, with USB 1.0 it's much bigger ...

Maybe Ubuntu team will learn how other distributions handle this job and improve it.

A search on this very ubuntuforums regarding USB Flash mount fired tens of results, many of them asking "Why my USB does not automount ?"

I recently saw Mark Shuttleworth on a presetation at Google, saying the Ubuntu developers read forums to see what problems users encounter. Well, this is one of them, definitely, properly supporting and automounting Flash Drives.

---

### Post by tmastran on 2007-02-14
In my experience USB support is hit or miss on all Linux versions I have used. I'm running Ubuntu+KDE on on Dapper (IA32) and Edgy (AMD64) and the same memory sticks and camera flash card readers that are detected every time from Windows on the same hardware is spotty when booted into Linux. There is a 90% chance that the USB devices will be detected (and maybe auto mount) directly after a reboot. There is a 5% chance that they will be after the system has been running a while.

I've described this before:
[http://www.ubuntuforums.org/showthread.php?t=318019](http://www.ubuntuforums.org/showthread.php?t=318019)

I'd love to jump in help debug this but don't know where to get started.

---

