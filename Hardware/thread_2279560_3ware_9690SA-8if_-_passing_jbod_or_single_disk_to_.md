---
title: "3ware 9690SA-8if - passing jbod or single disk to ubuntu mdadm"
date: 2015-05-24
forum: Hardware
---

### Post by jason63 on 2015-05-24
System;

Ubuntu 14.04.1 Server
Asus H87 Motherboard
i5-4570
16gb ram
Kingston 120GB SSD boot drive 
4 x 4TB WD Reds
3 x 2TB WD Greens with TLER disabled for raid use
3 x 200GB Seagate drives
2 x 320GB WD Caviars 
2 x 500GB WD Caviars

and

3ware 9690SA-8if 2 port SAS Card with 2 SAS to 4 SATA cables (8 drives)

Drives are configured in various raid arrays uses MDADM. I bought the 3ware 9690SA for practically nothing ($30), and want to use it to get extra drives connected to the system, and use mdadm to run the arrays.

In the 3ware bios it lists the JBOD export as N/A. Further reading shows the 3ware 9000 series cards don't support JBOD export to the OS. 3ware says to configure each disk as a single, if you want to use them as straight disks. If I configure each disk as a single, I CAN see them in mdadm and use them in an array.

Question;

Should I keep searching for a way to hack/bypass the 3ware bios to export JBOD, or leave them configured as singles and use them in the mdadm array as 3ware says?

The goals to use this controller as a sata expander as my mb has run out of ports.


Thanks guys !

---

