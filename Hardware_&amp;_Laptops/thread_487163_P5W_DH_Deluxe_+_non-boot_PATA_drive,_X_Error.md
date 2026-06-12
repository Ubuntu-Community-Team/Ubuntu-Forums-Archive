---
title: "P5W DH Deluxe + non-boot PATA drive, X Error"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by phyrko on 2007-06-28
Well, here is someone revisiting the P5W DH Deluxe JMicron IDE controller!

Put simply, I've installed Feisty fine on a new WD Raptor (SATA) and I have a large Seagate Barracuda (SATA 2) mounted without too many problems; although boot times are long. I have the 'irqpoll noapic nolapic' stuff going on at boot.

To keep things straightforward when I was installing I just disabled the JMicron Controller in BIOS. Now when I enable it to access the PATA drive the X Server doesn't load complaining that it can't find device ATI Radeon X600. Weird.

Disable the controller again and lo! I can boot to the desktop no problem. This is obviously some sort of conflict but is there anything I can do?

Change IRQ numbers about maybe? It seems crazy because I could mount the drive in Edgy and possibly even in a previous install of Feisty.

Thanks.

---

### Post by paulroberts on 2007-07-16
Hi,

I am just starting to experience this issue having tried to install Ubuntu 7.04 on my system yesterday. I am using an Asus P5W-DH with 2 x 400GB SATA drives in Easy RAID configuration running Vista, and I wanted to put Ubuntu on a spare 80GB IDE drive I had. As the optical drives were already using one IDE controller, the only one left for the IDE drive was the JMicron controller.

Although Vista can see the IDE drive fine, the BIOS doesn't seem to auto-detect it and Ubuntu couldn't see it either (when asked to partition the drive it could only see the 400GB RAID drive not the 80GB IDE drive). In fact I couldn't get the Live CD to boot at first, it was only when I went into the BIOS and started mucking around with the IDE configuration I got it to work. I think I had to change it from "Advanced/PnP OS" to "Standard/Legacy OS" or something.

I did a quick search and found references to kernel versions and a huge 30+ page post on here somewhere, but I couldn't quickly find a solution, so if anyone has any ideas while I continue to reasearch this, please let me know? :-)

Cheers,

Paul

---

