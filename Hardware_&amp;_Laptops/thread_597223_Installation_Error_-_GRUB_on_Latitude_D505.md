---
title: "Installation Error - GRUB on Latitude D505"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Bumbler on 2007-10-30
This is a report on what I experienced installing Kubuntu on my Dell Latitude D505.

I've got slightly smaller LCD option (14.1" versus the 15"), so the native resolution of 1400x1050 everyone else talks about doesn't exist on mine. Thus, fooling with 915resolution is pointless. Apparently not everyone is aware there were two options on the display. Also, using the i810 driver gives me a band of garbled screen across the top, and the display is shifted downward to match. Using the intel driver removes that. Yes, I have the A11 BIOS update.

The big deal was GRUB. Walking through the installer utility, my harddrive is regarded by Kubuntu as SCSI, though I don't know why. At any rate, I partitioned my drive thus:

/dev/sda1 = swap, 1019MB
/dev/sda2 = /, 12GB
/dev/sda3 = /home, 17GB

No part of GRUB was installed except the MBR bit. I booted from the CD and ran through the procedure for installing GRUB files into /boot, but it still failed to create the 'menu.lst'. I found where someone posted a generic copy of that, and created one edited for my particulars. Once I added that, the GRUB install routine worked as it should and I'm now running fine.

---

