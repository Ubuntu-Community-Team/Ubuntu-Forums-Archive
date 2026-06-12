---
title: "Probs dual booting Ubuntu Desktop &amp; Server"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by mickwombat on 2009-04-28
Hi,
I am trying to get a PC to dual boot Ubuntu Desktop & Server but have run into a few problems.

Managed to install Desktop with no problems.  Used a USB stick for bootloader as my bios does not recognise the sata drive.
Tried to install Server version choosing hda1 for the boot partition & loader etc and choose to write to mbr.
I then put the following into menu.lst (on the USB)

> title Ubuntu Server
root (hd0,0)
chainloader +1

When I try to boot into server, it is giving a, Grub Error 13: Invalid or unsupported executable format.

I was expecting that I would see a second boot loader for the Server version.

Is there something else I need to add into Grub.

Thanks

---

