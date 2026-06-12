---
title: "Poweredge 1950 PERC 5/i RAID"
date: 2014-03-24
forum: Hardware
---

### Post by cle-ziskind on 2014-03-24
Just bought a new Poweredge 1950 server with the PERC RAID controller. I'd like to break the RAID (-0) and have two separate disks. (Why? so that I can bring in a another disk with info and copy it over. This seems to be the easiest way ...)

I tried just deleting the VD from the RAID bios (and then setting up the VD with just one disk), with the predictable result that the Ubuntu install couldn't see any disks. So, how do I do this? I finished the install on RAID-0, but I would be willing to reinstall if necessary. Thanks!

---

### Post by tgalati4 on 2014-03-24
Normally you would turn the RAID off and set up the disk as JBOD (just a bunch of disks) within the PERC BIOS.  It helps to have the latest firmware from Dell for both the motherboard and the RAID controller.  Once that is done, you would have to reinstall your OS on one of the disks.  Then when you install another disk, it should show up with *fdisk*.

Once a set of drives has been striped by a hardware controller, there is no simple way to unstripe it without doing a complete wipe and starting over.  Of course, you have extra features from the RAID BIOS like hotswap and backup, but you need a free drive bay and a properly-sized disk to use those features.

---

### Post by cle-ziskind on 2014-03-24
Apparently, you can't do this (change PERC5 to JBOD). The best I could do is change the two disks to each be their own RAID0, which is good enough for me.

Thanks!

---

