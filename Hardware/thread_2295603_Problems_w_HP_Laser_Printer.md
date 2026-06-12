---
title: "Problems w/ HP Laser Printer"
date: 2015-09-20
forum: Hardware
---

### Post by grove0012 on 2015-09-20
I had an HP LaserjetPro 400 401n printer that worked great for several years with Ubuntu Linux, up through my current version (15.04).  It finally died, so I bought a (I believe) new IDENTICAL HP Laserjet Pro 400 401n printer to replace it.  It hooks to my router by Ethernet and all cable connections appear to be quite secure.  I already had HPLIP software installed for printer drivers.  But now the computer doesn't even see the new printer on the network, let alone print with it.  Under Settings---Printers there's only one entry, for an "HP-Fax" whatever that may be, allegedly hooked in by USB.  I can't find an option to make Ubuntu scan the network for new devices, or even manually put in a printer hooked by Ethernet.  The "Network Printer" part of the menu gives me a lot of choices of printing protocols, e.g., ipps, but I don't know what protocol is used with this printer.  Moreover, I can't actually pick out one of the protocols to (try) using.  Anybody know how I can get Ubuntu/computer/router combo to recognize this new printer and install appropriate drivers for it?

Frustrated,
Will Grove

---

### Post by tgalati4 on 2015-09-20
HP printers generally only do USB or ethernet, but not both.  So disconnect any USB cable, then reboot the computer.  Assign a static IP address to the printer through the front panel.

For example if your network is 192.168.1.XXX, then assign a high number:

IP  192.168.1.151  (many routers use 100 to 150 for handing out IP numbers using DHCP)
Netmask 255.255.255.0
Gateway 192.168.1.1 (many routers are 192.168.1.254, so check your router's documentation)

Adjust your settings so they are correct for your network.

Open a terminal on your Ubuntu machine:

```
ping -c 10 192.168.1.151
```

You should get low ping times (1-3 milliseconds) and no packet drops.  No connection means no printing.

```
hp-toolbox
```

Set up your printer.  It should automatically be detected during a network scan and the rest is plug-and-play.

---

