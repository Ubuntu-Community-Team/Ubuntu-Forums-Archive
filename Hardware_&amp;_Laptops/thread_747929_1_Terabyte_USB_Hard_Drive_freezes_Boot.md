---
title: "1 Terabyte USB Hard Drive freezes Boot"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by clay3482 on 2008-04-07
I have been using Ubuntu for about a year.  I have it installed on my Desktop, My Laptop, and my 8 year old Daughters Laptop.

We love it - thanks for the great software.

I just bought a 1 Terabyte Hard Drive to use on my desktop computer.  I was able to format the drive, mount the drive, and copy files to and from the drive.  I can watch Video and listen to music stored on the drive.

The problem comes up when I have to re-boot the Desktop.  If the USB drive is plugged into ANY of the USB ports (I have tried all 8) if it is plugged in then Ubuntu will freeze at boot about 3 seconds in.

If I unplug the USB Drive I can boot fine - then once the X-Manager is started I can plug the Drive in and continue like nothing happened.  It is however a pain plugging and unplugging the Drive.

This problem happens on Fiesty, Gutsy, MythBuntu 7.10 and Hardy on the desktop computer.  I have tried them all.  I am officially stumped.

Is there anyone out there who has any clue as to what I can do to fix this problem?

I do not think it is a bios problem as the boot seems to get past the bios loading and only hangs when Ubuntu starts booting.

Thank You so much. 
Clay

---

### Post by tamoneya on 2008-04-07
can you post the contents of /etc/fstab.  It may be trying to do some sort of integrity check on the drive automatically and since it is so large it just takes forever and appears to stall.

---

### Post by sdennie on 2008-04-07
Depending on how you've formatted the disk (ext2, ext3, etc), you may not be cleanly unmounting it when you reboot and so the filesystem forces a check on reboot.  As tamoneya said, with a disk that large, an fsck could very well appear to be a system hang.  Unless you had the disk plugged in when you installed Ubuntu, I don't think it will show up in /etc/fstab though.

I'm not an expert on udev/hal/dbus or whatever subsystem sees the insertion of new media but, it's possible that it's not forcing the disk check once the system is up and running (which is why it seems to work properly after the machine is already up).  What you could try to do would be to plugin the disk after you've booted, unmount it and then manually fsck it.

---

