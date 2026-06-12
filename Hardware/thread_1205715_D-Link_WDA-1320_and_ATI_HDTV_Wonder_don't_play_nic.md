---
title: "D-Link WDA-1320 and ATI HDTV Wonder don't play nice together"
date: 2009-07-06
forum: Hardware
---

### Post by molder on 2009-07-06
recently upgraded my Mythbuntu box from an old linksys 11b card to a D-Link WDA-1320 card.  I also have an ATI HDTV Wonder card installed to serve as my tuner card.  I can not boot with both cards installed.  I have tried the following kernel boot options with no success: irqpoll, noacpi, pci=noacpi, acpi_irq_balance, noapic, nolapic.  I am at a loss why I can succefully boot with either card install but just not both.

PC Stats:
Jaunty Mythbuntu 9.04
Pentium 4 2.80 GHz
Biostar P4M900-M4 motherboard
2 gb ram

I have attached the output of lspci uname syslog and dmesg with each card separately installed.

---

### Post by molder on 2009-07-06
So I uninstalled Network Manager and the box booted but I have not connectivity :( .

---

