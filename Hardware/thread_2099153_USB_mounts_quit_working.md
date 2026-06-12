---
title: "USB mounts quit working"
date: 2012-12-28
forum: Hardware
---

### Post by wwarren on 2012-12-28
This is a new problem that's shown up in the last month or so that I never have had for the last couple of years.  I have two USB hard drives mounted as /mnt/mybook and /mnt/mybook2.  After a few days of uptime, those mount points are still there, but show no contents.  When that happens, if I reboot, or unmount and remount them, their contents becomes available again.

Ideas as to why?  I'm on Ubuntu 10.04LTS.  The drives are formatted as EXT3.

---

### Post by Bashing-om on 2012-12-28
wwarren; Hi !

As your mount point is in /mnt I assume you are using /etc/fstab to mount the devices.

What pops to mind is in the fstab file the reference is not by UUID and thus the reference may change. 
These tutorials may shed some light:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://myubuntublog.wordpress.com/2009/05/25/auto-mount-usb-hard-drive-at-boot/](http://myubuntublog.wordpress.com/2009/05/25/auto-mount-usb-hard-drive-at-boot/)
[INDENT][INDENT][INDENT][INDENT]HTH <== BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wwarren on 2013-01-29
Being only a beginner with Linux, I had used Webmin to mount those drives.  They were mounted based on the drive label.  I've changed them to mount based on the ID.  I'll run like that for a few weeks and see if the problem keeps happening.

---

### Post by Bashing-om on 2013-01-29
wwarren; Sounds like a plan.

Have you considered a means to monitor the drives conduct?
Like maybe a script to read a file on the drives with a cron job, email you upon failure ?

[INDENT][INDENT]just a thought 
[/INDENT][/INDENT]

---

