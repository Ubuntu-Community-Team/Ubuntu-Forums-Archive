---
title: "Can't see USB device"
date: 2009-07-29
forum: Hardware
---

### Post by graynada on 2009-07-29
Hi,

I am having problems connecting to my Navman S30 Satnav.  Until recently I could just plug it would appear as a storage device, and I could connect via Virtualbox to do Navman type stuff, ie backup, load maps etc.

Now when I connect, nothing, and the S30 itself doesn't seem to recognise it is connected.  When I do lsusb the S30 is not listed, but the response to lsusb is slower than when it is not connected.

Can any one help please, oh and please be gentle I am far from an Ubuntu/Linux expert. Thank you

---

### Post by rannable on 2009-07-29
when you remove an external device please always dismount it properly rather than just unplugging it, it could be that the data on the local storage card for the gps unit has become corrupted. does it work if you plug it in to another machine?
if you have access to a dreaded ms vista or win7 machine i think they auto scan/fix removable devices if problems are discovered, you could try this then plug it back onto your system.

sorry to suggest using a MS laptop i just figured as a newbie it might be the easiest way...

good luck!
rob

---

### Post by graynada on 2009-07-29
Thanks for the reply Rob.

I am pretty good at unmounting before removing usb devices, but not withstanding this I have identified something.

This problem appears to be as a result of an SD card being in a weird state. The SD card I was using usually resides in my eeepc (running eeebuntu 3.0) and in this machine, or in my phone (SPV M600 running WM5) behaves as expected. When it is in my main PC (running Ubuntu 9.04 or XP in VirtualBox) it claims to be read only and won't let me write to it, delete from it, format it, or delete the partition. When this SD card is in my Navman (or phone for that matter) they refuse to connect to anything via USB. Eject the SD card and the device appears, weird!

I will take a trip to the eeebuntu forums with this but on the off chance does anyone know how I can get the SD card into a state where it can be used on any device?

---

