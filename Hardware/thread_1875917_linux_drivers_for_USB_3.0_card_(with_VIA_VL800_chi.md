---
title: "linux drivers for USB 3.0 card (with VIA VL800 chipset)?"
date: 2011-11-05
forum: Hardware
---

### Post by wallymann on 2011-11-05
just bought a 4-port USB3.0 PCIe card for my workstation running 10.10.

installed, no probs @ boot, but it doesnt recognize any USB 1.0/2.0/3.0 devices that i plug into the card.

did some googling and it looks like the 10.10 kernel should support USB3.0, so i'm guessing i need a diver for this card.  

i'm a bit of a rookie when it comes to specialty drivers, and honestly i'm surprised its not working -- ubuntu's always been great with any device i install.

if anyone has any suggestions/tips on how to get this card to work, i'd love to hear about it!

[IMG]http://i779.photobucket.com/albums/yy76/yinkwanfu/4portsVLI.jpg[/IMG]

---

### Post by amigabill on 2011-12-22
I'm also interested if there is a driver for this chipset, or what USB3 chip is recommended for Linux use. (Particularly if there are open-source drivers out there for it)

Do different USB3 host chips need drivers specific to them, or are they all XHCI and any USB3 host chip works with the kernel XHCI driver from intel?

---

### Post by Huzudra on 2012-01-11
I just got a pair of these in fresh from ebay via china post. I'm running 11.04 and....it works. My USB 3.0 drive is loaned out, I'll test the speed later and try to remember to post the result. It was one of those 'it just worked and I didn't do anything' kind of hardware installs. Actually had to install a driver in Win7 64.

---

### Post by Huzudra on 2012-01-14
Ok so...
All my USB ports stopped working under Ubuntu, but worked under windows. I power cycled the system totally off, then on, all is well and all work fine now. I don't know if it was related to the new card or not but whatever. 

The card works at USB 3.0 speeds under Win7 64bit (between 70 and 100MB/s to an external platter drive). Under Ubuntu it works at USB 2.0 speeds but slowly. Using the motherboard's ports I get a solid 30MB/s from my 2.0 flash drives, from this card a solid 20MB/s. It seems to be there is a driver issue with Ubuntu/Linux for this particular USB chipset. According to the diagram schematic on the VIA website, there are two controllers, a 3.0 for only 3.0 SS operation and then a standard 2.0 HS/FS/LS controller. I suspect that Ubuntu is only loading the driver for the 2.0 chip and totally ignoring the 3.0 chip. 

Is there something like NDIS wrapper for other devices?

---

### Post by Mark Phelps on 2012-01-16
> **Huzudra said:**
> Is there something like NDIS wrapper for other devices?

Sorry -- NO -- NDISwrapper is only for networking cards.

---

### Post by thedanyes on 2012-01-18
I have one of these cards and see the same issue. (Syba SD-PEX20080)
[http://www.syba.com/index.php?controller=Product&action=Info&Id=1216](http://www.syba.com/index.php?controller=Product&action=Info&Id=1216)

ON VIA USB3 PORT
[FONT="Courier New"]sudo hdparm -tT /dev/sdd1

/dev/sdd1:
 Timing cached reads:   11928 MB in  2.00 seconds = 5967.35 MB/sec
 Timing buffered disk reads:  42 MB in  3.03 seconds =  13.87 MB/sec
[/FONT]
ON INTEL USB2 PORT
[FONT="Courier New"]sudo hdparm -tT /dev/sdd1

/dev/sdd1:
 Timing cached reads:   11828 MB in  2.00 seconds = 5917.36 MB/sec
 Timing buffered disk reads: 100 MB in  3.03 seconds =  32.98 MB/sec
[/FONT]

I get some interesting messages in dmesg also with the drive connected via USB3:
[FONT="Courier New"][    3.787111] sd 11:0:0:0: Attached scsi generic sg4 type 0
[    3.787397] sd 11:0:0:0: [sdd] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    3.787726] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.788227] sd 11:0:0:0: [sdd] Write Protect is off
[    3.788230] sd 11:0:0:0: [sdd] Mode Sense: 23 00 00 00
[    3.788510] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.788972] sd 11:0:0:0: [sdd] No Caching mode page present
[    3.788975] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[    3.789718] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.790469] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.790924] sd 11:0:0:0: [sdd] No Caching mode page present
[    3.790926] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[    3.800615]  sdd: sdd1
[    3.801450] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.802222] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.802632] sd 11:0:0:0: [sdd] No Caching mode page present
[    3.802636] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[    3.802639] sd 11:0:0:0: [sdd] Attached SCSI disk
[    3.805929] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.806679] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[    3.905562] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
[   10.985321] usb 3-1.2: reset high speed USB device number 3 using xhci_hcd
[   11.057418] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   11.057465] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88010e751880
[   11.057468] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88010e7518c0



[/FONT]

---

