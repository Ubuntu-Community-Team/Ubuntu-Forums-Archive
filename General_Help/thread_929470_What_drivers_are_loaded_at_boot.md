---
title: "What drivers are loaded at boot?"
date: 2008-09-25
forum: General Help
---

### Post by Bucky Ball on 2008-09-25
Simple question hopefully with a simple answer.

Just wondering where I should look to find what drivers are being loaded when I boot the Toshiba Satellite 2410 I am working on. Having a nightmare and wondering if I have some conflicting drivers for nvidia. Seems that way.

Thanks in advance ...

---

### Post by DagMan on 2008-09-25
It's been quite a while since I had an Nvidia card but I recall there was a conflict for sure when I compiled a driver from the Nvidia website as there's also an nvidia module elsewhere, either in the restricted package or there's an open source module using the same name as the compiled one.  What was happening for me is that I'd compile the one from the website, then on reboot it would go back to the other one, but I did'nt know there was 2.  See if you can find 2 separate nvidia modules using the search function for starters, and make sure you aren't looking at the same one through a link by testing the md5sum if you do indeed find more than one.

---

### Post by Bucky Ball on 2008-09-25
Thanks for that. Where I am up to with the whole thing is posted here:

[http://ubuntuforums.org/showthread.php?t=928662](http://ubuntuforums.org/showthread.php?t=928662)

I have no nvidia drivers installed for the moment and am starting from scratch and following this:

[http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy](http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy)

:)

---

