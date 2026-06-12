---
title: "Floppy Formatter problem with removable USB Floppy Disk Drive"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by philw on 2005-05-08
Floppy Formatter always fails with the message "Cannot initialise device Unable to open any device, formatting cannot continue"

Otherwise, everything is fine with the floppy drive :
1. A floppy icon pops up on the desktop when I insert a floppy disk
2. I can browser the contentsof the floppy in File Browser
3. I can format the floppy OK with mk2efs or mkdosfs from a terminal
4. I can mount the floppy with this line in /etc/fstab
/dev/sda        /media/floppy    auto    user,noauto      0       0

My PC is a Dell X300 which has one removable media bay connected by USB. Apart from this one problem, the USB CD-RW and USB Floppy disk drive seem to work fine. I installed Hoary from CD without problems.

Is this a bug in the Floppy Formatter Application?

---

