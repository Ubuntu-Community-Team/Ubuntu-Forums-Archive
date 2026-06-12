---
title: "Wireless networking with a Thinkpad A22M"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by batkins on 2006-03-13
I convinced my father to let me install Ubuntu on his personal laptop.  The problem is trying to get it to connect to the Internet.  During the install, Ubuntu didn't automatically detect the Ethernet port in the back (some guides for the A22M suggest that the Ethernet port isn't actually hooked up to a NIC!).

I do have a Linksys PCMCIA wireless card that he used to use when the laptop was  "running" Windows, but I'm not sure how to get it set up, or if it's possible without a pre-existing network connection to install the software it needs.

Thanks,
Bill

---

### Post by djroadrash on 2006-03-14
hi batkins:
did u installed ubuntu, if u did and dont mind doing it again it would be the easiest way to get things to work, the problem is that for some reason if u just boot the installer with the original settings it will enable acpi and dma and for some reason it stops the ethernet and other things to turn on.
if i were u, i would just throw the cd in the machine and do a clean install with this parameters at boot
linux acpi=off dma=off
i belive u have to put linux first, but do a little search before u boot and push f1 and f3 and f4 for more parameters and the correct way to put them down.
this should fix your ethernet nic problem
if u want to try wireless just put the cardbus in and go to system/admin/networking and see if it comes up out of the box, chances are it will. then if so , configure in properties.
good luck:)

---

### Post by djroadrash on 2006-03-14
also i i asumed u are running 5.10, if not maybe the card will or not be supported but the other stuff should work, if u have a copy of a livecd of ubuntu brezzy 5.10 do the test with it first.
:)

---

