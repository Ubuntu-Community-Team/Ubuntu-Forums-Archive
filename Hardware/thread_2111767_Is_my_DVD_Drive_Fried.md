---
title: "Is my DVD Drive Fried?"
date: 2013-02-02
forum: Hardware
---

### Post by RiverwestMatty on 2013-02-02
Hello,

Here is my dilema.  In a nutshell my Laptop's DVD/RW Drive isn't working properly.  After reboot, I can close my drive only once but then it will pop back open after a minute and not want to re-close.  I've searched for a solution but most say it's just dust.  It's not.  I've removed it, cleaned it, re-inserted it, and I still get the same problem.  My computer recognizes the drive as well.  Here are the returns from the following commands:
[B]$ dmesg | egrep -i --color 'cdrom|dvd|cd/rw|writer'
$ more /proc/sys/dev/cdrom/info
$ cd-drive[/B]

Your help is much appreciate.  Please let me know if possible.  Thank you.

**$ dmesg | egrep -i --color 'cdrom|dvd|cd/rw|writer'**

[2.252111] ata3.00: ATAPI: HL-DT-ST DVDRAM GT20F, ET03, max UDMA/133
[2.262490] scsi 2:0:0:0: CD-ROM HL-DT-ST DVDRAM GT20F ET03 PQ: 0 ANSI: 5
[2.267436] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[2.267439] cdrom: Uniform CD-ROM driver Revision: 3.20


**$ more /proc/sys/dev/cdrom/info**

CD-ROM information, Id: cdrom.c 3.20 2003/12/17
drive name:		sr0
drive speed:		24
drive # of slots:	1
Can close tray:		1
Can open tray:		1
Can lock tray:		1
Can change speed:	1
Can select disk:	0
Can read multisession:	1
Can read MCN:		1
Reports media changed:	1
Can play audio:		1
Can write CD-R:		1
Can write CD-RW:	1
Can read DVD:		1
Can write DVD-R:	1
Can write DVD-RAM:	1
Can read MRW:		1
Can write MRW:		1
Can write RAM:		1


**$ cd-drive**

cd-drive version 0.83 i686-pc-linux-gnu
Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
The driver selected is GNU/Linux
The default device for this driver is /dev/cdrom

Drivers available...
  GNU/Linux ioctl and MMC driver     
  cdrdao (TOC) disk image driver     
  bin/cuesheet disk image driver     
  Nero NRG disk image driver         

CD-ROM drive supports some nonstandard or degenerate set of MMC

                       Drive: /dev/cdrom
Vendor                      : &#65533;
Model                       : `yI&#65533; yI&#65533;@yI
Revision                    : 
Hardware                                  : CD-ROM or DVD
Can eject                                 : No
Can close tray                            : No
Can disable manual eject                  : No
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : No
Can hard reset device                     : No

Reading....
  Can read Mode 2 Form 1                  : No
  Can read Mode 2 Form 2                  : No
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : No
  Can read C2 Errors                      : No
  Can read IRSC                           : No
  Can read Media Channel Number (or UPC)  : No
  Can play audio                          : No
  Can read CD-DA                          : No
  Can read CD-R                           : No
  Can read CD-RW                          : No
  Can read DVD-ROM                        : No

Writing....
  Can write CD-RW                         : No
  Can write DVD-R                         : No
  Can write DVD-RAM                       : No
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by RiverwestMatty on 2013-02-02
> **ahallubuntu said:**
> If it is fried, it might be fairly easy to replace and not expensive.  Find the exact part number and check eBay.  On several of my laptops, I can swap out the DVD player by removing one screw.

Ah, the easy way out!  I might as well just do that.  I think the hour I spent trying to correct the problem on my own was worth more than a replacement would have been.  Thanks for the new direction/motivation.

---

