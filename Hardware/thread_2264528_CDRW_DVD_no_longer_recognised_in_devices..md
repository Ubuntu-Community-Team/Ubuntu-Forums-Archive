---
title: "CDRW DVD no longer recognised in devices."
date: 2015-02-08
forum: Hardware
---

### Post by damien17 on 2015-02-08
Please help me.

My DVD CDRW was working in unbuntu.
But I was having problems ripping cd's.
I have installed rhtyhmbox and Asunder, but could not get either or them to rip cd's.

earlier today I have found this information:

=============================================================
damien@damien-OptiPlex-GX620:~$ wodim –devices 
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'CDRW/DVD SCB5265'
Revision       : 'TD17'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: No such file or directory. Cannot open '–devices'.
damien@damien-OptiPlex-GX620:~$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:        sr0
drive speed:        24
drive # of slots:    1
Can close tray:        1
Can open tray:        1
Can lock tray:        1
Can change speed:    1
Can select disk:    0
Can read multisession:    1
Can read MCN:        1
Reports media changed:    1
Can play audio:        1
Can write CD-R:        1
Can write CD-RW:    1
Can read DVD:        1
Can write DVD-R:    0
Can write DVD-RAM:    0
Can read MRW:        1
Can write MRW:        1
Can write RAM:        1


damien@damien-OptiPlex-GX620:~$  eject device-name 
eject: unable to find or open device for: `device-name'
damien@damien-OptiPlex-GX620:~$  eject  /dev/sr0
eject: unable to eject, last error: Inappropriate ioctl for device
damien@damien-OptiPlex-GX620:~$ eject /dev/sr0
eject: unable to eject, last error: Inappropriate ioctl for device
damien@damien-OptiPlex-GX620:~$ 

==================================================

the drive had stop being recognised as I typed in random suggestions from the internet :

such as :
[My DVD-ROM is not showing up in /media or in mount for Ubuntu 10.10 - Super User]("http://superuser.com/questions/264465/my-dvd-rom-is-not-showing-up-in-media-or-in-mount-for-ubuntu-10-10")

[Asunder CD Ripper — Ubuntu Apps Directory]("https://apps.ubuntu.com/cat/applications/asunder/")

[Authenticate to http://ubuntuforums.org]("https://login.ubuntu.com/mMYRhfgSOYhOdevO/+decide")

[Audio CD not appearing in Rhythmbox / Multimedia and Games / Arch Linux Forums]("https://bbs.archlinux.org/viewtopic.php?id=103711")

[drivers - Cannot view, use, or open CDs or DVDs in Ubuntu 12.04 - Ask Ubuntu]("http://askubuntu.com/questions/144860/cannot-view-use-or-open-cds-or-dvds-in-ubuntu-12-04")

[drivers - Ubuntu won't recognize DVD drive - Ask Ubuntu]("http://askubuntu.com/questions/353803/ubuntu-wont-recognize-dvd-drive")

[Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332")

[Hardware - Post New Thread]("http://ubuntuforums.org/newthread.php?do=newthread&f=332")

[How to re-install dvd-driver in ubuntu - Ask Ubuntu]("http://askubuntu.com/questions/51809/how-to-re-install-dvd-driver-in-ubuntu")

[installing cdrw drive in ubuntu - Google Search]("https://www.google.co.uk/search?client=ubuntu&channel=fs&q=installing+cdrw+in+ubuntu&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=0EjXVN6yGsPH8gewo4DgDQ#channel=fs&q=installing+cdrw+drive++in+ubuntu")

[installing cdrw in ubuntu - Google Search]("https://www.google.co.uk/search?client=ubuntu&channel=fs&q=installing+cdrw+in+ubuntu&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=0EjXVN6yGsPH8gewo4DgDQ")

[Installing Your ATAPI CDRW Drive in Linux]("http://www.troubleshooters.com/linux/cdrw.htm")

[mount - CD/DVD drive not mounted when inserted with Disc of any kind - Ask Ubuntu]("http://askubuntu.com/questions/76860/cd-dvd-drive-not-mounted-when-inserted-with-disc-of-any-kind")

[Mount/USB - Community Help Wiki]("https://help.ubuntu.com/community/Mount/USB")

[[SOLVED] CDROM / DVD Drive not detected or useable]("http://ubuntuforums.org/showthread.php?t=1950008")

[[ubuntu] How do I fix: Unable to mount Blank CD-R Disc Location is already mounted"?]("http://ubuntuforums.org/showthread.php?t=2235496")




Thank you for any help.

my email if needed is [email]damienredmondguitar@gmail.com[/email]

---

