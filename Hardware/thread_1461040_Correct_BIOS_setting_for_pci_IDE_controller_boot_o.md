---
title: "Correct BIOS setting for pci IDE controller boot option?"
date: 2010-04-23
forum: Hardware
---

### Post by Moozillaaa on 2010-04-23
It's a new build, with only 1 IDE channel, on which are the 2 optical disk drives.

I had 2 IDE disks on the old setup, secondary IDE channel. Only place to put them now is on a PCI IDE controller card.

So far, only the card is detected, not the disks.

The BIOS boot options are floppy (what's that???), and CD drive.

Ideas?

---

### Post by paulisdead on 2010-04-23
When you say the controller is detected, and not the disks, do you mean the POST for the card itself shows them not detected, or do you just mean that the drives aren't bootable?  Most Add in cards have their own POST after the bios POST, and might show the drives it detects.

Check through the bios settings for the motherboard for a setting something like "Boot Other Device" or "Bootable Add-In Cards."  Some of them have the boot option for SCSI, that just means boot from an add in card, as well, and will boot an IDE card.

*ninja edit
I think you're saying you expect the disks attached to the add in card to show as boot options in the motherboard's bios.  That won't happen, but another device like the ones I mentioned above, like add-in card or SCSI might show up if you have the right other options enabled.

---

### Post by Moozillaaa on 2010-04-24
Solved. The problem was foremost a card driver problem...

... and then a combination of jumper errors, and primary/secondary channel configuration (still don't know which is which either).

BIOS lists devices on PCI IDE card with RAID prefix, even tho' they're not RAIDed, just 'devices'.

With Linux as master on one PCI controller channel, and Windows master on [other] PCI contoller channel, only one comes up in BIOS as a bootable device (Linux in my case).

Third disk is slave behind Linux. Windows chainloads in order.

Windows had to be re-loaded too :(

But joy now :guitar:

---

