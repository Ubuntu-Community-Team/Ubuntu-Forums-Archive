---
title: "Building the Supreme Ubuntu Bootdisk for USB/FireWire Externals"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by diverge on 2006-01-10
DaBruGo wrote an [excellent guide on installing Ubuntu to an External]("http://www.ubuntuforums.org/showthread.php?t=80811") USB Device/Hard Drive.  However, for many of us there is one major issue that hasn't been addressed:  What if your BIOS doesn't support USB (or FireWire) booting?

In many cases - if not all - the BIOS lacks the ability to detect the USB external itself.  And because most bootloaders merely identify the location of an operating system - rather than actively scaning for potential storage devices - a standard boot disk is not a solution.

And so we arive at our goal: Build a "Supreme Ubuntu Bootdisk" (SUB) that will allow booting Ubuntu from an external device anywhere, no matter how outdated the BIOS.


The overall method is clear: Have a disk - CD, floppy, or even a local partition - that the BIOS will recognize and attempt to boot to. The SUB would then load drivers and scan all possible devices regardless of whether the BIOS had previously loaded them. Once discovered it will either boot directly to or shift the root location to the detected Ubuntu OS.

Most methods load a modified linux kernel onto the boot disk itself. With the proper configuration this kernel loads device drivers, scans a predetermined list of devices, and then redirects root to the desired location.  Of course, there are alternatives: Build a bootable program analogous to Smart BootManager, find a way to the SUB load EVERYTHING (including the kernel) from the target location, etc.



So for those up to the challenge of making Ubuntu competitive with Damn Small Linux and other distros that already have own supreme boot disks, here are some resources that will be of use in developing the Supreme Ubuntu Bootdisk:


-->  Boot Linux from a FireWire device  <--
(IF NOTHING ELSE, READ THIS!!!)
[http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)

This guide gives two methods, both of which can be used to boot from USB and/or FireWire.  The "Two-Phase Boot" seems the most simple: The kernel stored on the boot disk is booted into the RAM, then "using our mini environment to rescan the SCSI bus, wait for the external disk to be recognized, then switch to using this as our real root and continue to boot."  All you have to do is very slightly customize the kernel and use the PROVIDED SCRIPT to search for and switch to the real goal.


-->  Boot Puppy From USB  <--
[http://www.goosee.com/puppy/boot2pup.htm](http://www.goosee.com/puppy/boot2pup.htm)
[http://www.murga.org/%7Epuppy/viewtopic.php?t=1346](http://www.murga.org/%7Epuppy/viewtopic.php?t=1346)

Two great methods, each slightly different, for booting Puppy from a USB drive.  A great resource if you would prefer to tweak already created code.


-->  Booting Fedora or Debian off of a USB drive  <--
[http://www.simonf.com/usb/](http://www.simonf.com/usb/)
[http://www.lammerts.org/software/kernelpatches/](http://www.lammerts.org/software/kernelpatches/)

Good/more info on alternative method(s), primarily based on using a kernel patch.  The second site contains a version of the patch.


-->  Boot Linux from FireWire on Macs  <--
[http://ubuntuforums.org/showthread.php?t=84131](http://ubuntuforums.org/showthread.php?t=84131)
[http://hansmi.ch/articles/boot-linux-from-firewire](http://hansmi.ch/articles/boot-linux-from-firewire)
[http://ubuntuforums.org/showthread.php?t=3952](http://ubuntuforums.org/showthread.php?t=3952)
[http://ubuntuforums.org/showthread.php?t=91755](http://ubuntuforums.org/showthread.php?t=91755)

Getting more off-target, these provide some good ideas aimed specificly at Mac users.  Whether of use to non-Macs is unknown.  One of the pages actually contains pre-configred code, but previous knowledge of "yaboot" may be helpful.


-->  Smart BootManager  <--
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

Everything we want!  Our dream program!  It does a scan, builds a list, and lets you pick!  Plus additional features.  But it hasn't been updated in years and doesn't support USB booting.

If you want to make a huge splash across the board, update this baby's source to have it scan USB and FireWire before displaying options.  We're talking your product on every rescue disk for every OS.


-->  Make a Ubuntu Boot-CD (Like a boot floppy)  <--
[http://www.ubuntuforums.org/showthread.php?t=19428](http://www.ubuntuforums.org/showthread.php?t=19428)

I don't believes this tells how to make an all-purpose boot disk.  But it does give advice on how to get stuff on CD.

---

### Post by pomalin on 2006-01-10
here in french I put an how to make usbuntu, and isos of bootcd to boot from usb with internal ide hdd, or internal sata hdd, and I will post one bootcd iso based on the live/install dvd, to be able to boot install or live.
[http://usbuntu.info](http://usbuntu.info)

---

### Post by HJB on 2006-02-23
Hi diverge, have a look here. I am sure they might be able to help us.
[http://www.murga.org/~puppy/viewtopic.php?t=3875]("http://www.murga.org/~puppy/viewtopic.php?t=3875")

---

