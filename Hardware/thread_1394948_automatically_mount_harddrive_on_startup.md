---
title: "automatically mount harddrive on startup"
date: 2010-01-31
forum: Hardware
---

### Post by Palanthas on 2010-01-31
I have a two part question. I want to have my computer automatically mount two hard drives on start up. Currently I have to manually go to places and click them (under Computer) which then asks for my password. etc, etc... Not a big deal except that I would rather not go through this routine every time I restart the machine. 

Second part is that after I mount the drives a link for each of them is placed on the desktop. Is it possible to mount the drives without the link being placed on the desktop?

Ubuntu 9.10 x64


Thanks in advanced!:D

---

### Post by mk1w86 on 2010-01-31
To have the partitions mounted at bootup add them to your /etc/fstab file. Here is a guide on doing this:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you do not want the drives to appear on the desktop create a mountpoint in /mnt instead of /media which is the default (that is what I do anyway ;)).

---

### Post by Palanthas on 2010-01-31
Alright, I'll try that. Thanks mk1w86! :)

---

### Post by Palanthas on 2010-01-31
Thankyou mk1w86! I finally got it to work!

---

