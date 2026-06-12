---
title: "HP NetRAID (D4393) controller card not recognized"
date: 2009-04-20
forum: Hardware
---

### Post by CaptNibor on 2009-04-20
Hi there,
     I am trying to setup a server using an HP NetRAID controller card.  The model is D4393 which is a three channel UW SCSI controller card.  It appears that I need to run a driver for it before Xubuntu 8.10 will realize the card is there.  I read in another area in these forums "Change your SCSI emulation from I20 to MASS STORAGE, erase your array (you will lose everything on your drives) and rebuild and initialize it. This way Ubuntu will not see multiple installations and will erase the entire disks."  I do not see SCSI Emulation as an option in my controller card's firmware, so that didn't help.

Any ideas?

Thanks,



Robin


EDIT:  Well, I solved my own issue.  Seems I needed to Configure, Initialize and basically setup an array (even with just one drive connected to the card) using the HP Express Tools <Ctrl>+<M> menu.  Once I did that, Xubuntu recognized the hard drive apparently using the already built in driver MegaRAID.  I apologize if I took up space here for no good reason.

---

