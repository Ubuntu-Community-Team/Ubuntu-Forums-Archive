---
title: "Fresh Warty = No CDRom / DVD :-("
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by marguz on 2005-03-08
Hey all,
 
I've just reinstalled Warty and applied all the updates.
I can't seem to find my CD/DVD drives. Hal is running, but when I try and mount the devices I get this error "mount: special device /dev/hdc does not exist"

#uname -a
Linux mark1 2.6.8.1-5-686 #1 Sat Feb 12 00:50:37 UTC 2005 i686 GNU/Linux

I run cdrecord and get this......
root@mark1:/home/mark # cdrecord -scanbus
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


I know my devices work as I just removed MEPIS (and well I just used the CD to install Warty).

Hmmmmmm...

---

### Post by llama on 2005-03-09
i had a similar problem. my dvd-rom was missing but my dvd-rw was there..

my solution was to disable the drive in the bios. i set the secondary slave (the dvd-rom) to none.

and as if by magic it appeared in warty! and was still fine in windows too. very very strange tho..

---

### Post by marguz on 2005-03-09
[QUOTE=llama]i had a similar problem. my dvd-rom was missing but my dvd-rw was there..

my solution was to disable the drive in the bios. i set the secondary slave (the dvd-rom) to none.

and as if by magic it appeared in warty! and was still fine in windows too. very very strange tho..[/QUOTE]
 Thanks for the Tip, but that did not work  :-(

Anyother ideas ????

---

### Post by tlwest on 2005-03-10
Running  warty 2.6.8.1-5-686 #1 here

This seems to be a fairly widespread problem - I can see about a dozen posts in the last couple of weeks that report what seems to be the same problem, but seen from different angles. Here's what I've found so far:

The problem seems to be that the hotplug/udev system is not configuring the CD/DVD drives at boot time - the so-called cold-plug scenario. dmesg reports that the CDROMs are being detected, but the special device files in /dev (/dec/hdc, /dev/hdd, /dev/cdroms, etc)  are not getting set up. I can't find any recognizable error messages in the logs, but I'm new to udev so I may not know what to look for.

I tried this to see if it was a driver problem:

stopped udev with
    /etc/init.d/udev stop
/dev/hdc is now present - not surprising, since I'm back to the pre-udev device files
I can now create the symlinks for /dev/cdrom and/or /dev/cdroms/cdrom0 and 1, gnome-cd works, and I can mount and access a data CD. 

Try to restart udev, and it doesn't seem to restart reliably.

Reboot, and I'm back to square one where nothing works.

It looks like a problem with either hotplug/udev, or with one of their configuration files. I haven't yet found a good tutorial on mucking about in the configurations, so I'm going to leave well enough alone for now.

From what I read, this part of the kernel is seeing alot of churn, so the solution, alas, may just be to just live with it until it gets fixed/broken/fixed/broken/fixed.

Other than this, I'm very pleased overall with the ubuntu release.

---

### Post by marguz on 2005-03-10
[QUOTE=tlwest]Running  warty 2.6.8.1-5-686 #1 here

This seems to be a fairly widespread problem - I can see about a dozen posts in the last couple of weeks that report what seems to be the same problem, but seen from different angles. Here's what I've found so far:

The problem seems to be that the hotplug/udev system is not configuring the CD/DVD drives at boot time - the so-called cold-plug scenario. dmesg reports that the CDROMs are being detected, but the special device files in /dev (/dec/hdc, /dev/hdd, /dev/cdroms, etc)  are not getting set up. I can't find any recognizable error messages in the logs, but I'm new to udev so I may not know what to look for.

I tried this to see if it was a driver problem:

stopped udev with
    /etc/init.d/udev stop
/dev/hdc is now present - not surprising, since I'm back to the pre-udev device files
I can now create the symlinks for /dev/cdrom and/or /dev/cdroms/cdrom0 and 1, gnome-cd works, and I can mount and access a data CD. 

Try to restart udev, and it doesn't seem to restart reliably.

Reboot, and I'm back to square one where nothing works.

It looks like a problem with either hotplug/udev, or with one of their configuration files. I haven't yet found a good tutorial on mucking about in the configurations, so I'm going to leave well enough alone for now.

From what I read, this part of the kernel is seeing alot of churn, so the solution, alas, may just be to just live with it until it gets fixed/broken/fixed/broken/fixed.

Other than this, I'm very pleased overall with the ubuntu release.[/QUOTE]
 tlwest,

Thanks for the response. I have stoped and restarted udev, and guess what .................
the dam thing works !? I'm now able to use my dvd and cdrom burner. :-)
I have no idea what will happe after a reboot, but that's ok, as I can live with this.
How sweeeeeeeet is that :-)

Thanks :-)

Yes, I too am VERY pleased with the progress of Ubuntu. I love it!  I love GNOME :-)

Later

---

### Post by dkitty on 2005-04-10
[QUOTE=marguz]I have stoped and restarted udev, and guess what .................
the dam thing works !? [/QUOTE]

Really? How did you do that? Just...

udev stop

udev start

at the terminal?

---

