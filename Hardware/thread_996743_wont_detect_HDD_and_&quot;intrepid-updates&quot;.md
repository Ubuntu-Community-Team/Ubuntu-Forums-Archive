---
title: "wont detect HDD and &quot;intrepid-updates&quot;?"
date: 2008-11-29
forum: Hardware
---

### Post by mic159 on 2008-11-29
Hey, i was trying to install 810 server on an old laptop (server edition because i just want bash, no gnome, etc)
This laptop is an old toshiba Portege 3110CT, and dosnt have a CD-rom drive. Not to worry, i can do a PXE install.

So I downloaded the 810 server ISO, extracted it, and put the tftp files in the appropreate place, and put the extracted ISO in my http root directory under /810/ (eg: http://192.168.0.1/810/)

I booted if off the network and the installer found the mirror, but in "Download installer components" it fails with "No kernel modules found"??
Its trying to download "/810/dists/intrepid-updates/Release" of which there is non on the CD...?? I have installed ubuntu before with previous versions using this method..

Ok but that is not the only problem, if I say continue without the kernal modules, it cant find any HDD? Is it related to the first error?

The IDE controller is an Intel 82440MX PCI Bus IDE Controller and the HDD is a Toshiba HDD2143.

---

### Post by mic159 on 2008-12-02
BUMP

No one has any thoughts on either??

---

