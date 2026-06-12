---
title: "Help!  Trying to Recover NAS HDD"
date: 2010-04-04
forum: Hardware
---

### Post by nysimonsez on 2010-04-04
Hi -

In real dire need of help to recovery my data from a WD Mybook World NAS. I took out the drive and hooked it into a USB Enclosure.  I ran Ubuntu and mounted the drive and saw some of the data.  When I attempted to copy the folders into my new HDD, it will start and then suddenly has an input/output error and it seems like the drive is unmounted.  is my HDD dying (I assume it is) or is something else causing it to unmount.  I'm afraid to start it up again as I don't want to do any further damage to the HDD.

thanks for anyone who may have any thoughts.

thanks alot!

---

### Post by iponeverything on 2010-04-04
You might try removing the drive form the enclosure and mounting it directly.

---

### Post by tgalati4 on 2010-04-05
In a terminal:

dmesg | tail -50

---

