---
title: "Thinkpad t60p ultrabay issue /w 2.6.24"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by bismark on 2008-03-27
I've been trying to get my Ultrabay to work on my T60p with Hardy Heron ( feisty and gutsy too actually).

I've followed the instructions on ThinkWiki to get it working but I'm having no such luck.

First off I do not have /proc/acpi/ibm/bay.  I also have these entries in my syslog[/code]
[  443.143657] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[  443.143669] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[  443.143720] ACPI: Error installing bay notify handler
[  443.143728] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added[/code]

Search for on this I found [http://www.mail-archive.com/ibm-acpi-devel@lists.sourceforge.net/msg01204.html](http://www.mail-archive.com/ibm-acpi-devel@lists.sourceforge.net/msg01204.html)

One of the suggestions in from there was to add libata.noacpi=1 to my grub boot options, however grub tells me that it doesn't understand that option.

Does anyone have any suggestions?

---

