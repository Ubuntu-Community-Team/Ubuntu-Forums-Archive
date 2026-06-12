---
title: "unable to acces already mounted device when switch user"
date: 2009-10-12
forum: Hardware
---

### Post by jirafunky1 on 2009-10-12
Hi everyone !!!
Currently I'm using jaunty in a compaq laptop and it runs pretty slick with the third party hardware drivers enabled.
The thing is if I am on my session and have an external hard drive or a pendrive mounted and I want to switch user, once inside the other user account I can't acces the device.
Hope anyone can help me !!!
Thanks
:guitar:

---

### Post by cwb1627 on 2010-03-04
I had the same issue... maybe this will help.  I had to manually add the mount to the /etc/fstab file.  Then (for some reason) mine kept trying to mount elsewhere... I created a script to unmount, then remount and placed it in /etc/rc2.d.

That seemed to work for me - hope it helps... it might not be the best workaround - but it did work.

---

