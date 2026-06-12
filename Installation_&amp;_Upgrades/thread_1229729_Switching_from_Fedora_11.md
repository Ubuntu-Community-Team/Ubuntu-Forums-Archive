---
title: "Switching from Fedora 11"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by spillemw on 2009-08-02
I have a i386 system on which Fedora 11 had been installed using LVM.
The system has 4 hard disks : one serial ATA separate, one serial ATA separate, two serial ATA arranged as RAID but without RAID activation.
FC11 had arranged all these drives in a logical volume.
I want to switch this to Ubuntu Server 9.04
The installation program worked reasonably well, although I had to guess a bit at how to remove the LVM.
I installed everything on the first hard disk (which, bizarre, is called sdc).
However, on reboot, I get :
MBR FA:
and then nothing.
If I push the (a) I get :
MBR 1234F:

And nothing again.

I assume this may be because the partition for some reason has not been activated, but I don't know how to do that from the rescue disk.
Any suggestions?

---

### Post by spillemw on 2009-08-03
After extensive search I used cfdisk to make the partition bootable.

---

