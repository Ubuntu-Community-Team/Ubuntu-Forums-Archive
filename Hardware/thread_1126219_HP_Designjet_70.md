---
title: "HP Designjet 70"
date: 2009-04-15
forum: Hardware
---

### Post by jumpa72 on 2009-04-15
Hi,
I want to create a server machine with Ubuntu, and replace so my old Windows machine. A very important keypoint is the printer support:
I have a HP Designjet 70 and a Samsung SCX 4216 F. For the last one Samsung has released a driver, HP doesn't! :-(
I have tried with Turboprint, but my printer is rebooted as soon as I print a page ](*,)
Could someone help me?
Thanks
Jumpa

---

### Post by khelben1979 on 2009-04-15
It definitely feels like you're out of luck with that HP printer. I checked out their homepage and I also looked in HPLIP. No drivers anywhere.

---

### Post by jumpa72 on 2009-04-17
To solve driver problem, I've installed VirtualBox and virtualized a Windows 2k machine. In the guest, I've correctly installed the printer, with proper driver. The point is: I cannot print in the guest machine too! The printer is installed and ready, but if I print a test page, I receive an unuseful error message.
(if I connect the printer back to the original windows 2k server, with the same usb cable, the printer works very fine!)
](*,)

---

### Post by Piscicani on 2009-12-04
Your DesignJet 70 work and also very well (because mine does); you have to go to OpenPrinting.com and follow [***these instruction***]("http://forums.linux-foundation.org/read.php?20,10618"). HPLIP is not supported.

---

