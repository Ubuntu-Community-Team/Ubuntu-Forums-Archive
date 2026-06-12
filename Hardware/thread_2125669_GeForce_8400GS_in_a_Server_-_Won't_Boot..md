---
title: "GeForce 8400GS in a Server - Won't Boot."
date: 2013-03-14
forum: Hardware
---

### Post by TheAdmiralty on 2013-03-14
Hello again!

You might have read the last three page thread I opened on getting Linux installed on an Acer Altos G510 server.  If not, I finally managed to do exactly that.

Since then, I picked up a used (looks NiB) BFG PCI 8400GS from the local brick and mortar store to replace the ATI Rage 128 which was incapable of running a Gnome desktop.  Tested it in another system and it appears to work.

This server has six PCI slots - four PCI-X slots of two different speeds, and two starndard PCI.  Putting the card in any of the PCI-X slots results in the system POST'ing, but hanging immediately after the POST beep on a page listing all connected devices; the card is displayed as "PCI Slot <#> - PCI Bridge", which seems correct as the card is normally PCIe and is bridged over to PCI.  It stops there until reset.

If the card is installed in either of the conventional 32-bit PCI slots, the system won't post and hangs at "Checking NVRAM..." until reset.

I can put up pictures if requested.

Any ideas as to why this card is causing problems?  I'm assuming it's related to the PCIe to PCI bridge used on the card, but is there any workaround for this?

---

