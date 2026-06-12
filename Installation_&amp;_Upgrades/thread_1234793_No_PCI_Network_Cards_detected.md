---
title: "No PCI Network Cards detected"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by galileon on 2009-08-08
Hello,

I've just tried to install Ubuntu 9.04 on my brother's computer, and I can't get a PCI Network Card to work. I've tried both a RTL8139B and a Netgear WG311v3 and neither worked.

I've tried lspci and lshw with both, and I include the results for the RTL card. Neither appears under lspci or lshw. dmesg also didn't look very helpful. Included here is dmesg for the RTL. (I've trimmed out stuff about hard disk drives to make the file small enough to upload, there's a limit here).

I've played around with irqpoll, acpi=off, noacpi, nolapic, etc and none seems to have worked. menu.lst included.

Any ideas on how to proceed? Thanks for any input!

---

