---
title: "Toshiba Satellite A65 pci hotplug issue"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by bcashman on 2005-07-14
Im trying to resolve a wireless issue but it seems that the problem is related to the pcmcia card slot and not the device. I have a D-link dwl-630 wireless card that doesn't seem to be recognized. I have installed ndiswrapper and I know its working because I can load a usb wireless device and it works fine. The problem is that i get no response from the d-link card at all. No lights, and when when i do an ndiswrapper -l i get a driver installed msg, but no hardware present msg. I did a dmesg and got noticed the following;
 
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ohci_hcd: 2004 Nov 08

So I wonder if the slot is working. Anyone have any ideas? Im a noobie so please be gentle....

---

