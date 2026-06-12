---
title: "SCSI LSI MegaRAID works in one installation and does not in another"
date: 2010-08-20
forum: Hardware
---

### Post by jim.cat on 2010-08-20
Hello,

I am using ubuntu 10.04 and I have been using it from 6.06 and I have deceided that it needs a proper doing since it works quite cranky after several updates :/

I installed new SCSI drives to install the new fresh install in them. If i boot my usual updated version it can see the controller without a problem and use the discs, however if i boot from the CD to install it it can't see the controller and therefore i can't install it. I tried to install the system i nanother spare SATA hard drive in order to install it there update it and make it see the controller and then move the partitions (clone them with dd) to the SCSI drives and voila make it work.

The problem is that **the new fresh installed and fully updated ubuntu 10.04 (new) can't see the controller, however the old cranky ubuntu 10.04 (old) a thousand times updated can**. 

The controller I have got is a SCSI LSI MegaRAID, which i don't think it is a fakeraid since it is an actual proper PCI-X controller.

I have copied the /etc/modules from the old 10.04 to the new 10.04 in order to see if any of them was to do with the controller but they don't seem to do anything with it and this doesn't solve the problem.

I have seen as well that there is a package called "dmraid" meant to make the LSI Logic MegaRAID to work, however i believe this should be only for the sata fakeraid controllers, and anyway dmraid is NOT installed on the old 10.04, where the controller works.

I basically **need to identify why the controller works on the old system in order to copy whatever makes it work to the new system**, however i don't know whether that is possible (other than with the kernel modules which I tried). As far as I am aware both systems are updated until the same point.

I hope somebody has a brilliant idea to identyfy what is making the damn card work :P

---

