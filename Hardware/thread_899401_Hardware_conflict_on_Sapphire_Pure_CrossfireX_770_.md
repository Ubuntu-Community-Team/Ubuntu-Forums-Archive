---
title: "Hardware conflict on Sapphire Pure CrossfireX 770 Motherboard"
date: 2008-08-24
forum: Hardware
---

### Post by Quirion on 2008-08-24
Greetings,
I'm experiencing an hardware conflict issue with my Sapphire PURE CROSSFIREX 770 motherboard. On Windows' Device Manager the ATI SMBus seems to use the same memory range as the high precision event timer. The real problem is that this conflict seems to cause a failure when booting the Linux kernel unless it is booted with the option acpi=off. The error I get looks something like this:

PCI: cannot allocate resource region for device 00:00.0
PCI: cannot allocate resource region for device 00:14.0

According to the output of the lspci command, the two devices are:

00:00.0 Host bridge: ATI Technologies Inc RX790 Northbridge only single slot PCI-e_GFX and HT3 K8 part
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)

I have already upgraded the BIOS to the latest version and i'm using an nVidia 9600GT video card. Can anybody help me? Thanks in advance.

EDIT: I forgot to mention: I'm using ubuntu 7.10.

---

