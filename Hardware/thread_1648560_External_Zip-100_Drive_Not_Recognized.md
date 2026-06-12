---
title: "External Zip-100 Drive Not Recognized"
date: 2010-12-18
forum: Hardware
---

### Post by HDTimeshifter on 2010-12-18
I hooked up an external Zip-100 drive via parallel port, but Ubuntu 10.10 doesn't recognize it.  I tried rebooting, and it still doesn't show up in Places/***puter.

My other ***puter with Ubuntu 10.10 recognizes an internal Zip-100 drive and is able to read/write to it.

---

### Post by Tamrac on 2010-12-19
> **HDTimeshifter said:**
> I hooked up an external Zip-100 drive via parallel port, but Ubuntu 10.10 doesn't recognize it.  I tried rebooting, and it still doesn't show up in Places/***puter.

My other ***puter with Ubuntu 10.10 recognizes an internal Zip-100 drive and is able to read/write to it.

Parallel port ZIP drives are too antiquated to be supported. That will not work with Vista or Win7. Your other computer's ZIP drive is IDE. W/c is a universal standard. And should work on all platforms.

---

### Post by HDTimeshifter on 2010-12-19
Really?  I thought Linux is supposed to support legacy devices.  It's only 15 years old.  I don't suppose Ubuntu dropped support of parallel printers also?

---

### Post by efflandt on 2010-12-19
The modules are probably still there, especially if your internal Zip drive works, just as modules instead of built into the kernel.

It may just be a matter of figuring out which additional modules you need to use it on parallel. Under /usr/src/linux-headers-<version>-generic/drivers look through parport, block/paride, ide, and whatever else looks interesting.  While not all mention a Zip drive, some do mention Zip along with LS-120, and I used to run zipslack (Slackware Linux for a Zip drive) from an LS-120 SuperDisk (internal IDE ATAPI), which is a combo 1.44 MB floppy and 120 MB floppy.

So you may get some clue from modules used for your internal Zip drive related to ide-atapi, but you may also need paride and pf modules (but not sure what, if any, options they might need).

I used to actually do networking over parallel ports, because parallel ports using PLIP on LapLink parallel cable was faster than the UART of serial ports using PPP on null modem cable.  But that was a long time ago.

---

### Post by HDTimeshifter on 2010-12-20
I unplugged it from my server, which does not have a floppy drive either.  My 2 other workstations (1 Ubuntu and Windows 7 dual boot and another XP both have and support internal IDE Zip drives).  I was hoping to make use of the drive on the server in the event that my network goes down or otherwise since it only has a DVD drive and I only have a couple of USB drives but about 25 Zip disks.  Oh well, it is already on my pile of extra (obsolete?) computer junk.

I guess hacking to get it to work isn't worth it since I wouldn't really use it except in an emergency.  I would have thought the Ubuntu boot process would have detected it and loaded the appropriate drivers.

---

### Post by gazBoston on 2011-03-11
You should log into a terminal window as root and type:

modprobe ppa

Your parallel-port ZIP Drive should then be recognized.

Might be a good idea to get your stuff off of the disks onto something more portable, as the other users have suggested.

After getting your data, if you want to format the disk to ensure that data cannot be retrieved from it once you discard the disks, you can use the 'disk utility' from the System->Administration->Disk Utility menu to do so.

Good luck!

---

