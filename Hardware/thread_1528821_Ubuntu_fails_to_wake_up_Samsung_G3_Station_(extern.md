---
title: "Ubuntu fails to wake up Samsung G3 Station (external HD)"
date: 2010-07-11
forum: Hardware
---

### Post by BoredBySanity on 2010-07-11
Hi guys

I just bought an external drive, Samsung G3 Station 2 TB. I have formated it to use the ntfs file system because I need to access it from windows machines too.

It works fine until I leave it idle for some time, then the drive goes into power save mode. Which is fine except that it seems that ubuntu cannot wake the drive up again... 

The drive does not unmount, but if I try to access it then nautilus hangs and I will have to force quit the file manager.

If I do not mount the drive after starting up my computer and waits, the drive will also fall alseep and it is not possible to mount it. I can push the mount button in the drive manager but it just hangs...

I'm sorry, I'm quite new to linux and it would probably help with some more info from a log or something, but Im not quite sure how to do that... Any help will be greatly appreciated!

I did try to google but I only found different versions of this solution which doesn't seem to work:
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
Which I guess is not surprising since the allow_restart parameter is already set to 1 on my system.

Anyway, thanks for taking time to read all this nonsense :D

EDIT: BTW the drive is connected by USB.


SOLUTION:

Ubuntu 10.4 does not seem to have this issue.

---

