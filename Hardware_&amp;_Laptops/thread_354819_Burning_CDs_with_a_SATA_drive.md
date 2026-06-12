---
title: "Burning CDs with a SATA drive"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by Jodokos on 2007-02-06
Hello!

I know, that there are several guides out there, how it should work, but none of them worked for me so far.
Might be someone can help me! After tinkering around with my box for a few days to get everything to work, I'm really tired of it. The burning issue is the last one to solve.  Then I can finally kick windows off my partition.

The problem:
I have a SATA CD/DVD burner and I can't burn.
It doesnt appear in my fstab. But I can use it normally for reading cds/dvds. Discs are automatically mounted upon insertion.

Even empty cds are recognized.

Its located under /dev/sg0 and /dev/scd0

Initially I had the problem with rights, so I changed the access rights and chowned it to the cdrom group.

"cdrecord -scanbus" shows
```

1,0,0   100) 'TSSTcorp' 'CD/DVDW SH-W163A' 'TS01' Removable CD-ROM

```

Upon burning, Brasero shows
```

imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
imager (BraseroBurnSum) set_output
job (BraseroBurnSum) set_task
imager (BraseroBurnSum) get_track
sum (BraseroBurnSum) connect_to_clock
sum (BraseroBurnSum) set_action
sum (BraseroBurnSum) start_progress
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
sum (BraseroBurnSum) set_written
job (BraseroBurnSum) asked to stop
	status	= 0
iter (BraseroBurnSum) stopping
sum (BraseroBurnSum) disconnect_from_clock
iter (BraseroBurnSum) stopped
job (BraseroBurnSum) got out of loop
job (BraseroBurnSum) set_task
Session starting:
	flags			= 16759 
	media type	= 0
	speed		= 56
	track type		= 6
	track format	= 3
	output		= none
job (BraseroMkisofs) set_source
imager (BraseroMkisofs) set_output_type
imager (BraseroMkisofs) set_output
job (BraseroMkisofs) set_task
imager (BraseroMkisofs) get_size
process (BraseroMkisofs) getting varg
mkisofs (BraseroMkisofs) set_action
mkisofs (BraseroMkisofs) start_progress
process (BraseroMkisofs) got varg:
	mkisofs
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_SUTkyJ/brasero_tmp_79H2MT
	-exclude-list
	/tmp/brasero_tmp_SUTkyJ/brasero_tmp_CAI2MT
	-q
	-print-size
process (BraseroMkisofs) launching command
process (BraseroMkisofs) stderr: HUP
process (BraseroMkisofs) stdout: 109835
process (BraseroMkisofs) stdout: HUP
job (BraseroMkisofs) asked to stop
	status	= 0
iter (BraseroMkisofs) stopping
process (BraseroMkisofs) got killed
iter (BraseroMkisofs) stopped
job (BraseroMkisofs) got out of loop
job (BraseroMkisofs) set_task
imager (BraseroMkisofs) get_track_type
job (BraseroCDRecord) set_rate
recorder (BraseroCDRecord) set_drive
recorder (BraseroCDRecord) set_flags
job (BraseroCDRecord) set_source
job (BraseroCDRecord) set_task
recorder (BraseroCDRecord) record
process (BraseroCDRecord) getting varg
imager (BraseroMkisofs) get_track_type
imager (BraseroMkisofs) get_size
cdrecord (BraseroCDRecord) set_action
process (BraseroCDRecord) got varg:
	cdrecord
	-v
	dev=/dev/scd0
	gracetime=0
	speed=56
	driveropts=burnfree
	fs=9m
	tsize=109835s
	-dao
	-data
	-nopad
	-
process (BraseroMkisofs) getting varg
process (BraseroMkisofs) got varg:
	mkisofs
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_SUTkyJ/brasero_tmp_79H2MT
	-exclude-list
	/tmp/brasero_tmp_SUTkyJ/brasero_tmp_CAI2MT
	-V
	Daten-CD/DVD (06 Feb 07)
	-A
	Brasero-0.5.1
	-sysid
	LINUX
process (BraseroMkisofs) launching command
process (BraseroCDRecord) launching command
process (BraseroCDRecord) stderr: cdrecord: Warning: Running on Linux-2.6.17-10-generic
process (BraseroCDRecord) stderr: cdrecord: There are unsettled issues with Linux-2.5 and newer.
process (BraseroCDRecord) stderr: cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
process (BraseroCDRecord) stderr: scsidev: '/dev/scd0'
process (BraseroCDRecord) stderr: devname: '/dev/scd0'
process (BraseroCDRecord) stderr: scsibus: -2 target: -2 lun: -2
process (BraseroCDRecord) stderr: Warning: Open by 'devname' is unintentional and not supported.
process (BraseroCDRecord) stderr: Linux sg driver version: 3.5.27
process (BraseroCDRecord) stderr: cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
process (BraseroCDRecord) stderr: SCSI buffer size: 64512
process (BraseroCDRecord) stderr: cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
process (BraseroCDRecord) stderr: cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
process (BraseroCDRecord) stderr: cdrecord: Drive does not support SAO recording.
process (BraseroCDRecord) stdout: Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
process (BraseroCDRecord) stderr: cdrecord: Illegal write mode for this drive.
job (BraseroCDRecord) asked to stop
	status	= 1
	error		= 10
	message	= "Das Laufwerk scheint beschäftigt zu sein (vielleicht sollten Sie die CD/DVD neuladen)"
iter (BraseroMkisofs) stopping
process (BraseroMkisofs) got killed
iter (BraseroMkisofs) stopped
iter (BraseroCDRecord) stopping
process (BraseroCDRecord) got killed
process (BraseroCDRecord) stdout: NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
process (BraseroCDRecord) stdout:       and thus may have bugs that are not present in the original version.
process (BraseroCDRecord) stdout:       Please send bug reports and support requests to <cdrtools@packages.debian.org>.
process (BraseroCDRecord) stdout:       The original author should not be bothered with problems of this version.
process (BraseroCDRecord) stdout: 
process (BraseroCDRecord) stdout: TOC Type: 1 = CD-ROM
process (BraseroCDRecord) stdout: Using libscg version 'debian-0.8debian2'.
process (BraseroCDRecord) stdout: Driveropts: 'burnfree'
process (BraseroCDRecord) stdout: atapi: 1
process (BraseroCDRecord) stdout: Device type    : Removable CD-ROM
process (BraseroCDRecord) stdout: Version        : 5
process (BraseroCDRecord) stdout: Response Format: 2
process (BraseroCDRecord) stdout: Capabilities   : 
process (BraseroCDRecord) stdout: Vendor_info    : 'TSSTcorp'
process (BraseroCDRecord) stdout: Identifikation : 'CD/DVDW SH-W163A'
process (BraseroCDRecord) stdout: Revision       : 'TS01'
process (BraseroCDRecord) stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
process (BraseroCDRecord) stdout: Current: 0x0009
process (BraseroCDRecord) stdout: Profile: 0x0015 
process (BraseroCDRecord) stdout: Profile: 0x0016 
process (BraseroCDRecord) stdout: Profile: 0x002B 
process (BraseroCDRecord) stdout: Profile: 0x001B 
process (BraseroCDRecord) stdout: Profile: 0x001A 
process (BraseroCDRecord) stdout: Profile: 0x0014 
process (BraseroCDRecord) stdout: Profile: 0x0013 
process (BraseroCDRecord) stdout: Profile: 0x0011 
process (BraseroCDRecord) stdout: Profile: 0x0010 
process (BraseroCDRecord) stdout: Profile: 0x000A 
process (BraseroCDRecord) stdout: Profile: 0x0009 (current)
process (BraseroCDRecord) stdout: Profile: 0x0008 
process (BraseroCDRecord) stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
process (BraseroCDRecord) stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
process (BraseroCDRecord) stdout: Supported modes: 
process (BraseroCDRecord) stdout: Drive buf size : 1582592 = 1545 KB
process (BraseroCDRecord) stdout: FIFO size      : 9437184 = 9216 KB
process (BraseroCDRecord) stdout: EOF
iter (BraseroCDRecord) stopped
job (BraseroCDRecord) got out of loop
job (BraseroCDRecord) set_task
Session error : Das Laufwerk scheint beschäftigt zu sein (vielleicht sollten Sie die CD/DVD neuladen)

```

