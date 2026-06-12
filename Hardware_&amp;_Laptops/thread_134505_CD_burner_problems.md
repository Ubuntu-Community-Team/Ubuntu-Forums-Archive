---
title: "CD burner problems"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by David Valentine on 2006-02-22
I have hunted through the Ubuntu WIKI and the forums, and I haven't been able to find a a solution to my issue (although I did find a lot of unresolved similar issues, which is a little scary).  I cannot get Ubuntu to burn CD's on a Cyberdrive CW068D CD burner on either of two PC's that have one.  On my dual-booting work PC, it's the only burner, and when I boot into WinXP it burns fine.  On my home PC, I also have a DVD burner installed, and it burns fine under Ubuntu, the but the Cyberdrive does not.  Thus at work I know my Cyberdrive is OK; at home, I know Ubuntu can successfully burn a CD but not on the Cyberdrive.  I think I can safely conclude that there is an incompatibility between my Cyberdrive CW068D burners and Ubuntu.  I have tried to get cdburner and cdrdao to help inform the situation.  Here is what I get from typing```
sudo cdrecord -scanbus dev=ATAPI
```> Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
However, if I type```
sudo cdrecord -scanbus dev=ATA
```I get> cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hda'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
The odd thing is that it keeps trying to open hda, but my burner is hdc, and I get the same "device or resource busy" errors from typing ```
cdrdao scanbus
```.  Do I need to go buy a new burner, or can someone shed some light on this?

---

### Post by mravik on 2006-05-05
Try 

sudo cdrecord dev=/dev/hdd -scanbus

or change hdd to hdc depends on where you have connected the burner.

---

