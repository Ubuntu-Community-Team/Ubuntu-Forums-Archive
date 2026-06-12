---
title: "keyboard (USB) doesn't let ubuntu boot up,also prevents mounting of extern volumes"
date: 2009-04-29
forum: Hardware
---

### Post by s'Miri on 2009-04-29
Hi,

I'm quite new in the forum and with Ubuntu. I use Ubuntu 8.04 (Hardy) on a Fujitsu Siemens Amilo Laptop. My extern keyboard (Hama Keyboard SL560, USB) causes some problems:

It properly works in the GRUB-menu, but afterwards ubuntu will not boot up, if the keyboard is plugged in. 
Usually I unplug the keyboard for the start, for the LogIn I can use it again, within Ubuntu everything is working properly, too. It only hinders booting up the system. 
(If I choose my Windows partition, everything is normal and fine.)

I already deactivated quiet splash, but I cannot see, that the error is always at one specific same moment. Usually the boot-process stops without any error message. Only once there the following last lines:[INDENT]ACPI: ACPI bus type pnp unregistered
PnPBios: Disabled by ACPI PNP
PCI. Using ACPI for IRQ routing
[/INDENT]I don't fully understand it, but it may has got something to do with my problems???


It would not be so bad to unplug the keyboard for starting up the laptop... But unfortunately the plugged-in keyboard also disables the mounting of USB-sticks and my extern harddisc-drive. 
They don't get recognized at all, unless I unplug everything and then only plug-in the USB-volume. If I replug the keyboard while any USB-Volume is mounted, it disappears instantly from the screen... (None of such incompatibility with Windows)

Other USB-devices (printer, scanner, mouse) work properly and don't interfere with the keyboard or extern volumes, so I suppose the USB-ports are alright.
The problem must lie somewhere within the keyboard. 
Can there be any system-chip or windows-module inside the keyboard? Could it be disabled?

Can I try to spot the issue in the Bios or test the technical keyboard-properties with any terminal command? (the hardware-test-function of the ubuntu hardware-database gives only information about key functions...)

Does anybody run this keyboard without problems or even solved the kind of problems I have?

Any help and hint is welcome!! Thanx a lot,
Mirjam

---

