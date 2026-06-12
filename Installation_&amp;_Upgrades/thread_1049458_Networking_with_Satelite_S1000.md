---
title: "Networking with Satelite S1000"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Jacob_Kreed on 2009-01-24
I had problem with Ubuntu told to use Xbuntu...Spot on....But I cant seem to install the network side.  Because I want to install WINE.  Any use the net.

It a Satelite S1000, tried ifconfig, lspci and sudo lshw -C Network , which method the card was disabled...

---

### Post by lemming465 on 2009-01-25
I'm assuming you are trying to get WIFI to work, not wired ethernet?  Toshiba has used a lot of different chips, and the details matter, so if you could post some of that lspci output, that would help.  The odds are fairly high that it has a not quite supported Atheros chip.  If so, the things that are likely to work are either 8.04 variants with ndiswrapper and the XP driver, or 8.10 variants with the newer madwifi driver compiled from source.  Which version of Xubuntu are you running?

If you have access to a live Fedora 10 CD, that might be interesting, as that was the first thing to actually get WIFI right out of the box on my toshiba satellite A215-S5818 laptop (atheros AR5006EG, AR2423 chip).

---

### Post by ugm6hr on 2009-01-25
> **Jacob_Kreed said:**
> It a Satelite S1000, tried ifconfig, lspci and sudo lshw -C Network , which method the card was disabled...

Post the output from these commands.

A disabled card may be due to BIOS setting, Windows turning off network adapter due to "power-saving" or incorrect driver.

---

### Post by bapoumba on 2009-01-25
Title edited. Please try to use a title related to your own problem, that will help people help you, thanks.

---

### Post by Jacob_Kreed on 2009-01-27
> **ugm6hr said:**
> Post the output from these commands.

A disabled card may be due to BIOS setting, Windows turning off network adapter due to "power-saving" or incorrect driver.

 *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:47:c9:24:72:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

This a wired inbuilt card, not a wireless I plug a 3com into the pc card slot to check the networking, there only minimal setup screen in the bios.

---

### Post by ugm6hr on 2009-01-27
> **Jacob_Kreed said:**
> This a wired inbuilt card, not a wireless I plug a 3com into the pc card slot to check the networking, there only minimal setup screen in the bios.

I don't think it is.  pan0 is generally for Bluetooth networking:
[http://affix.sourceforge.net/affix-doc/c1051.html](http://affix.sourceforge.net/affix-doc/c1051.html)

Does ifconfig / lshw list any other network interfaces?

---

