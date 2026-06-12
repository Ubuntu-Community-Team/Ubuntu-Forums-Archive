---
title: "Xeon and SCSI Install Woes - 8.10 Server Edition"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by jkholmes on 2009-04-11
Hey all.
I have been attempting to install Ubuntu 8.10 Server edition on a Dual Xeon box, with an Adaptec 71xx SCSI subsystem, with 1 gig of RAM and a 74 Gig Seagate HD.
The install drive is an Atapi CDROM.

Here's what happens:

The system boots from the cd just fine, and to all appearances installs fine. The installer corectly identifies the controller, the drive, the network etc.
I walk through the installation, and all goes fine, until the system wants to reboot.
Grub comes up, and beyond that it says that it's loading, and to please wait.
After about 30 seconds it comes up with the message that it has timed out waiting for the drive. If I edit the command line, and remove the quiet parameter and I get all sorts of detail, it appears to be a normal boot but just Stops.
Any help would be appreciated, this is the first of several production servers and it's not looking good for this.
Thanks!

---

