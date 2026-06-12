---
title: "USB drive stops responding"
date: 2010-08-16
forum: Hardware
---

### Post by Bakmeel on 2010-08-16
Hello,

I am running a small server with Ubuntu Server 10.04, that is taking care of a few torrents.

The torrents are cached on a Samsung S1 Mini USB drive (120GB model) because the system disk is a bit small to store all the files.

For some reason, the USB drive becomes unreachable after a day or so, but I can't find any info in dmesg or syslog that would indicate it has been unmounted.
If I perform a hard reboot (power off - wait - power on) the disk *sometimes* comes back again.

Does anyone have some experience with USB drives dropping out? Do these S1 drives (or USB drives) tend to shut down for self-protection if they run longer than 24h or so?

Thanks

---

### Post by buddy.johns on 2011-01-11
I'm actually having a similar problem...hopefully someone can help with this issue (even though the thread is old).

I have a laptop running 10.10.  It has 3 usb drives attached and I am using it as a file server.  I use samba and connect to the drives using a MacBook Pro over a wireless network (the laptop is connected to a router configured as an access point via ethernet cable).  The main drive i connect to seems to work fine 24/7 UNLESS I try to access the drive for extended periods of time, usually when read/writes are required.

For example:
I haven't seen the drive fail while serving video files to XBMC (couple hours and mostly simply reading the drive, no significant writing going on).

I OFTEN see the drive fail when I backup my MacBook.  I've seen it with both rsync and timemachine, which both use heavy reads (to check for existing files) and writes.

I've eliminated the hardware by swapping out everything methodically, to include drives, usb drive cases (even different manufacturers) and cables.  The problem follows the procedure, not the hardware.

The previous version of Ubuntu (10.04) had the same issue on this laptop.

To help the originator of this thread:
The only remedy I've found so far is to reboot and this fixes it in almost all cases. however, one of the cases I used while troubleshooting required me to power off the usb drive AND reboot the laptop.  I suspect that this case may not have reset internally when power was removed from the usb port and that the other two I have do reset in this way, thus not requiring the power reset.

Specs:
Ubuntu 10.10
1TB 3.5" internal hard drive
Rosewill SATA/USB case (externally powered)
Wireless network

Any ideas anyone?  This is very problematic when trying to backup unattended!

---

