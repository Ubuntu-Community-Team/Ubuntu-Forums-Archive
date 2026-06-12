---
title: "Install to laptop from floppy?"
date: 2008-05-13
forum: Hardware
---

### Post by VanCardboardbox on 2008-05-13
My objective is to install Ubuntu to a *very* old Toshiba Portege 7200 laptop. Problem is that the only bootable device for this thing is a floppy drive. Wired Ethernet is off board, provided via PCMCIA and can not be used for PXE. Yes, so old that on board Ethernet was not standard. 

Is there a means by which I can begin an install from floppy, wake up USB or PCMCIA service and continue the install from another device? I have a USB CR-ROM, USB pen drives and a PCMCIA CD-ROM drive at hand. 

If not Ubuntu, is there another distro that lends itself to floppy-initiated installs?

---

### Post by VanCardboardbox on 2008-05-14
I should have mentioned that Win2000 is presently installed and functional on this machine. So to be precise, the machine can boot from floppy or from the internal HDD into W2K.

---

### Post by VanCardboardbox on 2008-05-15
No luck figuring out how to do this with Ubuntu but I did find a floppy-friendly distro. Puppy Linux has an installation option that employs a floppy to wake up USB, then completes installation from a Puppy live CD or stick. I've already used Puppy a little bit (I keep a bootable USB stick installation around) so this will work fine.

---

