---
title: "adding my pci raid card with windows causes HAL failure"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by hereitcomes on 2006-07-26
adding my pci raid card with windows on it causes HAL failure
ive had ubuntu for quite some time with no problems, but recently i was getting Failed to initialize hal at bootup and tried reinstalling several times, this didnt fix it
just now i realised it could have been my raid card so i removed and reinstalled, and sure enough, everything went fine. I just put it back in the system and booted up, got the HAL error again, and the mounting root file system at bootup takes a good 30 seconds longer too.
I have an 80GB IDE drive connected to the motherboard with ubuntu on it, and a PCI RAID card (SIIG IDE) with two IDE drives with XP on them
any advice on how to fix this problem? preferably one that will still let me dual boot too??
any help is very much appreciated!

---

### Post by hereitcomes on 2006-07-26
update to the situation
i left the RAID controller plugged in, but removed the 2 drives from it, and linux booted fine, so it's obviously having trouble dealing with the two drives when connected
any idea how i could get linux to ignore this device when booting, or obviously configure it to understand the device properly?  I still need to retain the dual boot i have going with grub if possible
thank you

---

