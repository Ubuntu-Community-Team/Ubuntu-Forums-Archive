---
title: "USB locking up machine"
date: 2009-11-18
forum: Hardware
---

### Post by skogs on 2009-11-18
I'd like to add one more straw to the back of the camel. 
I have a wonderful custom built machine.  Hardware of interest includes:

[LIST]
[*]ASUS M4A78T-E motherboard
[LIST]
[*]AMD 790GX / SB750 chipset
[*]6 back panel USB
[*]3 USB headers for 6 more USB up front
[*]lsusb says: 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
[*]lsusb says: 00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
[/LIST]
 
[*]PNY mini-Attache' 2Gig USB stick
[*]Kingston DataTraveler 2Gig USB stick
[*]USB 'Browser' Mouse
[*]Dell USB keyboard with smartcard reader
[*]'PowerUp' media card reader USB 2.0
[*]unknown external media card reader USB 1.1
[*]StarTech 2 drive eSATA/USB2.0 toaster -- using USB since I'd obviously like to hot swap the darn things, and I haven't made that work right yet with the eSATA
[/LIST]

When I first built this machine, I immediately loaded 9.04 on it.  Worked flawlessly.  Spent about 20 minutes getting video to work.  Other than that perfect.  Media transfer to and from USB worked correctly and fast.

Sometime in early September, my machine completely locked up when I inserted a USB media card.  Mouse stuck on screen, no reaction from keyboard.  Hard reset only thing to do.  Machine has been locking up pretty frequently since.  I'd say about 70% of the time when I stick something into a USB slot it locks the machine up.  It might only be locking up the USB system, but since that is where all my user interaction happens....I'm sort of boned.  

Upgrading to 9.10 did nothing to fix it.  

I have tried:

[LIST]
[*]following threads about turning on modules and turning on modules
[*]reset bios 'plug and play aware OS' to yes and no
[*]reset bios 'EHCI handoff / workaround /etc" to every possible combination
[*]removing multi-card reader completely
[*]moving connectors around on the headers
[*]pulling hair out
[/LIST]
I've just about had it.  Naturally when I dual boot to the windows partition....everything is fine.  This is a nasty, nasty USB bug.

---

### Post by nixscripter on 2009-11-18
Try booting into [single user mode]("http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/"), and see if it still happens. If you stay on the console when you plug the device in, you might get some output that is useful.

---

