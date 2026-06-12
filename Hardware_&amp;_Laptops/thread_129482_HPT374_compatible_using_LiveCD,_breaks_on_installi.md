---
title: "HPT374 compatible using LiveCD, breaks on installing Ubuntu"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by themole22 on 2006-02-13
I'm currently trying to install Ubuntu onto my fileserver. 4 of my drives are on a Highpoint R1540 card (based on the HPT374 chipset) which a few people are having problems getting running.

What I've noticed is that it only causes problems once Ubuntu is installed. It works correctly on the liveDVD version, allowing browsing of the HDDs attached to the controller.

Could anyone help either:
a) install Ubuntu without having the card hang my PC on bootup (unlikely, I think - there are a few posts on the web about driver issues).

b) somehow install the LiveDVD version of Ubuntu on my HDD so I can modify it to add EVMS (the only functionality I actually need!)

c) help me to install EVMS-GUI (or even EVMS-CLI) onto a liveDVD-booted copy of Ubuntu - apt-get and synaptic both hang because they thing archive.ubuntu.com is on 1.0.0.0.

Notes: the drives on the controller are SATA, they are not bootable and they work fine under WinXP and are browseable under Ubuntu LiveDVD. On startup after installing Ubuntu, the PC hangs at the point before initialising /dev at the end of Loading Modules. This error is presumably: [http://bugme.osdl.org/show_bug.cgi?id=2555](http://bugme.osdl.org/show_bug.cgi?id=2555)

---

