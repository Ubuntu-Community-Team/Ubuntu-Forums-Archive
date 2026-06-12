---
title: "Pcmcia"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by Bertmartin on 2004-12-21
I have a very old Compaq Presario 1080 that I am trying to use as a simple web terminal.  Ubuntu installed fine and works (very slow but it works).  The only problem I have is that I can't get it to load PCMCIA support.  I have tried using a linksys and netgear wireless card.  

pcic_probe returns " PCI bridge probe: Cirrus Logic CL 6729 found, 2 sockets

lsmod shows  "pcmcia core    63156  4  i82092,ds,yenta_socket, pd6729"

cardmgr returns "no sockets found"

I tried manually starting the pcmcia service ("/etc/init.d/pcmcia start") and it comes back as failed.

This computer does not have a usb port so this my only avenue for getting network availability.

Any help or thoughts of things to try would be great.

---

