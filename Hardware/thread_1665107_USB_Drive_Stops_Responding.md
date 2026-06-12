---
title: "USB Drive Stops Responding"
date: 2011-01-11
forum: Hardware
---

### Post by buddy.johns on 2011-01-11
Please note that the following is posted here as a partial answer to an older thread:
[http://ubuntuforums.org/showthread.php?p=10346284#post10346284](http://ubuntuforums.org/showthread.php?p=10346284#post10346284)

I have a laptop running 10.10. It has 3 usb drives attached and I am using it as a file server. I use samba and connect to the drives using a MacBook Pro over a wireless network (the laptop is connected to a router configured as an access point via ethernet cable). The main drive i connect to seems to work fine 24/7 UNLESS I try to access the drive for extended periods of time, usually when read/writes are required.

For example:
I haven't seen the drive fail while serving video files to XBMC (couple hours and mostly simply reading the drive, no significant writing going on).

I OFTEN see the drive fail when I backup my MacBook. I've seen it with both rsync and timemachine, which both use heavy reads (to check for existing files) and writes.

I've eliminated the hardware by swapping out everything methodically, to include drives, usb drive cases (even different manufacturers) and cables. The problem follows the procedure, not the hardware.

The previous version of Ubuntu (10.04) had the same issue on this laptop.

The only remedy I've found so far is to reboot and this fixes it in almost all cases. however, one of the cases I used while troubleshooting required me to power off the usb drive AND reboot the laptop. I suspect that this case may not have reset internally when power was removed from the usb port and that the other two I have do reset in this way, thus not requiring the power reset.

Specs:
Ubuntu 10.10
1TB 3.5" internal hard drive
Rosewill SATA/USB case (externally powered)
Wireless network

Any ideas anyone? This is very problematic when trying to backup unattended!

---

### Post by buddy.johns on 2011-01-14
Update...

I attempted to run a large backup via rsync ssh and the result was the same.  Originally I thought the problem may be related to samba, but that is not the case.

Anyone??

---

### Post by konstandinos on 2011-01-17
Hey buddy

I am having the exact same issue you describe but for seemingly different reasons - so I agree that it is not necessarily a samba issue.

I have an external hard drive enclosure which houses a 300gb SataII drive. This external HD is connected to my laptop (IBM Thinkpad) via a USB cable.

I plug in the HD's USB cable, power on the enclosure and Ubuntu (also 10.10) opens it just fine. I then play a song on the HD (about an hour long song) using Totem Movie Player. All is working fine.

Then randomly - sometimes after 5 minutes, but other times after a couple of hours - the music stops playing. About 3 seconds later a read error pops up on Totem. I also notice that the external HD's icon on the desktop is no longer there (in other words, it is no longer mounted).

I power off the external HD, power it back on, and Ubuntu finds it again and so I play the song again. But the problem repeats itself randomly.

Does anyone have any ideas what is causing mine and buddy's problem?

Thanks,
K

---

