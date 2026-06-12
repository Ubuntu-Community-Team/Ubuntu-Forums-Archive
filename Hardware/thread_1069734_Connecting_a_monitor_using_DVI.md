---
title: "Connecting a monitor using DVI"
date: 2009-02-14
forum: Hardware
---

### Post by baldurpet on 2009-02-14
I just got a "new" hand-me-down MultiSync LCD monitor so now I have two of them (both have VGA and DVI ports). Please mind that my computer has two DVI ports.
[LIST]
[*] The first one has been connected to my computer for ages, and it's worked well with Ubuntu 8.10. It is connected with a VGA cable, and then I use a VGA and DVI converter.
[*] The new one is connected to my computer solely with an DVI cable.
[/LIST]

Now here's the odd thing. When I turn the computer on **both** monitors show the boot loader and GRUB (I think that's what it's called), but when it reaches Ubuntu's login screen the screen connected with the DVI cable displays something like "no signal found through DVI"... I've tried switching monitors, and the first monitor doesn't work if I connect it through the DVI cable. 

Doesn't Ubuntu support DVI?! :confused:

---

### Post by mrcn on 2009-02-18
I have the same problem with one single monitor. 
VGA works well, but X11, which is the graphical interface for ubuntu, doesn't seem to send out a DVI signal. That's why it works while booting but switches off when ubuntu is started. 
As far as I know this doesn't have anything to do with the gfx card. At least I've heard about this problem from people with nvidia, as well as ati cards.

Does anybody by any chance know an Option to put into the xorg.conf which activates DVI-output? Would be very appreciated :)

---

