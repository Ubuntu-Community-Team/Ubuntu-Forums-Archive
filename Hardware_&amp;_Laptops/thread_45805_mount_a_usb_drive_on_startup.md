---
title: "mount a usb drive on startup"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by Brandon Hoult on 2005-07-01
I am setting up a server that needs to share two usb drives.  I have added the drives to the fstab and they mount with a mount -a from the command line.  The problem is that they do not mount automatically during initialization.  I belive it is may be because they are trying to mount before the USB drivers are installed, but I do not know how to chang this.  I made another file in /etc/init.d with a mount -a in it and added it to the end of rc5.d (99) but it still does not mount.  

Any ideas?

Brandon.

---

### Post by Brandon Hoult on 2005-07-01
I got it working so I thought I would just answer my own question.  I made a file with mount -a in it set it to executable and put it in /etc/init.d then linked it into rcS.d (instead of rc5.d) and it seems to work now.

---

