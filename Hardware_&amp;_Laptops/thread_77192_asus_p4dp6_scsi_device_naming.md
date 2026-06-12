---
title: "asus p4dp6 scsi device naming"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by dmallery on 2005-10-16
hi

i have had this problem on this machine previously with other distros and with breezy..

during the system set-up phase, the set up discovers the usb drives before the main two scsi drives.  the sysgen proceeds making the main drives sde and sdf.

when the newly loaded system boots, the init finds the disks in the proper order, so now they are sda and sdb.  so much for that sysgen.

this seems like a hardware identification bug.  has anyone swatted it?

thanks

dave mallery

ADDENDUM:  i started on another machine (perfect 5.4) and the SAME thing is happening.
install thinks the hard drives are sde and sdf.  bail out.

---

### Post by dmallery on 2005-10-16
I should add that the second machine is a Thunder K7 mobo.

both are MP.   This never had the problem in 5.4

my only other machine is a amd64.

---

### Post by dmallery on 2005-10-18
ANSWER:  i removed my usb2.0 card and did a full install.

works!

then i re-installed the card and itstill works.

clearly an installer bug.  off to bugzilla we go!!!!!

---

