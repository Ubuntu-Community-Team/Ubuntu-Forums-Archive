---
title: "Do you have wireless that &quot;just worked&quot; ?"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by joepotter on 2005-04-09
Hello all,

I am interested in what wireless nic cards are out there that work out of the box with native drivers. I want to find a pci card for desktops; but I need to know about laptop solutions also.

Who had one that just worked?

Thanks.

---

### Post by godsdog on 2005-04-09
I'm using a rebranded (Cabletron) Orinoco Gold card that worked on install with Warty and Hoary both on my IBM A30 Think Pad. Bought it from an ebay seller that included a CD with a Linux driver (which I haven't needed yet) and a number of Linux and windows programs.

---

### Post by kennethong on 2005-04-09
[QUOTE=joepotter]Hello all,

I am interested in what wireless nic cards are out there that work out of the box with native drivers. I want to find a pci card for desktops; but I need to know about laptop solutions also.

Who had one that just worked?

Thanks.[/QUOTE]


 My Sony Vaio T-17GP/S with an integrated Intel 2200BG chipset works out of the box.  :-D

---

### Post by weblars on 2005-04-09
My Netgear MA311 PCI card (Prism chipset) works fine.

---

### Post by ploum on 2005-04-09
3Com Corporation 3CRWE154G72 - rev1 ( 0280:10b7:6001)

Prism54 Chipset.

Works perfectly out of the box on Warty and even during the installation for Hoary. Really really good

---

### Post by mrbass on 2005-04-09
I kept trying ubuntu and never could get my netgear WG311 pci card working until 5.04 so now I'm stoked.

---

### Post by Ryujin on 2005-04-09
I have a lynksys WPC11 PCMCIA (oronico) old yes, but it works like a charm!

---

### Post by bobmitch on 2005-04-10
I have a netgear wg311 v2 pci card.  (Texas Instruments chipset)

The support is experimental - but flawless in hoary for me so far.

---

### Post by joepotter on 2005-04-15
thanks all,

We need a list of cards that work, and one of cards that work with native drivers. I hate it when the chip changes but they do not have the decency to change the model number. that one has caught me more than once.

---

### Post by lao_V on 2005-04-15
[QUOTE=bobmitch]I have a netgear wg311 v2 pci card.  (Texas Instruments chipset)

The support is experimental - but flawless in hoary for me so far.[/QUOTE]

Does this work with or without WEP?
I have a card with TI chipset which keeps crashing the machine when used with WEP (ndiswrapper/driverloader)

---

### Post by bobmitch on 2005-04-15
[QUOTE=lao_V]Does this work with or without WEP?
I have a card with TI chipset which keeps crashing the machine when used with WEP (ndiswrapper/driverloader)[/QUOTE]

Running without WEP at the moment, and have no plans to turn it on anytime soon. :)

---

### Post by speedman on 2005-04-15
chris@i8500:~ $ cardctl ident
Socket 0:
  product info: "D", "Link DWL-650 11Mbps WLAN Card", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

This card works like a champ out of the box on Hoary on 3 laptops in my office.


Regards,

SM

---

### Post by tread on 2005-04-17
My Toshiba Satellite M35x S149 came with:

Built-in Wi-Fi-compliant Atheros wireless LAN(802.11b/g)
10/100Base-TX Ethernet (RJ-45 connector)

I had to compile a driver for it on Mandrake, but Ubuntu "just worked". Even with encryption, which I had occasion to test during a visit to my brothers.

---

