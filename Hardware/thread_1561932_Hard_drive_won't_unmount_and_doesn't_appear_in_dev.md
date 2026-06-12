---
title: "Hard drive won't unmount and doesn't appear in devices"
date: 2010-08-26
forum: Hardware
---

### Post by theluddite on 2010-08-26
So about once every few days my Lacie external HD will stop working, without any noticeable pattern.  For seemingly no reason, when I try to ls the mounted directory I get 

> ls: reading directory /media/Primary/: Input/output error

The drive is getting old so that's not really the problem.  The real pain is that I can't umount no matter what I do.  I've tried lsof | grep mountpoint, I've tried umount -f and I've tried just shutting down the drive but the device stays mounted until I reboot.  I've run e2fsck and the device shows no errors.  Any suggestions on what's going wrong or how I can force the umount of a failing drive?

---

### Post by theluddite on 2011-03-16
I'm still having this problem.  

As an aside, it seems like the drive wasn't failing after all.  Now I think the problem may have been due to too many files in a few folders.  I would often run gthumb image viewer as a slideshow in the background as I used the terminal.  In any of the folders I'd use for the slideshow there were 1000+ images.  I'm thinking maybe the argument list was too long for gthumb or my RAM?  Anyway, I used a script to resort the images into 10 subfolder and so far I haven't had the problem that caused the I/O error -- but I'd still like any suggestions on how to really force the umount of a drive.

---

