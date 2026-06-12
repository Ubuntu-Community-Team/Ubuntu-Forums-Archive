---
title: "How do I find &amp; mount my USB DVD drive?"
date: 2011-09-10
forum: Hardware
---

### Post by tweezak on 2011-09-10
I bought a Rosewill USB 2.0 adapter for IDE/SATA drives.

If I start it up with a hard drive attached the drive mounts and is fully functional. Data transfer is a little slow but that's just USB2.0.

However, when I attach a CD/DVD drive and fire it up I get nothing. The disk spins up as it should but then spins back down. The only device showing up in /dev/usb is the dongle for my wireless mouse/keyboard.

I've searched around but haven't found any answers yet. I know it's something simple.


FWIW the computer is an HP mini 311 and I'm running Ubuntu 11.04.


Thanks!

---

### Post by tweezak on 2011-09-10
For troubleshooting purposes I reattached the HDD and was dismayed to find it also did not show up. No activity whatsoever. Now I'm bummed.

So, I try a few things and eventually decide to try Winblows. I reboot into Win7 (it's been months since I've booted windows) and try there. Still no joy with either device.

I then checked the jumper setting on both drives. The HDD was set to Cable Select but the DVD was set to master. I changed the HDD to master and tried again. Lo and behold it spins up and reads fine. So next I try the DVD drive and it too is now working.

So I disconnect the drive and reboot into Ubuntu. I plug in the DVD and it spins up and mounts automatically with no issues. Same goes for the HDD.

All I can figure is that the adapter got left in some strange state and switching from CS to master forced it to reset. 

All's well that ends well...for now.

---

