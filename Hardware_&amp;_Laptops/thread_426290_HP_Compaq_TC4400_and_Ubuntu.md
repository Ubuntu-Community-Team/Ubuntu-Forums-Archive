---
title: "HP Compaq TC4400 and Ubuntu"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by AlexDavidson on 2007-04-28
I've been using Linux for about three years for various things, starting with a Debian server and migrating to Gentoo (there was a stage where every one of my five working computers had Gentoo on it). Recently I switched to using OpenBSD for the server, as part of my decision to use the absolute best tool for the job in future. :P

Which is why I put Ubuntu on my new Tablet PC.

I have to say, I'm very impressed. Tablet, wireless, SATA hard disk; all worked out of the box and the OS installed cheerfully from a USB CD drive. I put Gentoo on my last Tablet, and that runaround involved netbooting just to get it on the disk, and two hours fiddling with X to get the Tablet to work.

So yeah, I'm definitely happy with Ubuntu, with just a few remaining problems:
 * The nipple mouse on this computer is annoying, because I tend to click it accidentally while typing. I need some way to disable it. I'd prefer to leave the touchpad operational, but losing it too would not be much of a problem. The pen is more than adequate.
 * Speedstep doesn't appear to be working. The Gnome CPU frequency applet complains that it's not supported, and attempting to load the required modules throws up a 'No such device' error.

Firstly, the mouse issues. I determined that the nipple mouse maps to /dev/psaux, /dev/input/event4 and /dev/input/mouse2. The XOrg config treats it as just /dev/input/mice, and /dev/psaux is taken to be the touchpad. I disabled both entries in the xorg.conf and it had no effect at all. Both devices still worked.
No idea what else to do here. I have verified that the touchpad and nipple mouse are separate devices. The pad is /dev/input/event2.

Secondly, the Speedstep. The BIOS settings for this machine are stupendously limited, and If frequency scaling is disabled in the BIOS, there's no way to enable it. I guess the thinking is that the fewer options the vendors put in the BIOS, the fewer things the user can screw up, but it's damned annoying when you're trying to do troubleshooting.
I tried poking around in the kernel config. I'm still running a vanilla kernel, but I've downloaded all the tools and source required to build a new one should it be necessary. I'm not used to needing an initrd, so I'm unwilling to pare back the options too much in case I nuke something important.
As far as I can tell, the current kernel has all the ACPI and Speedstep stuff in it, either compiled in or as a module. I don't think compiling more stuff into the kernel is going to solve this.
The CPU is definitely a Core 2 Duo, so it should have support for this stuff.


Thanks in advance for any assistance rendered.

---

### Post by alfem on 2007-05-19
Hi !

I've got one of those tc4400 and I love it. 

Everything works great but cpu scaling and battery capacity. I don't know why, but battery indicator sometimes gets stuck in a number. If you check out /proc/acpi/battery/C1AC/state , acpi parameters also stop moving.

Which Ubuntu are you using ? Mine is an Edgy derivative.

---

