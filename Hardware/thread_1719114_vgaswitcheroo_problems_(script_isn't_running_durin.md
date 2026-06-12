---
title: "vgaswitcheroo problems (script isn't running during boot)"
date: 2011-04-01
forum: Hardware
---

### Post by MCRappel on 2011-04-01
Hi,

I've tried to use vgeswitcheroo at startup like it described in this guide: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

After I have done all the stuff which is listed at "Script for use during bootup" I get a message, that grub can't find the file/directory "/scripts/local-top/hybrid_boot_options". In fact, there is no such file. This file is placed in the directory "/etc/initramfs-tools/scripts/local-top/".

What was my mistake?

My Hardware:

Acer Aspire TimelineX 3820TG with integrated graphics and a Radeon HD 6550M

Greetings
MCRappel

PS: I'm pretty new to Ubuntu.

---

### Post by Yellow Pasque on 2011-04-01
I'm not sure where the error is, but the obvious workaround is to put the file where grub asks for it.

---

