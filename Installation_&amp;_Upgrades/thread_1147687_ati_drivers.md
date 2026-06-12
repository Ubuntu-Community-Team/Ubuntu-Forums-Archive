---
title: "ati drivers"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by vi0lent666 on 2009-05-03
im new with this os... and i cant even install drivers.


ati-driver-installer-9-4-x86.x86_64.run    opens with ge edit .... text editor? how do install this :confused:

---

### Post by RedSingularity on 2009-05-03
Just go to system>Admin>hardware drivers.  The driver is there just activate it.

---

### Post by Sivan on 2009-05-03
I don't see anything when I do this. I have a Radeon X850.

---

### Post by RedSingularity on 2009-05-03
Before we try to install it with that package try this.  Go to a terminal and type "sudo apt-get install xorg-driver-fglrx"

Restart the PC and see what happens.

---

### Post by alphacrucis2 on 2009-05-03
> **Sivan said:**
> I don't see anything when I do this. I have a Radeon X850.

If you are running Jaunty then you may be out of luck using the proprietary driver. Jaunty ships with x.org server 1.6 which requires the fglrx driver released with Catalyst 9.4. Unfortunately ATI dropped support for a bunch of cards from that release. If yours is one of those cards you would have to run one of the OSS ATI drivers. Your other option is to install Intrepid instead.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

---

