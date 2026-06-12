---
title: "New Computer with a Asrock ALIVENF6G-DVI motherboard"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by mpitch2006 on 2006-12-06
Hi I have installed Ubuntu 6.06LTS on a new PC with this motherboard.  I initially had to run the install in safe graphics mode and now once the software is installed i can't connect to the internet as it doesn't seem to be able to use the onboard network device.  Also it doesnot recognise the on-board sound.  Please help

---

### Post by ReaderRat on 2006-12-06
Run (in the Terminal):
```
sudo lspci
```
and post the results here, so we can see what you have for hardware.

---

### Post by rascal on 2006-12-07
> **mpitch2006 said:**
> Hi I have installed Ubuntu 6.06LTS on a new PC with this motherboard.  I initially had to run the install in safe graphics mode and now once the software is installed i can't connect to the internet as it doesn't seem to be able to use the onboard network device.  Also it doesnot recognise the on-board sound.  Please help

I (and many others) have the same problem. see this thread : [http://ubuntuforums.org/showthread.php?t=309691](http://ubuntuforums.org/showthread.php?t=309691)

Probably the only way to fix this is to compile a newer kernel (or maybe upgrade to the developmen version, Feisty)

By the way, if you have IDE-devices in your system, could you check if they are using DMA or not? (with sudo hdparm /dev/hdX)

---

