---
title: "Help: ATI Radeon HD4200, mutter and the Catalyst driver"
date: 2011-06-24
forum: Hardware
---

### Post by fiacobelli on 2011-06-24
Help! :)
I am running Natty 11.04 x64 on a HP dm1z and I decided to install GNOME3 shell. Everything worked well until I installed the proprietary Catalyst drivers.

I did this because the resume time was very slow with the open source drivers and because the desktop sometimes turned extremely slow after resume.

The problem, though is that the proprietary drivers "diagonalized" my screen and I had to use the classic GNOME, no effects to be able to use my computer. 

I read that this can be due to a problem between Mutter (special FX in gnome3) and the Catalyst ATI driver.
Does anyone know how to make both play nice?
thanks!

---

### Post by cbowman57 on 2011-06-24
Try this, go to your home folder and view your hidden files & folders.  Look for .profile, open with a text editor (gedit) and add this to the top ```
**export CLUTTER_VBLANK=none**
``` logout and see if it helps.

---

