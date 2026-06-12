---
title: "To Print the Unprintable Doc"
date: 2008-08-11
forum: General Help
---

### Post by raywood on 2008-08-11
I have a Canon imageCLASS MF5770 multifunction printer/scanner/copier/fax machine.  I understand, from the Open Printing Database, that this device is completely incompatible with Linux.

At the same time, if I choose File > Print, here in Firefox in Ubuntu Hardy 8.04, I see the MF5770 listed as one of my printing options.  So at least Ubuntu is seeing the printer, in some sense.

I have also gotten the impression, from various materials pertaining to virtualization, that a Windows XP virtual machine should be able to use WinXP drivers to operate a printer, even if the host operating system cannot.

I was hoping that virtualization could provide a workaround, so that I could use this device with Ubuntu.  I would also be interested in other suggestions.  I can dual-boot back into WinXP; I'm just not eager to if it's not necessary.

TIA.

---

### Post by rbmorse on 2008-08-11
I've used VMware workstation for that in the past and it was functional...i.e., it worked, but in the end, having to start a virtual machine in the middle of other work on Linux just to (in my case) scan a document was too much of a pain to use on a regular basis. 

You'll want to make sure whichever VM manager you're using can access the ports required by the device on the host machine. USB ports can be particularly problematic.

The other issue I had was the driver software for my problem device, a HP 4570CS scanner, was so bloated and contained so much unremovable "accessory" stuff (you can't say cr*pware here), it really increased the size of the XP virtual machine's footprint on the hard drive by an unacceptable amount.

---

