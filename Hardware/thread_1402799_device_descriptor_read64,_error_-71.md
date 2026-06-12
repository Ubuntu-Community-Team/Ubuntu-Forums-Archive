---
title: "device descriptor read/64, error -71"
date: 2010-02-09
forum: Hardware
---

### Post by carrabta on 2010-02-09
Hi all !
I'm having troubled trying to solve the following error code (from dmesg) :
"usb 2-1: device descriptor read/64, error -71 "

As a result, my USB devices are not usable (a printer, a scanner, and a webcam), though they are correctly listed with 'lsusb'.
I've got a usb hard drive that works fine. I think that the difference with the other devices is that it is connected to a usb 1 port. That would mean the problem is due to the ehci module... to be confirmed.

I had read a post somewhere in ubuntu forum (can't manage to find it again, though !...) that said it might be due to a kernel bug, a conflict with ACPI, and that setting the autosuspend parameter of the usbcore module to "-1" worked. But it didn't for me (It might be due to an error from me).

Can anyone help me with that ?

Distro = kubuntu 9.10
Desktop computer intel 32bit 
Intel motherboard

Thanx !

---

### Post by carrabta on 2010-02-09
One step ahead.... :

I've found in a french forum a "solution" consisting in applying an option to the usbcore module :

[LIST]
[*]in /etc/modprobe.d/user_usbcore.modconf (create the file if it does not exist)
[*]add the line : options usbcore old_scheme_first=1
[*]restart computer
[/LIST]
An other option might be to set this option to : usbcore old_scheme_first=1.

It gave partial satisfaction : error -71 disapeared but the devices do not seem to function properly (unable to print a document, use the webcam or get the scanner to be recognised by XSane...)

Any though ?

---

### Post by dortmann on 2010-09-14
I just encountered this USB error on 10.04.  Simultaneously, my X would not boot.  I noticed "vga16fb" had somehow snuck into the system ... it was missing from etc modprobe.d framebuffer blacklist.

I after adding vga16fb to the blacklist file I have both X and usb functionality again.

DISABLE ALL FRAMEBUFFER MODULES.

lsmod | grep fb


Hope this helps.
[email]dortmann31415@yahoo.com[/email]

---

