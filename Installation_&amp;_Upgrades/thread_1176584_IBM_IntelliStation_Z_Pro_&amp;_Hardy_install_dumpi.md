---
title: "IBM IntelliStation Z Pro &amp; Hardy install dumping into BusyBox"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by gcornelisse on 2009-06-02
I'm trying to do a fresh install of Hardy on a IBM IntelliStation Z Pro with 2 SCSI hard drives.  A previous version Hardy had been installed on the box, but is now corrupt.

I realize Hardy is not the latest release.  Its just what our department supports at the moment for the specific things we do.

Shortly after booting from the CDROM and selecting Install Ubuntu from the menu, the process dumps me into a BusyBox prompt.

There are a number of BusyBox related threads about installation and various solutions posted.  I've tried several install parameters including pci=nomsi, all_generic_ide, floppy=off, and irqpoll in various combinations.

My suspicion is the installer isn't recognizing or able to deal with the Adaptec/Planar SCSI.  Has anyone had experience with this?

Thanks, Gary

---

