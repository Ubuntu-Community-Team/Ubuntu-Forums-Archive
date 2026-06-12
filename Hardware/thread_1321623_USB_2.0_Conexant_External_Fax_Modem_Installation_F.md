---
title: "USB 2.0 Conexant External Fax Modem Installation For dailup connection"
date: 2009-11-10
forum: Hardware
---

### Post by sudo101 on 2009-11-10
I bought an External USB fax modem to use for dailup connection with my Ubuntu Karmic new installed Distro.. 

I was happy to find that the CD which came with the Hardware has a Driver for the GNU/Linux Distros after many faild attempts by the system to find the modem.. 

3 typs of drivers came in the CD...

RPM package
DEB package
TAR Package

I am using Ubuntu 9.10 Karmic Koala so i installed the Deb package and i found that it stops in terminal at

##
Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed}

Where is the linux source bild dicectory that matches your running kernel ?
[/lib/modules/2.6.31-14-generic/build]
##

And when i type

 mrb@hamadeh$ sudo dgcconfig 

I still get the same message..

running the "lsusb" command idinified the Modem as Conexant chip
Can anyone help me with how to install the driver ?
Thanks alot

---

### Post by sudo101 on 2009-11-12
No one yet can help me out :D ?!!

---

