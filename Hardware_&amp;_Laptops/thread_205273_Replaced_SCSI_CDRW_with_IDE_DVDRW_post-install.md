---
title: "Replaced SCSI CDRW with IDE DVDRW post-install"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by sorceror on 2006-06-28
I'm trying to figure out how to configure my new hardware after the main Ubuntu install. Ultimately, of course, I want to burn CDs and DVDs.

A couple weeks ago I did a fresh install of Ubuntu 6.06. Among the hardware present was a Hitachi DVD-ROM drive and a SCSI CDRW, TEAC model "CD-W512SB". All was well, things worked fine.

 A couple days ago I finally got a chance to actually install my Father's Day present, an LG DVD+-RW drive, model "GSA-4166B". I pulled the CDRW (and the SCSI card) and put in the new, IDE drive. So, right now, I have:

 hda: 120GB IBM deskstar
 hdb: Hitachi DVD-ROM
 hdc: 120GB IBM deskstar
 hdd: LG DVD+-RW

 It works to read media. I can insert stuff and it mounts. I've got DMA enabled on it, even. But when I try to detect it, I get problems. I gather from the docs that I shouldn't use "ide-scsi", I should use "ide-cd", and I should preferentially use "dev=ATA" with cdrecord.

 I modified my Grub menu.lst to add the kernel options "hdb=ide-cd hdd=ide-cd", but with or without this, I get the messages below:

-----------------------
# cdrecord dev=ATA -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004
Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to
<cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-25-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.

Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)...
retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hda'. Cannot open
SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
# cdrecord dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004
Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to
<cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-25-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg
(debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright
1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) *
        0,1,0     1) 'HITACHI ' 'GD-2000         ' '0056' Removable CD-ROM
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) *
        1,1,0   101) 'HL-DT-ST' 'DVDRRW GSA-4166B' '1.00' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

-----------------------

 Running "cdrecord -scanbus" just shows my USB media readers, which as expected show up as SCSI disks.

 So, it appears that the "ATAPI" interface mostly works, but is it really DMA-less? That would be bad. On a fresh install, what does Ubuntu do with an IDE burner? How is it configured?

 No, I haven't actually tried to burn anything yet. I'm trying to make sure the hardware's in a sane state first. What kind of tests can I run or is there any other information I could gather that'd be helpful? Is there a newbie guide I missed in my Googling?

---

### Post by GTvulse on 2006-06-28
Methinks you're confused... If it is SCSI DVDRW, it ain't an IDE device. Thusly it is not a /dev/hd* but a /dev/sd*. In the case of cdrecord, when working with SCSI devices, it locates them by their LUN bus address:
```
cdrecord dev=1,1,0 blah
```
I know that's a buch to type, but you can always set up an alias in /etc/default/cdrecord.

And btw, the passthough trick you used was the only way to have cdrecord work with 2.4 kernels. It is deprecated with 2.6 kernels and in fact you are hurting performance by doing it. Read the documentation in /usr/share/doc/cdrecord, in particular README.Debian.

---

### Post by sorceror on 2006-06-28
> Methinks you're confused... If it is SCSI DVDRW, it ain't an IDE device. 

No, no, the *old* CD-burner was SCSI. The *new* DVD-burner is IDE. Since I physically removed the SCSI card from the machine when I took out the old CD burner, I'm *quite* certain the new DVD burner is IDE. :)

---

### Post by sorceror on 2006-06-28
Hey, I did look in /usr/share/doc/cdrecord, and found "README.ATAPI.setup.ubuntu". This just might be what I need (and didn't find in my Googling). I'll see if I can't make this thing work tonight. Thanks!

BTW, anyone got recommendations for DVD burning software?

---

### Post by GTvulse on 2006-06-28
The dvd+rwtools utilities do a pretty good job, gwowisofs in particular... For a graphical interface K3b (KDE), Graveman (GTK) and Gnomebaker (Gnome) are good. Many swear by K3b, but I can't give you an educated opition; nautilus-cd-burner does most of what I need, else I just go to the console. :-)

---

### Post by sorceror on 2006-06-29
Good news, I was able to use the burner last night with cdrecord and growisofs, and burned a valid CD and a valid DVD. Specifying the device name directly, i.e.:

 cdrecord dev=/dev/hdd -scanbus

 ...produces useful info, and apparently uses the SCSI API.

 Interestingly, though, I have a new problem. Not a critical one, but... my DVD-ROM drive only works for data now. I can't get libdvdread to use /dev/hdb. I can play a movie from /dev/hdd (the DVD+-RW drive) but I can't play a movie from /dev/hdb (the old DVD-ROM drive). I *know* it worked before.

 Can anyone point me to some info about libdvdread and why adding another DVD drive would cause it to fail with a drive it's used before?

---

