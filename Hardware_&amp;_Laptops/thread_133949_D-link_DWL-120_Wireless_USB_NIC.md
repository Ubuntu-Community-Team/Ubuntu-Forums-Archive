---
title: "D-link DWL-120 Wireless USB NIC"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by Mysticode on 2006-02-21
I'm running Ubuntu 5.10, and it is not auto-detecting my usb nic, but I never thought it would in the first place.

I found drivers for the device that need to be compiled, but when I was following the guide to compile everything and get it running, Ubuntu told me that "make" was an unknown command. Yes, I have tried sudo make as well.

Does anyone know where I can get some real working drivers and information about this? Im new to Ubuntu, but I have some minor RedHat 8 experience.

Thanks.

---

### Post by Mysticode on 2006-02-21
Bumping for great justice!

---

### Post by Arc Owner on 2006-02-21
You first could try to find out what chipset your adapter uses by doing an 'lspci'. Once you find what chipset it uses you might be able to find linux drivers then. If all else fails you could always use ndiswrapper, a program that uses the Windows drivers files (for your wireless card) and "wraps" them with your linux install.

---

