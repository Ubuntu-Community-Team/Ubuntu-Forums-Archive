---
title: "Unable to install Breezy on AMD64"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by ben2005uk on 2005-09-24
Hello,
I have the following spec:

ECS K8 Elite RS480-M Motherboard (onboard everything)
1Gb ram
160Gb SATA drive
Wireless PCI Card
USB Wireless keyboard/mouse
DVDRW.

I tried to run MonoLive cd which is based on ubuntu and it gets to loading all the usb settings and sends the error :

ohci_hcd: 0000:00:13.1: Unlink after No-IRQ,  Different ACPI or APIC Settings may help.

This also is the same error I get when trying to install Breezy (AMD64 + i386 editions).

When I run AMD64 with NOAPIC boot options,  it loads but cannot detect my harddrive.

When I run MonoLive with NOAPIC boot options it gets to the splash screen after doing all the setting up and just hangs.

On the i386 with NOAPIC boot options it installs fine,  boots up,  goes over the new boot splash screen and then hangs after logging into gnome with the sound in a loop.


please please please help!!! I really want to use ubuntu.

btw - Windows XP Professional works fine on the system.....and my motherboard has the latest BIOS.


Look forward to your responses.


Ben

---

### Post by Gezzer on 2005-09-25
try the install with no usb hardware attached to the system
use a ps2 keyboard if u have one

also check in the bios that scsi is enabled for the sata drive

ie boot order
cd-rom
scsi
other devices

then try the install ...

---

### Post by ben2005uk on 2005-09-27
I do not currently have a ps2 keyboard :( :(

SATA drive is in IDE mode (means no need to mess around with SCSI drivers - thats how the shop set it, putting it in SCSI will kill windows :'(. ).   IDE Mode if you don't know means you get the speed of SATA but none of the driver hassle.  I do not have a RAID config (2 drives)

Boot Order currently:
CD-Rom
Floppy
IDE


Do you think it is my wireless keyboard?  It is the only thing plugged into the USB.

Cheers

Ben

---

### Post by Samiel on 2005-09-27
no Ben it's not your your keyboard. I'm running a much simliar gaming computer 64x and all. WIndows runs fine just as you said but when i boot you i get all the way to the login in screen and when i log in the computer freezes, my usb and ps2 keyboard stop responding but my usb mouse countinues to function prefectly. but it wont let me click or do anything because it is frozen at that light brown screen before everything loads (the on where the music play) 

I can't tell you what the true problem is, but alot of people seem to think it's a video card issue if ur running and Nividia card on Ubuntu with linux kernel 2.6.10.

Ryan and I are trying to figure out a work around so drop me an email and ill see what i can do.

---

