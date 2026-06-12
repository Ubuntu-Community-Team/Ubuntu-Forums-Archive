---
title: "Can't write usable image..."
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by uninventiveheart on 2009-09-06
Tried both methods of writing the .IMG to a USB Stick, and I get the same message each time without any progress past 12 seconds:
 
```
 
RealTek Fast Ethernet PCI (... didn't bother remembering that part.)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE-ROM.
Operating System not found

```
 
Does it need an ethernet cable plugged in with an active connection to install netbook remix?  (My workplace uses Intel Pre-Execution Environment, also called PXE on-screen, to initiate booting on our thin-client machines, which I'm using to type this.) Both ways I made the image (GUI, Command Line) it did the same thing.  I know Ubuntu will work with this netbook (Gateway LT3103u, runs Ubuntu 9.04 on another USB Key on Persistent Mode just fine) and I know that both keys are good.
 
I don't have an external optical drive on my netbook at this moment, so I can't go the CD/DVD route just yet... is there anything I'm missing or haven't tried?

---

### Post by P4man on 2009-09-06
you have to configure your bios to boot from the usb stick. Most bios's have an option to select the boot device by pressing some key (F11 on mine) after it checked its RAM. If you dont have that, you have to go in the bios and change the boot order. The message you see, is just the machine trying to boot from the LAN.

---

### Post by uninventiveheart on 2009-09-06
The device I select in the BIOS Boot Menu is "LEXAR JD-FIREFLY USB-HDD".  It's a netbook, my only choices are the Hard Drive, USB, or an Optical Drive I don't have anyway.

It's the image itself that's giving that message, regardless of the method I use to write it.

---

### Post by P4man on 2009-09-07
have you tested the stick on another machine?

Even if the stick works on a different machine, perhaps try another stick. i believe some sticks identify themselves in different ways (some as floppy, USB removable, even as USB ZIP drives) and perhaps your bios isn't happy with the stick ?

---

### Post by kerry_s on 2009-09-07
use the normal desktop iso, you can install the netbook stuff on top of that, it's easier.

---

### Post by uninventiveheart on 2009-09-08
My mom's PC gives the same error message (Compaq Athlon 64), as does my Desktop PC (Self-made Pentium D), my mom's Compaq uses American Megatrends for it's BIOS (Foxconn mobo) and my Desktop Machine uses Phoenix (Biostar mobo), both produce the same error as before.
 
I've read other posts about the Gateway LT3103 running Netbook Remix, is there another method or file I can use (other than the .img... I like .iso's, I can work with those... no rhyme intended) instead? Or how do I install UNR on top of an existing Ubuntu partition? (Is this safe for a newb?)

---

