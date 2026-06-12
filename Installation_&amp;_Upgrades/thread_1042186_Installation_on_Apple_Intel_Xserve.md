---
title: "Installation on Apple Intel Xserve"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by addihetja on 2009-01-17
I'm trying to install Ubuntu 8.04 (LTS) Server to an Apple Intel Xserve. So far I have had no luck booting the install CDs (I've tried Desktop and server, both 32 and 64bit plus the "alternate" 64 bit server installer). 

I saw somewhere that the Intel Xserve's EFI firmware didn't have the BIOS emulation feature that other Apple Intel machines have (to run Microsoft Windows via Boot Camp). Is there an installation CD I could use that would enable me to install Ubuntu somehow?

I've also tried booting the Xserve in Target-disk mode and connecting it to a Mac mini that can boot the 64bit but it doesn't recognize the Firewire drive in the partitioner.

Any workarounds? Hints? Clues?

Thanks
A.

---

### Post by Mactopia on 2009-01-28
Try [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Download rEFIt 0.12 and run the tool "rEFItBlesser
Worked for me ;)

---

