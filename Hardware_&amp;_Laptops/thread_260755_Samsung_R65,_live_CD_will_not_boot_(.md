---
title: "Samsung R65, live CD will not boot :("
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by Xirtambus on 2006-09-19
I'm totally at my wit's end, could use some help.

For the past 2 days I've been trying to install ubuntu on my new laptop ready for university, but evey time I boot the system, it freezes totally at 'loading ACPI modules' booting with the acpi=off cheatcode stops the laptop from booting at all :(

Horrible (open)SUSE 10.1 works fine, but it's so fat and slow i had to remove it. In desparation I tried installing ubuntu from my old hoary CD so I could get into the system then run a dist-upgrade, but the same old ACPI issue is there. :( :(

Any ideas?

---

### Post by bas_sefcom-computers on 2008-01-23
Hi,

Little bit late but he there must be more people with problems..

Can you try as boot option, type all as below in one line : (Ubuntu 7.04/7.10)

acpi=off noapic pci=bios 

That worked for me! Have fun with Ubuntu!

Bas
Sefcom Computers
100% Linux Support!

---

