---
title: "I don't want my hard disk to spin"
date: 2010-09-25
forum: Hardware
---

### Post by adit on 2010-09-25
I have installed ubuntu 10.10 beta in my 8 GB usb flash drive.  Entire operating system including my home directory is in this pen drive.  I am using Dell Inspiron 1525.  I don't want to access any of the files in the hard disk.  Whenever I am using this operating system from my pen drive the hard disk inside this computer is also spinning unnecessarily (I think so).  How to turn off the hard disk permanently.

---

### Post by efflandt on 2010-09-25
Simplest would be to go to System > Preferences > Power Management and check the box to **Spin down hard disks when possible**.  It may not happen immediately (not sure what the delay is).

Otherwise see **man hdparm** in a terminal, but you likely need to use **sudo** for the **hdparm** command.  Look at -B and -S options.

---

