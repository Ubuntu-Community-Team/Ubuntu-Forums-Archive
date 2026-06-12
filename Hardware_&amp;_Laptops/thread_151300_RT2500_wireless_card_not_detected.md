---
title: "RT2500 wireless card not detected"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by ?@yk0&amp;^4 on 2006-03-27
I have tried to install Breezy on a Dell Optiplex GX110 computer with a new Edimax EW-7128g PCI card (which has an RT2500 chipset), but the card was not detected properly.

If I run **lspci** I get the following in the list:
```
0000:01:0a.0 Network controller: RaLink: Unknown device 0301
```

However, the module for the card is not loaded (if I use **lsmod**) and the card does not appear in *System > Administration > Networking*

Does anyone have any ideas about what I should do to get Breezy to recognise the card?

Many thanks,
Greg.

---

### Post by ?@yk0&amp;^4 on 2006-04-03
Please... does anyone have any ideas why Breezy might not be recognising this particular card? All the reports on the net regarding the use of cards with this chipset are positive but mine just seems not to want to! Is there anything I should check?

This is my first try at wireless with Linux (except some very unsuccessful attempts with an ACX111 chipset card), and my research led me to believe that these cards are generally very reliable on Linux, does anyone have any idea why this card might not be working?

Many thanks in advance,
Greg.

---

### Post by Zeroedout on 2006-04-03
First think i'de do is run ```
sudo lshw
``` and make sure your card has an rt2500 chipset. If you're 100% sure your card has an rt2500 chipset and ra0 is not showing up, you might need to compile the latest version of the drivers. [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo) should give you a good guide. If all else fails, try ndiswrapper with the windows driver, probebly a shitty solution but it's better than nothing. I bought an Encore card with the model that was supposed to have the rt2500 chipset, but to my surprise, the revision I purchased was using some weird obscure chipset (those asshats!). Good luck.

---

### Post by ?@yk0&amp;^4 on 2006-04-04
When I run **lshw** I get this somewhere along the list:

```
*-network:0 UNCLAIMED
description: Network controller
product: RaLink
vendor: RaLink
physical id: a
bus info: pci@01:0a.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: iomemory:fdff8000-fdffffff irq:11
```

This presumably means that the chipset is an RT2500?

This card shares an IRQ with a USB controller... is this a problem (see below)

```
*-usb
description: USB Controller
product: 82801AA USB
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@00:1f.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd
resources: ioport:ff80-ff9f irq:11
```

Many thanks for your help,
Greg.

---

### Post by Zillion on 2006-04-04
I used this to get my RT2500 working

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

---

### Post by ?@yk0&amp;^4 on 2006-04-04
Just realised I posted the wrong section of the **lspci** readout... I posted the section for my (wired) NIC instead of the wireless card. I've edited the original post, and the correct readout from **lspci** is as follows:

```
0000:01:0a.0 Network controller: RaLink: Unknown device 0301
```

Many thanks,
Greg.

---

### Post by jhunholz on 2006-04-04
modprobe rt2500
iwconfig ra0 (or whatever device it names it) enc (insert encryption key here)
iwconfig ra0 essid (essid here)
dhclient ra0

That should do it.

If you don't have the rt2500 driver installed, its in Synaptic (just search for rt2500).

---

### Post by pshnfry on 2006-04-27
How does that assist when there is no logical name given at lshw as shown above?

I have the same problem with a RT2500 chip pci wireless nic.

Cheers,

Peter.

---

### Post by mithion on 2006-05-07
I have the same problem.  Breezy isn't detecting the network card correctly and I don't know why.  I've done a bit of research and here's what I found.  It seems linksys came up with a new revision for their network adapter.  They are now at revision 4.1.  Now I read somewhere that for this new revision, there has been a slight change in the chipset.  And these new cards would fall under the RT61 chipset.  Now I have no clue if this is correct, but it would explain why Breezy isn't detecting it correctly.  I tried compiling the linux drivers for RT61, but I'm new in linux and I haven't been able to make it work using this tutorial. [http://www.ubuntuforums.org/showthread.php?t=132980&highlight=RT61]("http://www.ubuntuforums.org/showthread.php?t=132980&highlight=RT61").  I also tried the windows drivers in conjunction with ndiswrapper, but that as well hasn't worked out for me.  That's all I've found so far, but nothing succesful.  Sorry.

---

