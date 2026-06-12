---
title: "Can't Mount USB Drive Properly"
date: 2009-09-06
forum: Hardware
---

### Post by awesomedeluxe on 2009-09-06
Well I was trying to put a few things on a friend's USB stick for her and the thing wouldn't mount.  It just sat there as a mysterious "USB Drive" and when I double clicked it, it told me it wasn't mounting.  Now, I am not *completely* new to linux, and I thought I was equipped to handle just this sort of problem.  I found the little guy with *fdisk -l *and tried to mount it in the terminal with *sudo mount -t vfat /dev/sdc1 ~/media*.  This seemed to work great until I found that I couldn't access any of the files except as root.

I tried chmod, which it ignored.  I tried chown, which it told me was not allowed (even though I tried it as root, what the heck).  I wasn't really sure what to do at this point, so I read the man page for mount found "-o users" which I tried in the mount command.  No go.

Finally I just restarted my computer.  This didn't help: now my ntfs partition and external hard drive randomly have the same problem!  How on earth?  Somebody please help bail me out of this mess.

---

