---
title: "IRQPOLL is creating some irq issues in my system"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by ayaskant16 on 2009-01-12
Hi Guys,

I am currently using linux kernel version: 2.6.23.2
I am always getting grub read error on software reboot command but when I am doing hard shut down and starting to restart again I don’t see grub read error.
My kernel was build with AHCI driver. So I changed the bios setting from IDE to AHCI.

After this the grub loading happened. But it gave a new problem which says:

irq 11: nobody cared(try booting with the "irqpoll" option)
handlers:
[<c0386149>](ahci_interrupt+0*0/0*429)
Disabling IRQ #11
ata1: COMRESET failed (errno = -16)
ata1: COMRESET failed (errno = -16)
ata1: COMRESET failed (errno = -16)

So I tried with IRQPOLL option in /boot/grub/menu.lst as a boot parameter.
Everything was going fine and after some testing I found dialup PPPD is not working.

While exploring I found that both SATA and Modem are using same irq 11
So I removed IRQPOLL from the boot option and got my dial up working but then soft-reboot is not working.

we never faced this kind of problem with linux 2.6.11.12 

Can any boot expert please help me know how to make both working without any side effects?

---

