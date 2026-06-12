---
title: "Freeze with VIA USB 2.0 PCMCIA card"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by AndyC_772 on 2007-12-06
I have a 4 port USB 2.0 PCMCIA card, which I'm using with my Dell Inspiron 8200.

I can plug storage devices into the card and they mount OK, and I can transfer data to and fro BUT: after a while - maybe, a few minutes, the PC freezes solid. Even the mouse pointer won't move.

I can unfreeze the PC by unplugging the USB device, but of course, this doesn't give me the chance to unmount it first. I even get the pop-up warning telling me I shouldn't have done it (like I had the choice!)

I'm now running Feisty, but Edgy was exactly the same. I've tried several USB drives, all have the same problem.

lspci lists it as:
07:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

lsusb (with one USB storage device plugged into the card) gives:
Bus 005 Device 005: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Any ideas please?

Andy.

---

### Post by AndyC_772 on 2007-12-08
Just updated to Gutsy - exactly the same behaviour :(

---

### Post by dp_surfer on 2008-01-02
Hi 

Same behaviour here. I'm using a Bravo USB 2.0 Controller for PCMCIA on a Dell Inspiron 4150.

I have a external 500GB Disk (WD Elements) attached, after some minutes of file-transfer, all freezes. Only a reboot helps.

The external Disk works OK on Windows XP and Vista.

Anybody experiencing the same Problem or has even a solution ?

regards,
dp_surfer

---

### Post by AndyC_772 on 2008-01-02
Glad it's not just me then. Could you try lspci to find out what the controller chip actually is?

My card has a Via controller - there are others out there with an NEC chip instead which I may try.

---

### Post by dp_surfer on 2008-01-02
seems to be VIA as well:

02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
07:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
07:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
07:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

---

### Post by dp_surfer on 2008-01-02
could it be apci ??

---

### Post by dp_surfer on 2008-01-02
well, looks like it was really acpi. I booted with acpi disabled and transferred about 80GB in 2hours... worked without a problem...

So disabling acpi seems to fix the problem.

regards,
dp_surfer

---

### Post by AndyC_772 on 2008-01-02
Interesting... so is there anything that now no longer works because acpi is disabled?

---

### Post by dp_surfer on 2008-01-02
well... power saving would be difficult. But since I'm using this laptop as a server... I don't care.

Don't know if it's possible to disable acpi specifically for a pcmcia slot...

---

