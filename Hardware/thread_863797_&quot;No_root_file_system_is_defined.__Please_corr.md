---
title: "&quot;No root file system is defined.  Please correct this from the partitioning menu.&quot;"
date: 2008-07-18
forum: Hardware
---

### Post by americanknight on 2008-07-18
I have a laptop with a defective hard drive.  I ordered a new one and swapped it with the old one, then booted with the Ubuntu Hardy CD.  When I enter the install wizard, I get to the partitioning menu, but it's completely blank.  I'm told "You need to specify a partition for the root file system (mount point "/")..." but there's no option to do anything like that, no right-click menu, etc.  If I click forward, I get this message "No root file system is defined.  Please correct this from the partitioning menu."

So I'm guessing that either this is a defective hard drive, and thus the computer can't detect it, or more likely, I need to do some manual mounting and/or partitioning ritual. If so, does anyone know how to do that? Thanks

---

### Post by logos34 on 2008-07-18
Check the Bios settings--make sure the drive is being properly detected.

If the installer still gives you the runaround, quit and return to desktop and run >system>admin>partition editor.  If it sees the disk, create a ext3 partition for /, and linux-swap for /swap.  Then rerun the installer and point it to /.

---

