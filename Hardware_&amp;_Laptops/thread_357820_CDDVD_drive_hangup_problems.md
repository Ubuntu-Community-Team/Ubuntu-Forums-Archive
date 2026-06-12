---
title: "CD/DVD drive hangup problems"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by kornelix on 2007-02-10
I am looking for advice on the source of nagging CD/DVD problems that seems to be present in all Linux systems. I would like to know whose cage to rattle about this. It is not Ubuntu. The problems must be in the kernel or device driver. 

The problems are the following:

1.  If there is a read error, the drive retries thousands of times, during which time the drive is dead: you cannot eject or unmount or reset (with a software IOCTL command) or do anything. Sometimes, after several minutes, the drive comes back to life, but often it stays dead until the system is rebooted.

2. If a process that is writing to a CD or DVD is killed, or sometimes if there is simply an I/O error, the drive may be left in the hung-up condition described above. Again, nothing short of a system reboot will bring the drive back to life. 

3. In the Gnome desktop environment, the entire desktop and all Gnome applications hang dead during a CD or DVD mount operation, which needs 30 seconds to complete. I don't know if other desktop environments have the same problem.

4. CD and DVD mount operations need 30 seconds to complete, which seems ridiculous.

I have seen these problems over the last two years in several different Linux systems. One common factor is Gnome, but I think the problem is deeper. Console apps like growisofs can also trigger the problems. 

If you have insight, or know where to dig, I would appreciate some advice.

---

### Post by mikeyc45 on 2007-02-13
Problems do appear to be in the kernel.  I am currently using Dapper 6.06 LTS.  Everything was working fine under 2.6.15-26.  When I updated to 2.6.15-27, my dvd drives stopped functioning.  2.6.15-28 soon followed and when I updated to it, thinking there might be a fix for my dvd drives, my sound and scheduling went away in mythtv instead.  When I reboot into M$ Windows 2000, everything works fine, which is why I ignore any advice that there's something wrong with my drives or the firmware.

There have been problems with removeable media in general since the beginning.  I started using the first version of Caldera and have used many other distros on several different computers since.  They all have problems with removable media to some degree or another.

As far as the long waits for a cd or dvd to mount, I've had the same problems with M$ Windows, and it, too, hangs the desktop until the media mounts.  If there's anything wrong with the media, it's reboot time.  Windows is, however, much more reliable with removeable media.

I'm currently booting up with -27 so I can use mythtv, and then rebooting into Windows to write dvd's.  It's a pain in the butt to copy files into the Windows FAT32 partition and then reboot whenever I need to write a dvd.

I will offer this ray of hope - in the beginning, support for printers was a nightmare and that has been fixed quite well with cups.  Setting up video drivers, resolutions, and X was a nightmare, and that has been fixed.

I would also like to say that this is free software that is supported by dedicated enthusiasts.  I think everyone in the Linux and FreeBSD development community is awesome!!!  Thanks everyone.

---

