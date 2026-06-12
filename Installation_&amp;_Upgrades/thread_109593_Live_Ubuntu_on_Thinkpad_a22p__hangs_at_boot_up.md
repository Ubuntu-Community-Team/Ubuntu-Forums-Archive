---
title: "Live Ubuntu on Thinkpad a22p : hangs at boot up"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by ygshah on 2005-12-28
Hi all.
I'm trying out **live cd 5.04-live-i386** on IBM Thinkpad a22p.
I need help. My laptop hangs on boot up. 
Using the default boot(live), I get the following messages:
... top part of the log messages removed  ...
pnp: 00:01: ioport range 0x1000-0x103f could not be reserved
pnp: 00:01: ioport range 0x1040-0x104f has been reserved
pnp: 00:01: ioport range 0xfe00-0xfe0f has been reserved
pnp: 00:01: ioport range 0x15e0-0x15ef has been reserved
Simple Boot Flag at 0x35 set to 0x1
audit: initializing netlink socket (disabled)
audit(1135809452.337 :0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: No Plug & Play device found
serio: i8042 KBD port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 165501
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:03.1[A] -> GSI 11 (level, low) -> IRQ 11

booting as: 
live DEBCONF_DEBUG=5 BOOT_DEBUG=1
OR
live DEBCONF_DEBUG=5[COLOR="Red"],[/COLOR]BOOT_DEBUG=1 
gives me the same set of messages as above.

I currently have W2K on the systems and in the past I did have the Redhat 7.3 installed and running.
Thanks for your help.

---

