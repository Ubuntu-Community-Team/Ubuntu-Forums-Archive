---
title: "installation stopped on &quot;Scanning CD-ROM&quot;"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by marvaneke on 2006-01-04
I have :
 - a SATA disk
 - a CD/DVD writer SONY model DW-U14A

On the page "http://www.debian.org/releases/stable/debian-installer/index.html", the problem is know on the paragraph "SATA driver can block access to CD drive in installations from CD."

When I tried to install the UBUNTU V5.10, the installation stopped on "Scanning CD-ROM".  I have tried these unsucessful actions :
 - boot : linux noapic acpi=off
 - boot : linux debian-installer/probe/usb=false
 - boot : expert irqpoll (the irqpoll is necessary to avoid the IRQ conflict for the SATA disk), and on the "Detect and mount CD-ROM", I have selected only the "generic, ide-generic, ide-cd and isofs" module.

I think that these last method should be the best, but I have to choose the right parameter.

Can someone help me ?

Have I to use another debugging mode ?

Regards.

Please don't answer if your are not sure.

For your suggestion, please send me a "private message", and thereafter I will report it on this thread.

---

