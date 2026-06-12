---
title: "How to reinstall via terminal?"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by thealmightyone on 2009-04-13
Had a dual boot XP/Ubuntu, but got Ubuntu to do all I need it to do, so want to extend the partition to where XP used to be (which is now free). Being an eeePC, I can't run off a liveCD, and no longer have the USB stick I originally installed Ubuntu with, so want to reinstall Ubuntu via the terminal. Surely it can be done.

---

### Post by Aubergines on 2009-04-13
I don't think it can be done, you'd be reinstalling over yourself live while running. The easiest option would be grab a USB drive and plonk the ubuntu image on it with something like [UNetbootin](http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/). Unless you just happen to have a have built yourself a PXE Boot server on your network so you could netboot :D

Alternatively you can look into something like gparted to extend your current install.

---

### Post by thealmightyone on 2009-04-13
I tried using gparted, but it won't let me do anything other than delete and format partitions. Again, I need a CD drive for gparted to mess with the main partition and extend it, a drive I don't have.

---

### Post by Aubergines on 2009-04-13
> **thealmightyone said:**
> Again, I need a CD drive for gparted to mess with the main partition and extend it, a drive I don't have.
Oh really? It shows I've never used it before unless it's the same tool that's used in the GUI install. I think picking up a USB drive is your best bet.

Just a thought, your Ubuntu install doesn't happen to be on a LVM does it? You probably still need a boot disk to resize (I can't remember).

---

### Post by thealmightyone on 2009-04-13
I have no idea what a LVM is.

---

