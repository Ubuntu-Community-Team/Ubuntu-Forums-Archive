---
title: "Problem with CMedia ISA sound"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by chantal on 2006-06-05
I can't get the sound to work on my PC Chips (AMD K6) M570 motherboard. The on-board ISA chip was not detected at install time. I'm using Hoary Ubuntu. The start-up screen says I have a CMI 8330/C3D Audio Adaptor. When I enter:

sudo modprobe snd-cmi8330   I get the reply

FATAL: Error inserting snd_cmi8330 (/lib/modules/2.6.10-6-386/kernel/sound/isa/snd-cmi8330.ko): No such device

And entering 'dmesg | grep isa'     I get the reply

No local APIC present or hardware disabled
SELinux:  Disabled at boot.
ACPI: Interpreter disabled.
pnp: PnP ACPI: disabled
audit: initializing netlink socket (disabled)
isapnp: Scanning for PnP cards...
isapnp: Card 'CMI8330/C3D Audio Adapter'
isapnp: 1 Plug & Play card detected total
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Disabled Privacy Extensions on device c02f0500(lo)
pnp: Device 01:01.00 disabled.

Can anyone help please?

---

