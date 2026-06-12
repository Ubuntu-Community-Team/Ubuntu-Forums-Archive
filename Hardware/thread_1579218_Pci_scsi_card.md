---
title: "Pci scsi card"
date: 2010-09-21
forum: Hardware
---

### Post by dschuett on 2010-09-21
I am looking for a good PCI SCSI card that is compatible with Ubuntu 10.04. It HAS to be PCI -- **NOT** PCI express or -x. **JUST PCI**. I will be using this to connect a tape drive for my backups. 

Any input is appreciated.

Thanks

---

### Post by Fafler on 2010-09-21
You should get an Adaptec card, and get a card that matches or is faster than the interface speed on your tape drive, eg. 20, 40, 80 or 160 mb/s. All models should be supported and it doesn't matter if you buy one with BIOS or not. You can disable the BIOS to decrease boot time, as you won't need to boot from the tapedrive anyway. Also make sure you have the right cabling and termination to ensure optimal performance.

What tape drive do you have?

---

### Post by dschuett on 2010-09-22
> **Fafler said:**
> You should get an Adaptec card, and get a card that matches or is faster than the interface speed on your tape drive, eg. 20, 40, 80 or 160 mb/s. All models should be supported and it doesn't matter if you buy one with BIOS or not. You can disable the BIOS to decrease boot time, as you won't need to boot from the tapedrive anyway. Also make sure you have the right cabling and termination to ensure optimal performance.

What tape drive do you have?

I have a HP StorageWorks Ultrium 448. That has a 68-pin IDC connection.

The sad story is that I just purchased this card: [http://www.provantage.com/startech-pciscsiuw~7STRP03R.htm](http://www.provantage.com/startech-pciscsiuw~7STRP03R.htm) and Ubuntu NOR Fedora will boot with the card in the machine. I have tried it in two different machines. Every time it just hangs at the splash screen. And if I edit the grub to noacpi and nosplash, it just hangs at a blank black screen on boot. It does the same thing when trying to boot with a live cd. However, if I take the card out of the machine, it boots fine.

I know the card works because it works in a windows machine just fine. So I'm thinking it is just incompatible with Linux (Even though it says that it should work with Linux on the Provantage site).

Any ideas? Or am I right that the card just simply will not work with Linux?

Thanks for your time.

---

### Post by Fafler on 2010-09-23
It probably hangs during boot. Disable the splash screen by booting in recovery mode to see whats going on.

---

