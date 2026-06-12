---
title: "problem with a network card"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Greenstr on 2009-08-01
Hi all. I'm not newbie in Linux (using OpenSuse since 10 version). I decided to try Ubuntu 9.04.
After an upgrade of some packages I saw a problem: Ubuntu doesn't want to see my network card. So... I cannot create any lan-connection, cannot create pppoe-connection.
System: Ubuntu 9.04
Network card: nVidia Corporation MCP67 Ethernet (rev a2)
here is a [screenshot]("http://img222.imageshack.us/img222/5157/98940583.png")

---

### Post by khelben1979 on 2009-08-01
The hard way would be to compile your own Linux kernel and in the configuration before you build it you'll see if the kernel supports it or not.

The easy way would be to find a driver package for this somewhere and just install it that way.

[Linux Kernel Database]("http://cateee.net/lkddb/") might give you something.

---

### Post by Greenstr on 2009-08-01
I don't think that it's the right way... Firstly, I'll try to reinstall network manager.
p.s.: model of my network card is supported. All drivers are installed

---

