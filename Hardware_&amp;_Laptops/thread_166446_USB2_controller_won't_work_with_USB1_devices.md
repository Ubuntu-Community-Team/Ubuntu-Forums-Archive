---
title: "USB2 controller won't work with USB1 devices"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by jerdcox on 2006-04-26
I recently added a PCI USB2 controller to a system running Dapper Beta; the card is correctly installed and has power on the positive USB bus, but would not work with any of my USB 1 devices. I looked in Device Manager, and noticed that the card (which has 6 ports) only showed one EHCI driver, and did not detect any USB1 devices that were connected to it (I tried a mouse, keyboard, hub, etc). I finally tried a USB 2 case connected to the card, and eventually got that to work (I had to plug and unplug it multiple times, still not sure why). That correctly mounted on the desktop and showed up in the device manager.

The motherboard has two onboard USB1 slots, and each of these shows a separate UHCI driver in the device manager, and correctly detects anything plugged into it (USB 1 or 2 at low speed). I assume I need a UHCI module set up for the USB2 card in order to detect and use USB1 devices with it, can anyone explain how to do it or how to get the system to correctly recognize the card for low speed devices?

The card is an ALI chipset, number 0x5239, according to the device manager. I have searched the web and these forums for a similar issue with no results, please let me know if there is any more information I can provide.
Thanks, Jeremy

---

### Post by jerdcox on 2006-04-28
Upgrading hal and the hal-device-manager to (0.5.7-1ubuntu11) seems to have resolved the issue. I now have two OHCI and one EHCI module listed for the card, and it correctly detects devices attached. Not sure whether a bug was fixed or the hardware just got rescanned after the upgrade.

Still don't know how to fix this manually, unfortunately, but at least it is working now.

---

