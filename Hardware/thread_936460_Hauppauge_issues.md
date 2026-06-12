---
title: "Hauppauge issues"
date: 2008-10-02
forum: Hardware
---

### Post by mcgodx on 2008-10-02
Hi,

I have a Hauppauge HVR-1600 TV tuner.  I'm satisfied with it for the most part, with one GLARING flaw to it.

Due to some mysterious reason, if a user has 4GB or more of RAM, this card will not allow them to boot, without the use of special drivers supplied by the vendor.  Now, they are available, but only for Windows.  I got it working in Windows Vista Business, but I want to run Ubuntu as well, and this card will stop any OS from loading fully until the drivers are installed, apparently.  Do you guys know of a fix to this?  I know it's a long shot but I figured it was worth the shot.

It's a PCI slot card by the way, so I don't know if there is an option to disable PCI support or something like that in Linux, that would probably solve the problem.  My BIOS does not have any such option.

Thanks

---

### Post by nixscripter on 2008-10-03
I'm afraid I don't know much about TV tuner cards, but this sounds like a high memory problem. I assume that this is a 64-bit machine (hence > 4 GB RAM), and x86-64 can have trouble with PCI.

What does "won't allow [it] to boot" mean? Nothing comes up? A kernel panic? A hang in trying to initalize the device?

---

