---
title: "Locked CD/DVD Drive ???"
date: 2009-02-22
forum: Hardware
---

### Post by Credo1970 on 2009-02-22
General Problem Description:
DVD/CD Drive locks up when empty.
Can not open/eject the drive using the drive's eject button nor by using 'eject' software.

So far this only occurs if the drive is 'empty' after having been used one time.

Ubuntu 8.04 LTS
Hewlett Packard XG843
CD/DVD Sony DRU-840A

eject -rv
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/scd0'
eject: `/dev/scd0' is not mounted
eject: `/dev/scd0' is not a mount point
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: unable to eject, last error: Input/output error

eject -sv
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/scd0'
eject: `/dev/scd0' is not mounted
eject: `/dev/scd0' is not a mount point
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using SCSI commands
# Comment: [while it reports as success, it is still closed!
eject: SCSI eject succeeded

I have searched hours for a way to resolve this issue to no avail.  Any ideas on how I can insert fresh media without having to 'reboot' or 'force the drive open' using a paperclip?

Thanks!

---

### Post by donmiguel on 2009-03-24
Hi, did you manage to solve this problem?
Please give me some feedback, as i have the exact same problem!
Cheers

---

### Post by spaceboy909 on 2009-04-26
I do have a work around that doesn't require a reboot or even X restart, so hopefully this will work for everyone.

First, my basic setup and situation:

AMD 64X2 5400
OCZ 2Gb
Gigabyte GA-MA78GM-S2H
WDC WD1500HLFS-0 Velociraptor  and WDC WD5000AAKB-2
**DUAL** LG DVDRAM GH20NS15
Intrepid Ibex  2.6.27-11-generic
Gnome 2.24.1

This is either the first or second time this has happened; I'm not positive.

Far too much time had passed between the last time I used the drives (previous day) and the time that I had the trouble, so there's no way I can recall any steps that might have led to the problem.

Bottom line, **one of my 2 dvd drives** refused to open, either via 'mouse eject' or the button on the drive.  There was no disc in this drive.  The drive light would not flash either.  The other drive ejected normally.

The number of drives displayed by Nautilus was wrong.  It showed 3: The functional one with a disc in it, a 'cd/cdrw' drive, and a 'cdrom' drive.

When 'mouse ejecting', I would get a 'cannot mount/unmount' error.  It also said that there was "probably no media in the drive", which there wasn't.  Attempts to mount, unmount and eject via Nautilus failed.

I tried the **eject** command by itself in the terminal, and it opened the other drive normally.

I then decided to look through the **/dev directory** and see what label I needed to try ejecting the other drive.  There were about 8 of them:  cdrom/1, cdrw/1, dvd/1, dvdrw/1.

I just started at the top, and '**eject -v cdrom1**' did the trick.  Afterwards, the drive seems to function normally and I burned and checked an iso successfully.

For reference, there are a number of others having similar issues.  I searched with the following terms and found many people stuck on this problem:  **_drive_**, **_eject_**, **_unable_**, **_mount_**, **_media_**

---

### Post by sandy8925 on 2009-05-06
I think that's a hardware problem in most cases because I have had the same problem many times whether I was using Windows or Ubuntu. I guess after using it for a long time it gets jammed or something.

---

