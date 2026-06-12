---
title: "USB 2.0 PCI Card Install Trouble"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by wirelessman on 2007-01-13
I can not get a usb 2.0 card installed.  Do I need to turn off the usb 1.1 thats on my mother board? Are there any extra drivers to in stall ?

The card works when I boot Kanotiix live CD. What gives?

---

### Post by RandomJoe on 2007-01-13
Every USB 2.0 card I've used was simply plug-and-play.  The all used the EHCI module for 2.0 and OHCI for 1.1.  I have never needed to turn off the motherboard USB to get them working.

First, does the system see the card?  'lspci -v' to get a detailed listing and see what you find for USB entries.  With the '-v' the USB lines should end with [UHCI], [OHCI] or [EHCI] to denote the capabilities of that component.  Your new card should list two, while the motherboard chipset will just have one.

On seeing the card, the kernel should load the module 'ehci_hcd'.  See if it is loading with 'lsmod'.  There should also be 'ohci_hcd' or 'uhci_hcd' to handle the USB 1.1 ports and the USB 1.1 portion of the new card.

If ehci_hcd isn't loaded and the system sees the card, what happens if you run 'sudo modprobe ehci_hcd'?  If that works, apparently the system doesn't want to load the module automatically for some reason - you could add it to /etc/modules to make sure it gets loaded.  (But this shouldn't be necessary...)

---

### Post by wirelessman on 2007-01-13
I ran your comands and yes it see's the card:

02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at ff9dfc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

and the other comand did not work, but, I'm very glad you are trying to help!!!

When I plug in my flash drive, and go to PLACES, then COMPUTER, it shows the drive, but will not let you mount it.  Now, you can get the same drive and plug it in the USB 1.1 slot and it works fine. What going on? Thanks again!

---

### Post by katana55@gmail.com on 2008-06-08
It seems that I have the same problem. Well, almost. I've bought a PCI USB2.0 card, and it behaves as if it is USB 1 and not 2. 

That is the information that I see:

02:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at df40 [size=32]
        Capabilities: [80] Power Management version 2

02:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at df80 [size=32]
        Capabilities: [80] Power Management version 2

02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

Help anyone?

---

