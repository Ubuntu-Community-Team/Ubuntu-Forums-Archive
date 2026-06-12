---
title: "Installation weirdness"
date: 2008-10-17
forum: General Help
---

### Post by Leadfinger on 2008-10-17
I'm trying to install Ubuntu 8.04 onto a Dell PowerEdge 1500SC.

After the normal boot splash screen, when I select "Install Ubuntu", the system runs for about 60 seconds, and then falls to a command-line screen with the following message:

> 
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _



I'm confused.  :\

---

### Post by cariboo on 2008-10-17
Does you computer have a scsi cdrom? This has led to installation problems. If you've got an ide cdrom I would give that a try.

Jim

---

### Post by Leadfinger on 2008-10-17
Edit:

The DVD drive appears to be attached to an IDE controller.  (Entering the SCSI BIOS only shows the 3 HDD's, and the Tape Drive)

---

