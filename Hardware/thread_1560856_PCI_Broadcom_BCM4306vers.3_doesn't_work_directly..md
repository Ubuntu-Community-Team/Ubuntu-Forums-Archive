---
title: "PCI Broadcom BCM4306/vers.3 doesn't work directly."
date: 2010-08-25
forum: Hardware
---

### Post by axrl on 2010-08-25
Hi,

My BCM4306/3 PCI card is not automatically recognized by Ubuntu 10.04 but I see there is a b43.ko module into the installation.  This would work but it doesn't.  Into Fedora I always used this b43 and it was working from installation !

So I had to be connected on Internet with a Wifi USB dongle to do : "System" ->  "Administration" -> "Hardware Drivers" and finding the proprietary driver on Internet.  Eventually the card is activated and works properly.

My question : how can I save on a CD or on a Floppy the driver I found in order to have it directly on hands if I install a newly Ubuntu  10.04 without any Internet access but the Broadcom one.  And what are the different steps to compile if there are any ?

Thanks.

P.S.  : It seems that it is really the b43 module that is used currently but I suppose that it is the newly downloaded one and not the original found in the Ubuntu10.04 distribution.

Lspci :

00:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Subsystem: Linksys Device 0013
Flags: bus master, fast devsel, latency 32, IRQ 17
Memory at ee000000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

---

### Post by Fafler on 2010-08-25
My laptop came with that card, and man, did it cause a lot of compatibility problems, both driver and accesspoint wise. I would recommend you go on eBay and get a Intel 5100 or similar.

Edit: But to actually answer your question, yes, you can. Use apt-cache search and apt-cache show to find information about the package. Download the driver package itself and all packages it depends on and then manually install with dpkg --install package.name.deb

---

### Post by axrl on 2010-08-26
Thank you [Fafler]("http://ubuntuforums.org/member.php?u=906274").  I found the package and all the dependances.  ([I]It was b43-fwcutter_012-1build1_i386.deb).

[/I]_For information_ : Since four years I never had a problem with this card (Linksys WNP54G-EU v2).Axrl

---

