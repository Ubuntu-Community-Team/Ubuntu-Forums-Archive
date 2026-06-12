---
title: "Only one user can see the Western Digital My Book external hard drive"
date: 2009-05-02
forum: Hardware
---

### Post by ionFreeman on 2009-05-02
My wife and I just got a fancy new 'Breeze' computer from ZAReason -- Jaunty preinstalled, ext4 file system. We've got this problem, which I don't think we had with the old Dell Dimension 3000, which had been running Ubuntu since, I think, Hardy Heron.

When she mounts the drive, I can't see it. When I mount it, she can't see it. Our laptops are supposed to be syncing to the thing, so this is a problem.

I found this thread ([http://ubuntuforums.org/showthread.php?t=510955](http://ubuntuforums.org/showthread.php?t=510955)), which describes our problem from another perspective, but has no solution -- I couldn't bump it.

I think the drive is mounting in user space, but I'd like it to act more like the CD drive.

Any ideas?

---

### Post by aesis05401 on 2009-05-02
*snip*

Edit: Hmmm.. that IRC link and most all the help links on the page I posted go right back to Ubuntu pages.  I assumed they would have shipped the device with some settings configured for network sharing, you may need to log into the box and check your permissions etc..  Nevermind.. move along - nothing to see here ;)

---

### Post by ionFreeman on 2009-05-02
Thanks, Aesis05401. We can take the laptops out of the equation. On the *local box*, only one of us has access at a time. I rebooted, and she got it again, probably because she had the first login.

I'm thinking this is as simple as an argument to 'mount', or mounting as the root user. Currently, for the user that doesn't have access, I get this:
$ ls /media/external\ drive/
ls: cannot open directory /media/external drive/: Permission denied
$ mount | grep external drive
/dev/sdb1 on /media/external drive type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

So, OK. I try
$ sudo umount /dev/sdb1
$ sudo mount -w -v -t vfat -o users,suid,dev,exec /dev/sdb1 /media/external\ drive/
/dev/sdb1 on /media/external drive type vfat (rw)

And that looks great, right? But, it's a lie. She and I can both list and view files on the drive, but can not write new ones, which would be useful.

---

### Post by ionFreeman on 2009-05-02
So, I figured, why not restore all the original options? And then I found [this page on Basic Linux Operations]("http://linux.about.com/od/linux101/l/blnewbie4_2_3.htm").
$ sudo mount -w -v -t vfat -o users,suid,dev,exec,flush,utf8,uhelper=hal,shortname=mixed,umask=000 /dev/sdb1 /media/external\ drive/
/dev/sdb1 on /media/external drive type vfat (rw,uhelper=hal,flush,utf8,shortname=mixed,umask=000)
$ sudo chmod a=rwx /media/external\ drive/

So... there we go. I think I'm all set.

---

