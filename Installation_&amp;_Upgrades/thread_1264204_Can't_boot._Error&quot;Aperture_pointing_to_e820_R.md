---
title: "Can't boot. Error:&quot;Aperture pointing to e820 RAM. Ignoring.&quot;"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by tburge on 2009-09-11
This is so frustrating.  I really want Ubuntu but can't get it installed.  

I purchased an XFX Motherboard, 1TB HDD, DVDwriter, all are SATA.  All new, no OS installed, no format on the 1TB drive, no nothing .... 

I got Ubuntu 8.10 on CD and got it to ?partially? install by using "all-generic-ide" during install.  Boot from HDD puts me in BusyBox command line.  

I got Ubuntu 9.04 on CD and attempted to boot from CD.  That puts me in BusyBox command line.

In all cases I get: 
"Aperture pointing to e820 RAM. Ignoring.
"Your BIOS doesn't leave a aperture memory hole
"Please enable the IOMMU option in the BIOS setup
"This costs you 64 MB of RAM

then BusyBox.  ??What is IOMMU??  And "all-generic-ide" doesn't do anything for me anymore.  

I've considered updating BIOS but don't know how to update BIOS without an OS.  

I really want to insert a CD and have Ubuntu install.  That's all.  Is it too much to ask?

Help me please.  please.  

Terry

---

### Post by hal10000 on 2009-09-12
> In all cases I get:
"Aperture pointing to e820 RAM. Ignoring.
"Your BIOS doesn't leave a aperture memory hole
"Please enable the IOMMU option in the BIOS setup
"This costs you 64 MB of RAM
This is not an error message, it' just a warning and it should have nothing to do with the fact that you can't boot the live-cd

Maybe it could help if you post the exact modell of your mainboard and also about your other hardware, especially your graphic card and harddisks, so other people with the same or a similar mainboard can help.

[EDIT] Don't update your BIOS out of the blue, do this _only_ if you ruled out any other chances.

---

### Post by tburge on 2009-10-15
Upgraded BIOS from v1.2 to v6.0.  Machine started and ran flawlessly.  All is well, I am on 9.04 and happy.
Had a friend make an ISO CD from XFX download file.  Booted from CD, erased and re-wrote bios flash memory.  Booted to Ubuntu.  

Thanks all.

---

