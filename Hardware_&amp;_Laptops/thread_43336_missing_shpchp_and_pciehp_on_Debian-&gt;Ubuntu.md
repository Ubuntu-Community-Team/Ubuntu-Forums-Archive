---
title: "missing shpchp and pciehp on Debian-&gt;Ubuntu"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by James_Ward on 2005-06-21
Hi,

I hope I can get support here as I wasn't able to use the standard Ubuntu installation method.  Due to
low memory (32M), I had to install from Debian Sarge diskettes.  I then replaced my
/etc/apt/sources.list with one from my normal Ubuntu system.  (Does this qualify as an Ubuntu system
now?)

My problem is that when I insert my Netgear wireless card, I get:

Jun 21 02:34:16 localhost pci.agent[1321]:      shpchp: can't be loaded
Jun 21 02:34:16 localhost pci.agent[1321]: missing kernel or user mode driver shpchp 
Jun 21 02:34:18 localhost pci.agent[1321]:      pciehp: can't be loaded
Jun 21 02:34:18 localhost pci.agent[1321]: missing kernel or user mode driver pciehp 

I've been poking around trying to figure out what package(s) I am missing, but no luck so far...  Can
someone here point me in the right direction?

The card uses the Atheros chipset and works great in my other subnotebook.

Thanks in advance,

James

---

### Post by ranf on 2005-06-21
[QUOTE=James_Ward]
My problem is that when I insert my Netgear wireless card, I get:

Jun 21 02:34:16 localhost pci.agent[1321]:      shpchp: can't be loaded
Jun 21 02:34:16 localhost pci.agent[1321]: missing kernel or user mode driver shpchp 
Jun 21 02:34:18 localhost pci.agent[1321]:      pciehp: can't be loaded
Jun 21 02:34:18 localhost pci.agent[1321]: missing kernel or user mode driver pciehp 

I've been poking around trying to figure out what package(s) I am missing, but no luck so far...  Can
someone here point me in the right direction?

The card uses the Atheros chipset and works great in my other subnotebook.
[/QUOTE]

I don't have an Atheros. Just had a look in aptitude. 
Looks like you need "linux-restricted-modules-2.6.10-5-686" (or -386 or -k7 depending on the kernel you use).

---

