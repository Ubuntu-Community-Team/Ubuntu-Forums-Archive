---
title: "video device permissions?"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by brickbat on 2005-06-10
Hi,

I cannot get kino to see me video device unless I run it with sudo.  I prefer not to do this because then all the files it generates are only editable by root.  What command can I use to make it run as a normal user and see my device?

The info below may help.

brickbat@lpc1:~$ ls -l /dev/raw1394
crw-------  1 root video 171, 0 2005-06-07 21:53 /dev/raw1394

brickbat@lpc1:~$ sudo lsmod | grep 1394
dv1394                 19788  0
raw1394                28652  0
ohci1394               31876  1 dv1394
ieee1394              100408  4 dv1394,raw1394,ohci1394,sbp2

btw, could someone please explain what this means? That would be nice too.

ciao
bb

---

### Post by skoal on 2005-06-11
Using "vi" (or even something like gedit), open up the file "udev.persmissions":
```
skoal@morpheus://~ $ sudo vi /etc/udev/permissions.d/udev.permissions
```
Look for "raw1394" (about line 80), and change it to:
```
raw1394:root:video:0660
```
Your normal user should already be a part of the "video" group, so reboot and you're good to go (I guess).  I don't know what your software needs or looks for, but at least that will change those permissions for that device.

\\//_

---

### Post by brickbat on 2005-06-11
Thanks,

I have made the change but I can't reboot at the moment.  I'll let you know if it worked.

ciao
bb

---

### Post by oofnik on 2005-06-28
Hey, just wanted to post that I did this too and after a reboot I can capture with kine without sudo. Thanks!

---

