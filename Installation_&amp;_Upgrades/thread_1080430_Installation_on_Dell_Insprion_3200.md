---
title: "Installation on Dell Insprion 3200"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by raypip on 2009-02-25
I am trying to install Xubuntu 8.04.1 on a Dell Insprion 3200 laptop with a Torisan DVD-ROM drive model DRD-N216. The installation hangs on " Detect and Mount CD-ROM". I like ideas on what I need to do to go beyond this point. There is no other OS on this laptop at the time of the current installation of xubuntu.
Also, I am new to Unix.

---

### Post by smani on 2009-02-25
Is it a kernel message or a BIOS message you are getting? From the posted information I cannot say much, but you may want to try to install it from a USB pen (which is imo the better way anyway, as you don't have to waste CD-ROMs just for installing the OS). Have a look at unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) - great utility that creates the bootable USB stick for you.

---

### Post by avtolle on 2009-02-25
We in the ppc community have run into this with 8.10, but not on 8.04.1. The work around on 8.10 (alternate install iso) is to hit Ctrl+Alt+F2 to get to a virtual terminal, and at the prompt type```
modprobe ide-scsi
``` then exit the terminal and get back to the initial screen, then (IIRC) select yes to the question, and installation proceeds from there. Don't know if this will work on an 8.04.1 Live or Alternate CD, but at this point, what is the harm in trying? :-)

---

