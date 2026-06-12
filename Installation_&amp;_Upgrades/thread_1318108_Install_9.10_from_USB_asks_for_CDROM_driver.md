---
title: "Install 9.10 from USB asks for CDROM driver"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by wscheun on 2009-11-07
Hi,

I'm trying to install Ubuntu server 9.10 from a USB stick on an Ebox 4863 minipc.
The box boots nicely from teh USB stick, goes through the language and keyboard detection dialogues, but then starts to aks for a cdrom driver, complains it can't find a cdrom drive and leaves me with no other option then to abort the instalation.
How do I continue installing from USB?

Any help is appreciated.

---

### Post by a212359 on 2009-11-08
You probably need to add this installer option:

cdrom-detect/try-usb=true 

If you are using unetbootin you can add this by hitting tab when the menu comes up. If you made your usb some other way at some point you should be able to edit the options before the installer runs and thats where you add it.

---

### Post by oxothuk on 2010-01-27
thanks
its works

---

### Post by ndoro on 2010-03-05
not work for me....


i use other option, and there is cdrom detect, but still cannot find cd rom...

---