Other programs (K3B, Gnomebaker) deliver an error like "cdrecord: TAO not supported for this drive". NeroLinux says that the medium is not empty (rw) and should be erased first.

What further information do you need to help me?
If anyone can help me: BIG THX!

J.

---

### Post by Jodokos on 2007-02-07
Although I turned autoumount off (System->Preferences), empty discs inserted, still will be mounted!

So that "turning off automount" doesn't turn it off for the  sata drive or any other drive in my system. Damn!

How can I turn it off temporarily? Completely removing it seems to be overkill, because I still want to use the digital camera, the mp3-player, as well as the external usb disc and some usb-sticks...

---

### Post by Boni2k on 2007-02-07
Hello,
I have exactly the same burner hardware and exactly the same errors with all programs using this cdrecord thing...

Help is appreciated!

Boni

EDIT: Our DVD Drive seems to be incompatible with cdrecord but after this [http://forum.ubuntu-fr.org/viewtopic.php?id=64397&p=2](http://forum.ubuntu-fr.org/viewtopic.php?id=64397&p=2) page it should work with Nero Linux

EDIT2: [http://lists.debian.org/debian-user-german/2006/10/msg02110.html](http://lists.debian.org/debian-user-german/2006/10/msg02110.html) It says that you can forget burning CDs when the Burner is connected to a RAID, that kinda sucks...

---

### Post by Jodokos on 2007-02-12
Ok, "fixed" the issue:

I didnt want to buy a non-raid sata controller. A new ide dvd-burner costs as much as the controller. So I bought a "cheap" IDE dvd burner for 30€

Which works now without any problem.

FINALLY!!
This is the first time, that my complete hardware works in linux (trying since a few years from time to time). This could be the final step away from windows...

---

### Post by Boni2k on 2007-02-12
Hmm, not a good solution for me, but starting Windows once a week is okay...
Anyway congratulation, despite the burner, everything works here, too :)

Boni

---

### Post by robenroute on 2007-02-28
All I had to do was change the group of /dev/sg0 to "cdrom" (was "root", and for some strange reason sg1 was "cdrom") and change the line in /etc/fstab that read "/dev/scd0 ......" to "/dev/sr0 ....."; "sudo mount -a", and Bob was my uncle indeed. Burning without any issues!

Hope this helps

---

### Post by Boni2k on 2007-03-01
I did so but actually k3b tried using /dev/scd0 and I could not change this. Is there a way for this?
I bought a new IDE DVD drive because I even had problems viewing DVDs with this drive.

---

### Post by robenroute on 2007-03-01
It doesn't really matter what the exact device id is, as far as I can judge at the moment. Important is that the correct permissions are set for the device. Have a look at the output of "ls -l /dev/scd0", the device should have owner:group set to "root:cdrom".

In my case, GnomeBaker tried to use device dev/sg0, which had the wrong group-owner setting ("root-root"). I find it strange that GnomeBaker tried /dev/sg0 instead of /dev/cdrom (or even /dev/scd0) as this is the device defined in /etc/fstab.

Come to think of it, I reckon I could change my /etc/fstab line back to /dev/scd0 (instead of /dev/sr0), because GnomeBaker uses /dev/sg0 anyhow.

You say that you can't change something, what exactly can't you change, the fact that K3b uses /dev/scd0 or the owner:group settings for /dev/scd0?

---

### Post by Boni2k on 2007-03-01
boni@boni-desktop:~$ ls -l /dev/scd0
brw-rw---- 1 root floppy 11, 0 2007-03-01 16:40 /dev/scd0
boni@boni-desktop:~$ ls -l /dev/sg0
crw-rw---- 1 root cdrom 21, 0 2007-03-01 16:40 /dev/sg0

Not sure about that. I can't change k3bs access trying to scd0 but as I understand this is not important.
Anyway, please don't put too much effort in it, I will get a new drive soon. But I appreciate your help :)

BTW: Are you able to play commercial DVDs with this drive?

---

### Post by robenroute on 2007-03-01
No problems playing anything (just tried official Out of Africa).

Back to your settings: change the group (chgrp command) of /dev/scd0 to "cdrom" (without the quotes). That should solve your problem.

---

### Post by Boni2k on 2007-03-02
With GnomeBaker I get an 
:-[ MODE SELECT failed with SK=5h/ASC=26h/ACQ=00h]: Input/output error
Error, with k3b the same. According to google this problem is not only on my machine (however only with this Burner)

Quite ugly in my eyes...

---

### Post by robenroute on 2007-03-02
Looks ugly indeed (he said, remaining rather clueless)....

---

### Post by robenroute on 2007-03-04
Have you people had a look at [this]("http://www.ubuntuforums.org/showthread.php?t=217472") thread yet? Perhaps this could help a few people out.

Cheers

---

