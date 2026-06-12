---
title: "Acer 5920 card reader"
date: 2008-10-21
forum: Hardware
---

### Post by Bartender on 2008-10-21
Our Acer 5920 lappy has a card reader on the front edge.  The reader works in Vista.  I get nothing in Ubuntu 8.04.  When I plug in the card from our camera nothing shows up on the desktop or in Places>Computer and Picasa for Linux doesn't see any device to "Import" from.
Anyone have any tips on how to wake up the card reader?
lspci shows two entries that seem to be related to the reader:

"SD Host Controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)"

and

"System peripheral: Ricoh Co Ltd xD-Picture Card Controller (revff)"

so there's some hope I would think...

EDIT: I pasted the lspci returns into a google search.  Bug reports have been written.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)
I'll read the bug report feedback, but if anyone is up to speed on this I'd appreciate any help

---

