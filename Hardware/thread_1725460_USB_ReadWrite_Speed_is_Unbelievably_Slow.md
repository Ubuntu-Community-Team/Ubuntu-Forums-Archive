---
title: "USB Read/Write Speed is Unbelievably Slow"
date: 2011-04-09
forum: Hardware
---

### Post by PythonEater on 2011-04-09
Hey there. For awhile now, any file transfer, or access to a usb device (4 flash drives and an external hard drive tested) have been believably slow. I noticed it when I made the switch over from Arch to Ubuntu to try out the new Unity interface (love it by the way, nice work to all the devs). I tar'd all my files in the home directory, and tried moving it to a hard drive. It was a single 5.7 GB file, and it took about 4 hours to transfer.

I'm not sure where to start troubleshooting what might be a hardware problem or a kernel problem, but I know that it happens on both Arch and Ubuntu (11.04 64bit).

Any help would be greatly appreciated. Thanks a lot! :D

---

### Post by PythonEater on 2011-04-09
bump

---

### Post by PythonEater on 2011-04-10
b-b-b-bump!

---

### Post by Spechal on 2011-04-10
My transfers are not slow, but it will get to the last .5MB of 213.9MB and just sit there for a few minutes then finish.  Highly annoying.  Happens with flash drives and USB HDDs ... been that way since I started using Ubuntu on 9.something.

Bump!!!

---

### Post by orethrius on 2011-04-10
I think a good starting point would involve the vendor / model information of the devices experiencing the problem, even if it's "all devices"; for instance, Broadcom had an entire *series* of wireless cards with non-proprietary issues, and the same applied to nearly a decades' worth of softmodems.

Every bit helps. :)

EDIT: Additionally, the vendor / model of the system in question wouldn't hurt, either. ;)

---

### Post by Spechal on 2011-04-11
OS: Ubuntu 10.04 TLS Desktop x64
GUI: GNOME 2.30.2
CPU; AMD Phenom x4 9500
Chipset: AMD 780G


USB devices:
WD Elements 1TB HDD with HPFS/NTFS filesystem.
Generic 1GB, 4GB and 16GB flash drives with FAT32 filesystem.

If you can help me find more information on the generic flash drives (micro center brand), I can provide more information.

Thanks.

---

### Post by gradinaruvasile on 2011-04-11
How was the speed in Arch?

---

### Post by PythonEater on 2011-04-11
The speed in Arch was exactly the same.

The system in question is a HP G60-249WM, and the specs for it can be found [here]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4621295") (I'm not sure all of what you need)

As for the devices I'm experiencing issues with, I can't get you the model numbers/part numbers, because I don't have them :P But, the hard drive is a 1TB External Hard Disk Drive from Western Digital, one of the flash drives is a 16GB SanDisk cruzer, and the other is a 4GB SanDisk cruzer. The devices are working properly, as they work on other machines as expected.

EDIT: If it matters, the External HDD is formated as NTFS, and the flash drives are formated as FAT32.

---

### Post by PythonEater on 2011-04-11
> **Spechal said:**
> My transfers are not slow, but it will get to the last .5MB of 213.9MB and just sit there for a few minutes then finish.  Highly annoying.  Happens with flash drives and USB HDDs ... been that way since I started using Ubuntu on 9.something.

Bump!!!

I think that's actually an issue with Nautilus' file copy dialog. I don't think that it's accurately measuring the time that is left. None the less, it's an unrelated problem, so you should open a different thread in (I may be wrong on the proper section) General Help.

---

### Post by PythonEater on 2011-04-12
*bumps*

---

### Post by gradinaruvasile on 2011-04-12
Did you try copying in a terminal?

---

### Post by PythonEater on 2011-04-12
Yep, as well as with Dolphin, Nautilus and Thunar.

---

### Post by PythonEater on 2011-04-12
*bump to first page*

---

### Post by PythonEater on 2011-04-13
Moar bump

---

### Post by PythonEater on 2011-04-13
I'm going to try an older Linux distro to see if it's a problem caused by new software. If this is the case, where should I move this to?

EDIT: After booting into Ubuntu 8.04, the read/write speed issue was fixed. I suppose the next test would be to download Natty for i686 and see if this happens across architectures, as my 8.04 disc is 32bit.

---

### Post by Roknrolzombie on 2011-04-18
> **PythonEater said:**
> I'm going to try an older Linux distro to see if it's a problem caused by new software. If this is the case, where should I move this to?

EDIT: After booting into Ubuntu 8.04, the read/write speed issue was fixed. I suppose the next test would be to download Natty for i686 and see if this happens across architectures, as my 8.04 disc is 32bit.
Find any solutions on this?  I've been running into what I believe are similar problems over the last few days, although if this does not appear to be the same as your issue, please let me know so that I can find a better thread to post this in:

USB 2.0 4TB JBOD ext4 - it appears to connect as a USB 2.0 drive

