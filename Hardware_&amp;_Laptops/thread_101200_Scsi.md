---
title: "Scsi"
date: 2005-12-09
forum: Hardware &amp; Laptops
---

### Post by richardm on 2005-12-09
Hello to all.
I just resurected some old hardware which used to have Suse 7.2 on it and installed Ubuntu 5.1 it detected the ide 30GB hard drive and installed ok, it detected the Symbios SCSI controller and the 3 drives attached but failed to detect the aha1542 SCSI controller with 3 more drives attached.
I tried to manually install the driver (which is in /lib/modules......./SCSI) with the command:
modprobe aha1542 aha1542=0x130,11
where 0x130 is the hardware address
and
11 is the irq
These used to work with Suse which I tested prior to loading Ubuntu and all was fine.
Any ideas?
Richard

---

