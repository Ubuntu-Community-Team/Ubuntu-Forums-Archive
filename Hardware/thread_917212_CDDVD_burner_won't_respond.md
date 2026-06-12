---
title: "CD/DVD burner won't respond"
date: 2008-09-11
forum: Hardware
---

### Post by rossbot on 2008-09-11
I am running a fully-updated Ubuntu install on an HP Pavillion a1130n. 

The DVDROM works fine but the burner won't even open up after Ubuntu begins bootup. It opens and closes during BIOS check.

On the desktop there is an icon for a "Blank Disk." There is no disk in either drive.

I am booted in failsafe right now because the graphics settings on Gnome are messed up. But when I boot with Fluxbox (not-failsafe) the drive won't respond, either. I don't think the two issues are related but I'm not sure. I don't want to confuse anybody with related issues, but I really need this burner working and I'd be very grateful for help.

Thanks,

Ross

---

### Post by DoctorMO on 2008-09-14
It sounds like a controller hardware failure.

Have you gone to a command line and typed in 'eject /dev/cdrom' ? come back and type out what is any error messages there where. Remember to replace /dev/cdrom if you have more than one with the right device name.

---

### Post by rossbot on 2008-09-15
$ eject -v cdrom0
eject: device name is `cdrom0'
eject: expanded name is `/media/cdrom0'
eject: `/media/cdrom0' is not mounted
eject: `/dev/hdc' can be mounted at `/media/cdrom0'
eject: `/dev/hdc' is a multipartition device
eject: trying to eject `/dev/hdc' using CD-ROM eject command
eject: CD-ROM eject command succeeded
$ eject -v cdrom1
eject: device name is `cdrom1'
eject: expanded name is `/dev/cdrom1'
eject: `/dev/cdrom1' is a link to `/dev/hdc'
eject: `/dev/hdc' is not mounted
eject: `/dev/hdc' is not a mount point
eject: `/dev/hdc' is a multipartition device
eject: trying to eject `/dev/hdc' using CD-ROM eject command
eject: CD-ROM eject command succeeded
$ eject -v cdrom
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdd'
eject: `/dev/hdd' is mounted at `/media/cdrom1'
eject: unmounting device `/dev/hdd' from `/media/cdrom1'
eject: `/dev/hdd' is a multipartition device
eject: trying to eject `/dev/hdd' using CD-ROM eject command
eject: CD-ROM eject command succeeded
$ eject -v cdrom2
eject: device name is `cdrom2'
eject: unable to find or open device for: `cdrom2'

alright..so i was unsure which device was the one i'm interested in opening, so i opened all the cdrom's. in /media is listed cdrom, cdrom0 and cdrom1. so i tried up to 2. as you can see they all result in "success." but the top drive (the cdrw i'm trying to open) did not open. the cdrom opened, but not the cdrw.

should i try to mount cdrom0 or 1?

---

### Post by DoctorMO on 2008-09-15
No it sounds like you need a new one. Physical damage can do odd things to devices at times.

---

### Post by rossbot on 2008-09-18
As I suspected, the hardware was fine. I reinstalled Ubuntu and I'm now able to access the drive. :lolflag::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by DoctorMO on 2008-09-18
Make sure to report a bug, you'd not want this problem to happen again or to others.

---