kern.log
```
[ 1156.692058] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 1156.827383] scsi10 : usb-storage 1-3:1.0
[ 1157.825226] scsi 10:0:0:0: Direct-Access     WDC WD20 EARS-00MVWB0          PQ: 0 ANSI: 2 CCS
[ 1157.826364] sd 10:0:0:0: Attached scsi generic sg5 type 0
[ 1158.039704] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[ 1158.040177] sd 10:0:0:0: [sde] 7814058336 512-byte logical blocks: (4.00 TB/3.63 TiB)
[ 1158.040922] sd 10:0:0:0: [sde] Write Protect is off
[ 1158.040930] sd 10:0:0:0: [sde] Mode Sense: 00 38 00 00
[ 1158.040936] sd 10:0:0:0: [sde] Assuming drive cache: write through
[ 1158.253689] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[ 1158.254922] sd 10:0:0:0: [sde] Assuming drive cache: write through
[ 1158.254937]  sde: sde1
[ 1158.560797] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[ 1158.573672] sd 10:0:0:0: [sde] Assuming drive cache: write through
[ 1158.573684] sd 10:0:0:0: [sde] Attached SCSI disk
[ 1159.822214] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)

```I notice that immediately after connecting the drive I can transfer a couple of gigs very quickly -  2gig folder transferred in about 3 minutes...nice and fast.  I was able to copy a couple of files about that size, and then the next batch of files I try to copy hangs at about 30 megs and doesn't progress beyond that.  If I leave it run, it *may* transfer another 50 megs or so, but that takes hours.  File size does not seem to be the problem, as stopping the copy (making sure that nautilus isn't in "Uninterruptable" state), attempting to transfer smaller files (<300 megs) hangs right around the 30Mb point as well.

I have tried both Nautilus and Dolphin, as well as cp and rsync to transfer the files (I'm attempting to migrate data from a different volume with a failing disk).
**(Note: I am testing the process by copying from a local (good) drive to the USB drive, rather than from the failing Share, so the other failing disk is not affecting this issue)

Not sure what info you guys may need from my PC, but below is what seems to make sense :)

Ubuntu 10.10 Maverick - 2.6.35-28.  Upgraded TO Maverick to see if it would resolve this problem, so the problem existed in 10.04 as well.

Motherboard: ASRock M3A780GXH
---------------------------

I'd never noticed this problem with smaller USB drives, but then again, whenever I use those it's usually for small files.

It's *acting* like it's filling a buffer somewhere and either not clearing it properly, or getting hung up with secondary/tertiary files or something.

I'm not a complete noob - I can find my way around the system and I'm perfectly comfortable with the command line, but I'm having a helluva time trying to nail this down.  I've attempted to install a variety of USB modules to correct the issue, but none of them have worked.  I've also attempted to change the I/O scheduler to the drive, but there doesn't seem to be a significant change (file transfers were slower with noop, but they would hang and get really slow at about the same time).

I'm no idiot, but drilling down to the hardware level is a little beyond me...I don't feel quite comfortable just guessing.

Any help would be appreciated - thanks!

James

---

### Post by buksy on 2011-04-27
Hey, any news? My usb transfer speed is so slow too, I'm forced to boot windows to copy files on usb 'coz it takes about 10times less time.

---

### Post by Roknrolzombie on 2011-04-27
> **buksy said:**
> Hey, any news? My usb transfer speed is so slow too, I'm forced to boot windows to copy files on usb 'coz it takes about 10times less time.
Nope, nothing new here...even less that's helpful...

---

### Post by fgr on 2011-05-10
I just have the 'slow read' problem with my card reader and sd cards since update to 11.04. read/write from/to usb hard disk is fast as ever.

I read from my card reader less then 900 KB/sec, and it is a fast sd card!

card reader: O2Micro Card Reader (Dell Studie 1747)

with 10.10 I watched HD videos from the sd card, now thats impossible.

any solutions?

---

### Post by fgr on 2011-05-10
> **fgr said:**
> I just have the 'slow read' problem with my card reader and sd cards since update to 11.04. read/write from/to usb hard disk is fast as ever.

I read from my card reader less then 900 KB/sec, and it is a fast sd card!

card reader: O2Micro Card Reader (Dell Studie 1747)

with 10.10 I watched HD videos from the sd card, now thats impossible.

any solutions?

tried it with windows 7 (2.nd boot partition on same laptop) and the files from the sd card were copied in 3-4 seconds, instead of 3-4 minutes with ubuntu.

---

### Post by Clancy_s on 2011-05-29
It's been happening to me too, since about 9.10 (I started with 7.10), now sitting on 10.04 64 bit since I don't need to be cutting edge.  All updates are installed, it's gotten worse in the last few days, in that the last few Mb take longer (haven't actually measured it) and the files are corrupt.

Tranfer is working find under Vista and was fine under ubuntu 'til around 9.10

Toshiba satellite A200/s01

OS: Ubuntu 10.04 TLS Desktop x64
GUI: GNOME 2.30.2
CPU; Intel Core 2 Duo 2.2 Ghz T7500

---

